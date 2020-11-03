---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/add-type?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-Type
ms.openlocfilehash: cfd6cac9c1dda0a86b5b2762be936dc5d77bf34e
ms.sourcegitcommit: e0f9fe6335be1e0f94bedaa0e8baec2acaeaa076
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2020
ms.locfileid: "93206233"
---
# <span data-ttu-id="a108e-103">Add-Type</span><span class="sxs-lookup"><span data-stu-id="a108e-103">Add-Type</span></span>

## <span data-ttu-id="a108e-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="a108e-104">SYNOPSIS</span></span>
<span data-ttu-id="a108e-105">Ajoute une classe Microsoft .NET Core à une session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a108e-105">Adds a Microsoft .NET Core class to a PowerShell session.</span></span>

## <span data-ttu-id="a108e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a108e-106">SYNTAX</span></span>

### <span data-ttu-id="a108e-107">FromSource (par défaut)</span><span class="sxs-lookup"><span data-stu-id="a108e-107">FromSource (Default)</span></span>

```
Add-Type [-TypeDefinition] <String> [-Language <Language>] [-ReferencedAssemblies <String[]>]
 [-OutputAssembly <String>] [-OutputType <OutputAssemblyType>] [-PassThru] [-IgnoreWarnings]
 [-CompilerOptions <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="a108e-108">FromMember</span><span class="sxs-lookup"><span data-stu-id="a108e-108">FromMember</span></span>

```
Add-Type [-Name] <String> [-MemberDefinition] <String[]> [-Namespace <String>]
 [-UsingNamespace <String[]>] [-Language <Language>] [-ReferencedAssemblies <String[]>]
 [-OutputAssembly <String>] [-OutputType <OutputAssemblyType>] [-PassThru] [-IgnoreWarnings]
 [-CompilerOptions <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="a108e-109">FromPath</span><span class="sxs-lookup"><span data-stu-id="a108e-109">FromPath</span></span>

```
Add-Type [-Path] <String[]> [-ReferencedAssemblies <String[]>] [-OutputAssembly <String>]
 [-OutputType <OutputAssemblyType>] [-PassThru] [-IgnoreWarnings] [-CompilerOptions <String[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="a108e-110">FromLiteralPath</span><span class="sxs-lookup"><span data-stu-id="a108e-110">FromLiteralPath</span></span>

```
Add-Type -LiteralPath <String[]> [-ReferencedAssemblies <String[]>] [-OutputAssembly <String>]
 [-OutputType <OutputAssemblyType>] [-PassThru] [-IgnoreWarnings] [-CompilerOptions <String[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="a108e-111">FromAssemblyName</span><span class="sxs-lookup"><span data-stu-id="a108e-111">FromAssemblyName</span></span>

```
Add-Type -AssemblyName <String[]> [-PassThru] [<CommonParameters>]
```

## <span data-ttu-id="a108e-112">Description</span><span class="sxs-lookup"><span data-stu-id="a108e-112">DESCRIPTION</span></span>

<span data-ttu-id="a108e-113">L' `Add-Type` applet de commande vous permet de définir une classe de base Microsoft .net dans votre session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a108e-113">The `Add-Type` cmdlet lets you define a Microsoft .NET Core class in your PowerShell session.</span></span> <span data-ttu-id="a108e-114">Vous pouvez ensuite instancier des objets, à l’aide de l’applet de commande `New-Object` , et utiliser les objets comme vous le feriez pour n’importe quel objet .net core.</span><span class="sxs-lookup"><span data-stu-id="a108e-114">You can then instantiate objects, by using the `New-Object` cmdlet, and use the objects just as you would use any .NET Core object.</span></span> <span data-ttu-id="a108e-115">Si vous ajoutez une `Add-Type` commande à votre profil PowerShell, la classe est disponible dans toutes les sessions PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a108e-115">If you add an `Add-Type` command to your PowerShell profile, the class is available in all PowerShell sessions.</span></span>

<span data-ttu-id="a108e-116">Vous pouvez spécifier le type en désignant un assembly existant ou des fichiers de code source. Par ailleurs, vous pouvez spécifier le code source inline ou enregistré dans une variable.</span><span class="sxs-lookup"><span data-stu-id="a108e-116">You can specify the type by specifying an existing assembly or source code files, or you can specify the source code inline or saved in a variable.</span></span> <span data-ttu-id="a108e-117">Vous pouvez même spécifier uniquement une méthode et `Add-Type` définit et génère la classe.</span><span class="sxs-lookup"><span data-stu-id="a108e-117">You can even specify only a method and `Add-Type` defines and generates the class.</span></span> <span data-ttu-id="a108e-118">Sur Windows, vous pouvez utiliser cette fonctionnalité pour effectuer des appels d’appel de code non managé (P/Invoke) à des fonctions non managées dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a108e-118">On Windows, you can use this feature to make Platform Invoke (P/Invoke) calls to unmanaged functions in PowerShell.</span></span> <span data-ttu-id="a108e-119">Si vous spécifiez le code source, `Add-Type` compile le code source spécifié et génère un assembly en mémoire qui contient les nouveaux types .net core.</span><span class="sxs-lookup"><span data-stu-id="a108e-119">If you specify source code, `Add-Type` compiles the specified source code and generates an in-memory assembly that contains the new .NET Core types.</span></span>

<span data-ttu-id="a108e-120">Vous pouvez utiliser les paramètres de `Add-Type` pour spécifier un autre langage et un autre compilateur, C# est l’option par défaut, les options du compilateur, les dépendances de l’assembly, l’espace de noms de la classe, les noms du type et l’assembly résultant.</span><span class="sxs-lookup"><span data-stu-id="a108e-120">You can use the parameters of `Add-Type` to specify an alternate language and compiler, C# is the default, compiler options, assembly dependencies, the class namespace, the names of the type, and the resulting assembly.</span></span>

<span data-ttu-id="a108e-121">À compter de PowerShell 7, `Add-Type` ne compile pas un type si un type portant le même nom existe déjà.</span><span class="sxs-lookup"><span data-stu-id="a108e-121">Beginning in PowerShell 7, `Add-Type` does not compile a type if a type with the same name already exists.</span></span> <span data-ttu-id="a108e-122">Recherche également les `Add-Type` assemblys dans un `ref` dossier sous le dossier qui contient `pwsh.dll` .</span><span class="sxs-lookup"><span data-stu-id="a108e-122">Also, `Add-Type` looks for assemblies in a `ref` folder under the folder that contains `pwsh.dll`.</span></span>

## <span data-ttu-id="a108e-123">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="a108e-123">EXAMPLES</span></span>

### <span data-ttu-id="a108e-124">Exemple 1 : ajouter un type .NET à une session</span><span class="sxs-lookup"><span data-stu-id="a108e-124">Example 1: Add a .NET type to a session</span></span>

<span data-ttu-id="a108e-125">Cet exemple ajoute la classe **BasicTest** à la session en spécifiant le code source stocké dans une variable.</span><span class="sxs-lookup"><span data-stu-id="a108e-125">This example adds the **BasicTest** class to the session by specifying source code that is stored in a variable.</span></span> <span data-ttu-id="a108e-126">La classe **BasicTest** est utilisée pour ajouter des entiers, créer un objet et multiplier des entiers.</span><span class="sxs-lookup"><span data-stu-id="a108e-126">The **BasicTest** class is used to add integers, create an object, and multiply integers.</span></span>

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

<span data-ttu-id="a108e-127">La `$Source` variable stocke le code source de la classe.</span><span class="sxs-lookup"><span data-stu-id="a108e-127">The `$Source` variable stores the source code for the class.</span></span> <span data-ttu-id="a108e-128">Le type a une méthode statique appelée `Add` et une méthode non statique appelée `Multiply` .</span><span class="sxs-lookup"><span data-stu-id="a108e-128">The type has a static method called `Add` and a non-static method called `Multiply`.</span></span>

<span data-ttu-id="a108e-129">L' `Add-Type` applet de commande ajoute la classe à la session.</span><span class="sxs-lookup"><span data-stu-id="a108e-129">The `Add-Type` cmdlet adds the class to the session.</span></span> <span data-ttu-id="a108e-130">Comme il utilise le code source en ligne, la commande utilise le paramètre **TypeDefinition** pour spécifier le code dans la `$Source` variable.</span><span class="sxs-lookup"><span data-stu-id="a108e-130">Because it's using inline source code, the command uses the **TypeDefinition** parameter to specify the code in the `$Source` variable.</span></span>

<span data-ttu-id="a108e-131">La `Add` méthode statique de la classe **BasicTest** utilise les caractères double deux-points ( `::` ) pour spécifier un membre statique de la classe.</span><span class="sxs-lookup"><span data-stu-id="a108e-131">The `Add` static method of the **BasicTest** class uses the double-colon characters (`::`) to specify a static member of the class.</span></span> <span data-ttu-id="a108e-132">Les entiers sont ajoutés et la somme est affichée.</span><span class="sxs-lookup"><span data-stu-id="a108e-132">The integers are added and the sum is displayed.</span></span>

<span data-ttu-id="a108e-133">L' `New-Object` applet de commande instancie une instance de la classe **BasicTest** .</span><span class="sxs-lookup"><span data-stu-id="a108e-133">The `New-Object` cmdlet instantiates an instance of the **BasicTest** class.</span></span> <span data-ttu-id="a108e-134">Elle enregistre le nouvel objet dans la `$BasicTestObject` variable.</span><span class="sxs-lookup"><span data-stu-id="a108e-134">It saves the new object in the `$BasicTestObject` variable.</span></span>

<span data-ttu-id="a108e-135">`$BasicTestObject` utilise la `Multiply` méthode.</span><span class="sxs-lookup"><span data-stu-id="a108e-135">`$BasicTestObject` uses the `Multiply` method.</span></span> <span data-ttu-id="a108e-136">Les entiers sont multipliés et le produit est affiché.</span><span class="sxs-lookup"><span data-stu-id="a108e-136">The integers are multiplied and the product is displayed.</span></span>

### <span data-ttu-id="a108e-137">Exemple 2 : examiner un type ajouté</span><span class="sxs-lookup"><span data-stu-id="a108e-137">Example 2: Examine an added type</span></span>

<span data-ttu-id="a108e-138">Cet exemple utilise l' `Get-Member` applet de commande pour examiner les objets `Add-Type` créés par les `New-Object` applets de commande et dans l' **exemple 1** .</span><span class="sxs-lookup"><span data-stu-id="a108e-138">This example uses the `Get-Member` cmdlet to examine the objects that the `Add-Type` and `New-Object` cmdlets created in **Example 1** .</span></span>

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

<span data-ttu-id="a108e-139">L' `Get-Member` applet de commande obtient le type et les membres de la classe **BasicTest** qui ont `Add-Type` été ajoutés à la session.</span><span class="sxs-lookup"><span data-stu-id="a108e-139">The `Get-Member` cmdlet gets the type and members of the **BasicTest** class that `Add-Type` added to the session.</span></span> <span data-ttu-id="a108e-140">La `Get-Member` commande révèle qu’il s’agit d’un objet **System. RuntimeType** , dérivé de la classe **System. Object** .</span><span class="sxs-lookup"><span data-stu-id="a108e-140">The `Get-Member` command reveals that it's a **System.RuntimeType** object, which is derived from the **System.Object** class.</span></span>

<span data-ttu-id="a108e-141">Le `Get-Member` paramètre **static** obtient les propriétés et les méthodes statiques de la classe **BasicTest** .</span><span class="sxs-lookup"><span data-stu-id="a108e-141">The `Get-Member` **Static** parameter gets the static properties and methods of the **BasicTest** class.</span></span> <span data-ttu-id="a108e-142">La sortie indique que la `Add` méthode est incluse.</span><span class="sxs-lookup"><span data-stu-id="a108e-142">The output shows that the `Add` method is included.</span></span>

<span data-ttu-id="a108e-143">L' `Get-Member` applet de commande obtient les membres de l’objet stocké dans la `$BasicTestObject` variable.</span><span class="sxs-lookup"><span data-stu-id="a108e-143">The `Get-Member` cmdlet gets the members of the object stored in the `$BasicTestObject` variable.</span></span>
<span data-ttu-id="a108e-144">`$BasicTestObject` a été créé à l’aide de l' `New-Object` applet de commande avec la classe **BasicTest** .</span><span class="sxs-lookup"><span data-stu-id="a108e-144">`$BasicTestObject` was created by using the `New-Object` cmdlet with the **BasicTest** class.</span></span> <span data-ttu-id="a108e-145">La sortie révèle que la valeur de la `$BasicTestObject` variable est une instance de la classe **BasicTest** et qu’elle comprend un membre appelé `Multiply` .</span><span class="sxs-lookup"><span data-stu-id="a108e-145">The output reveals that the value of the `$BasicTestObject` variable is an instance of the **BasicTest** class and that it includes a member called `Multiply`.</span></span>

### <span data-ttu-id="a108e-146">Exemple 3 : ajouter des types à partir d’un assembly</span><span class="sxs-lookup"><span data-stu-id="a108e-146">Example 3: Add types from an assembly</span></span>

<span data-ttu-id="a108e-147">Cet exemple ajoute les classes de l' `NJsonSchema.dll` assembly à la session active.</span><span class="sxs-lookup"><span data-stu-id="a108e-147">This example adds the classes from the `NJsonSchema.dll` assembly to the current session.</span></span>

```powershell
Set-Location -Path $PSHOME
$AccType = Add-Type -AssemblyName *jsonschema* -PassThru
```

<span data-ttu-id="a108e-148">`Set-Location` utilise le paramètre **path** pour spécifier la `$PSHOME` variable.</span><span class="sxs-lookup"><span data-stu-id="a108e-148">`Set-Location` uses the **Path** parameter to specify the `$PSHOME` variable.</span></span> <span data-ttu-id="a108e-149">La variable référence le répertoire d’installation de PowerShell dans lequel se trouve le fichier DLL.</span><span class="sxs-lookup"><span data-stu-id="a108e-149">The variable references the PowerShell installation directory where the DLL file is located.</span></span>

<span data-ttu-id="a108e-150">La `$AccType` variable stocke un objet créé avec l’applet de commande `Add-Type` .</span><span class="sxs-lookup"><span data-stu-id="a108e-150">The `$AccType` variable stores an object created with the `Add-Type` cmdlet.</span></span> <span data-ttu-id="a108e-151">`Add-Type` utilise le paramètre **AssemblyName** pour spécifier le nom de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="a108e-151">`Add-Type` uses the **AssemblyName** parameter to specify the name of the assembly.</span></span> <span data-ttu-id="a108e-152">Le `*` caractère générique astérisque () vous permet d’accéder à l’assembly approprié même si vous n’êtes pas sûr de son nom ou de son orthographe.</span><span class="sxs-lookup"><span data-stu-id="a108e-152">The asterisk (`*`) wildcard character allows you to get the correct assembly even when you aren't sure of the name or its spelling.</span></span> <span data-ttu-id="a108e-153">Le paramètre **PassThru** génère des objets qui représentent les classes ajoutées à la session.</span><span class="sxs-lookup"><span data-stu-id="a108e-153">The **PassThru** parameter generates objects that represent the classes that are added to the session.</span></span>

### <span data-ttu-id="a108e-154">Exemple 4 : appeler des API Windows natives</span><span class="sxs-lookup"><span data-stu-id="a108e-154">Example 4: Call native Windows APIs</span></span>

<span data-ttu-id="a108e-155">Cet exemple montre comment appeler des API Windows natives dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a108e-155">This example demonstrates how to call native Windows APIs in PowerShell.</span></span> <span data-ttu-id="a108e-156">`Add-Type` utilise le mécanisme d’appel de code non managé (P/Invoke) pour appeler une fonction dans `User32.dll` à partir de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a108e-156">`Add-Type` uses the Platform Invoke (P/Invoke) mechanism to call a function in `User32.dll` from PowerShell.</span></span> <span data-ttu-id="a108e-157">Cet exemple fonctionne uniquement sur les ordinateurs exécutant le système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="a108e-157">This example only works on computers running the Windows operating system.</span></span>

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

<span data-ttu-id="a108e-158">La `$Signature` variable stocke la signature C# de la `ShowWindowAsync` fonction.</span><span class="sxs-lookup"><span data-stu-id="a108e-158">The `$Signature` variable stores the C# signature of the `ShowWindowAsync` function.</span></span> <span data-ttu-id="a108e-159">Pour vous assurer que la méthode résultante est visible dans une session PowerShell, le `public` mot clé a été ajouté à la signature standard.</span><span class="sxs-lookup"><span data-stu-id="a108e-159">To ensure that the resulting method is visible in a PowerShell session, the `public` keyword was added to the standard signature.</span></span> <span data-ttu-id="a108e-160">Pour plus d’informations, consultez [fonction ShowWindowAsync](/windows/win32/api/winuser/nf-winuser-showwindowasync).</span><span class="sxs-lookup"><span data-stu-id="a108e-160">For more information, see [ShowWindowAsync function](/windows/win32/api/winuser/nf-winuser-showwindowasync).</span></span>

<span data-ttu-id="a108e-161">La `$ShowWindowAsync` variable stocke l’objet créé par le `Add-Type` paramètre **PassThru** .</span><span class="sxs-lookup"><span data-stu-id="a108e-161">The `$ShowWindowAsync` variable stores the object created by the `Add-Type` **PassThru** parameter.</span></span>
<span data-ttu-id="a108e-162">L' `Add-Type` applet de commande ajoute la `ShowWindowAsync` fonction à la session PowerShell en tant que méthode statique.</span><span class="sxs-lookup"><span data-stu-id="a108e-162">The `Add-Type` cmdlet adds the `ShowWindowAsync` function to the PowerShell session as a static method.</span></span> <span data-ttu-id="a108e-163">La commande utilise le paramètre **MemberDefinition** pour spécifier la définition de méthode enregistrée dans la `$Signature` variable.</span><span class="sxs-lookup"><span data-stu-id="a108e-163">The command uses the **MemberDefinition** parameter to specify the method definition saved in the `$Signature` variable.</span></span> <span data-ttu-id="a108e-164">La commande utilise les paramètres **Name** et **Namespace** pour spécifier le nom et l'espace de noms de la classe.</span><span class="sxs-lookup"><span data-stu-id="a108e-164">The command uses the **Name** and **Namespace** parameters to specify a name and namespace for the class.</span></span> <span data-ttu-id="a108e-165">Le paramètre **PassThru** génère un objet qui représente les types.</span><span class="sxs-lookup"><span data-stu-id="a108e-165">The **PassThru** parameter generates an object that represents the types.</span></span>

<span data-ttu-id="a108e-166">La nouvelle `ShowWindowAsync` méthode statique est utilisée dans les commandes pour réduire et restaurer la console PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a108e-166">The new `ShowWindowAsync` static method is used in the commands to minimize and restore the PowerShell console.</span></span> <span data-ttu-id="a108e-167">La méthode accepte deux paramètres : le handle de fenêtre et un entier qui spécifie le mode d’affichage de la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="a108e-167">The method takes two parameters: the window handle, and an integer that specifies how the window is displayed.</span></span>

<span data-ttu-id="a108e-168">Pour réduire la console PowerShell, `ShowWindowAsync` utilise l' `Get-Process` applet de commande avec la `$PID` variable automatique pour recevoir le processus qui héberge la session PowerShell active.</span><span class="sxs-lookup"><span data-stu-id="a108e-168">To minimize the PowerShell console, `ShowWindowAsync` uses the `Get-Process` cmdlet with the `$PID` automatic variable to get the process that is hosting the current PowerShell session.</span></span> <span data-ttu-id="a108e-169">Elle utilise ensuite la propriété **MainWindowHandle** du processus actuel et la valeur `2` , qui représente la `SW_MINIMIZE` valeur.</span><span class="sxs-lookup"><span data-stu-id="a108e-169">Then it uses the **MainWindowHandle** property of the current process and a value of `2`, which represents the `SW_MINIMIZE` value.</span></span>

<span data-ttu-id="a108e-170">Pour restaurer la fenêtre, `ShowWindowAsync` utilise la valeur `4` pour la position de la fenêtre, qui représente la `SW_RESTORE` valeur.</span><span class="sxs-lookup"><span data-stu-id="a108e-170">To restore the window, `ShowWindowAsync` uses a value of `4` for the window position, which represents the `SW_RESTORE` value.</span></span>

<span data-ttu-id="a108e-171">Pour agrandir la fenêtre, utilisez la valeur de `3` qui est représentée par `SW_MAXIMIZE` .</span><span class="sxs-lookup"><span data-stu-id="a108e-171">To maximize the window, use the value of `3` that represents `SW_MAXIMIZE`.</span></span>

## <span data-ttu-id="a108e-172">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a108e-172">PARAMETERS</span></span>

### <span data-ttu-id="a108e-173">-AssemblyName</span><span class="sxs-lookup"><span data-stu-id="a108e-173">-AssemblyName</span></span>

<span data-ttu-id="a108e-174">Spécifie le nom d'un assembly qui inclut les types.</span><span class="sxs-lookup"><span data-stu-id="a108e-174">Specifies the name of an assembly that includes the types.</span></span> <span data-ttu-id="a108e-175">`Add-Type` prend les types de l’assembly spécifié.</span><span class="sxs-lookup"><span data-stu-id="a108e-175">`Add-Type` takes the types from the specified assembly.</span></span> <span data-ttu-id="a108e-176">Ce paramètre est obligatoire lorsque vous créez des types basés sur un nom d’assembly.</span><span class="sxs-lookup"><span data-stu-id="a108e-176">This parameter is required when you're creating types based on an assembly name.</span></span>

<span data-ttu-id="a108e-177">Entrez le nom complet ou simple, également appelé « nom partiel », d’un assembly.</span><span class="sxs-lookup"><span data-stu-id="a108e-177">Enter the full or simple name, also known as the partial name, of an assembly.</span></span> <span data-ttu-id="a108e-178">Les caractères génériques sont autorisés dans le nom de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="a108e-178">Wildcard characters are permitted in the assembly name.</span></span> <span data-ttu-id="a108e-179">Si vous entrez un nom simple ou partiel, `Add-Type` le résout en nom complet, puis utilise le nom complet pour charger l’assembly.</span><span class="sxs-lookup"><span data-stu-id="a108e-179">If you enter a simple or partial name, `Add-Type` resolves it to the full name, and then uses the full name to load the assembly.</span></span>

<span data-ttu-id="a108e-180">Ce paramètre n’accepte pas de chemin d’accès ou de nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="a108e-180">This parameter doesn't accept a path or a filename.</span></span> <span data-ttu-id="a108e-181">Pour entrer le chemin d’accès au fichier de bibliothèque de liens dynamiques (DLL) de l’assembly, utilisez le paramètre **path** .</span><span class="sxs-lookup"><span data-stu-id="a108e-181">To enter the path to the assembly dynamic-link library (DLL) file, use the **Path** parameter.</span></span>

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

### <span data-ttu-id="a108e-182">-CompilerOptions</span><span class="sxs-lookup"><span data-stu-id="a108e-182">-CompilerOptions</span></span>

<span data-ttu-id="a108e-183">Spécifie les options du compilateur de code source.</span><span class="sxs-lookup"><span data-stu-id="a108e-183">Specifies the options for the source code compiler.</span></span> <span data-ttu-id="a108e-184">Ces options sont envoyées au compilateur sans révision.</span><span class="sxs-lookup"><span data-stu-id="a108e-184">These options are sent to the compiler without revision.</span></span>

<span data-ttu-id="a108e-185">Ce paramètre vous permet de demander au compilateur de générer un fichier exécutable, d’incorporer des ressources ou de définir des options de ligne de commande, telles que l' `/unsafe` option.</span><span class="sxs-lookup"><span data-stu-id="a108e-185">This parameter allows you to direct the compiler to generate an executable file, embed resources, or set command-line options, such as the `/unsafe` option.</span></span>

<span data-ttu-id="a108e-186">Vous ne pouvez pas utiliser les paramètres **CompilerOptions** et **ReferencedAssemblies** dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="a108e-186">You can't use the **CompilerOptions** and **ReferencedAssemblies** parameters in the same command.</span></span>

```yaml
Type: System.String[]
Parameter Sets: FromSource, FromMember, FromPath, FromLiteralPath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a108e-187">-IgnoreWarnings</span><span class="sxs-lookup"><span data-stu-id="a108e-187">-IgnoreWarnings</span></span>

<span data-ttu-id="a108e-188">Ignore les avertissements du compilateur.</span><span class="sxs-lookup"><span data-stu-id="a108e-188">Ignores compiler warnings.</span></span> <span data-ttu-id="a108e-189">Utilisez ce paramètre pour empêcher `Add-Type` de gérer les avertissements du compilateur comme des erreurs.</span><span class="sxs-lookup"><span data-stu-id="a108e-189">Use this parameter to prevent `Add-Type` from handling compiler warnings as errors.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: FromSource, FromMember, FromPath, FromLiteralPath
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a108e-190">-Langage</span><span class="sxs-lookup"><span data-stu-id="a108e-190">-Language</span></span>

<span data-ttu-id="a108e-191">Spécifie la langue utilisée dans le code source.</span><span class="sxs-lookup"><span data-stu-id="a108e-191">Specifies the language that is used in the source code.</span></span> <span data-ttu-id="a108e-192">La valeur acceptable pour ce paramètre est **CSharp** .</span><span class="sxs-lookup"><span data-stu-id="a108e-192">The acceptable value for this parameter is **CSharp** .</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.Language
Parameter Sets: FromSource, FromMember
Aliases:
Accepted values: CSharp

Required: False
Position: Named
Default value: CSharp
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a108e-193">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="a108e-193">-LiteralPath</span></span>

<span data-ttu-id="a108e-194">Spécifie le chemin d'accès aux fichiers de code source ou aux fichiers DLL d'assembly contenant les types.</span><span class="sxs-lookup"><span data-stu-id="a108e-194">Specifies the path to source code files or assembly DLL files that contain the types.</span></span> <span data-ttu-id="a108e-195">Contrairement à **path** , la valeur du paramètre **LiteralPath** est utilisée exactement telle qu’elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="a108e-195">Unlike **Path** , the value of the **LiteralPath** parameter is used exactly as it's typed.</span></span> <span data-ttu-id="a108e-196">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="a108e-196">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="a108e-197">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="a108e-197">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="a108e-198">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="a108e-198">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: FromLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a108e-199">-MemberDefinition</span><span class="sxs-lookup"><span data-stu-id="a108e-199">-MemberDefinition</span></span>

<span data-ttu-id="a108e-200">Spécifie les nouvelles propriétés ou méthodes de la classe.</span><span class="sxs-lookup"><span data-stu-id="a108e-200">Specifies new properties or methods for the class.</span></span> <span data-ttu-id="a108e-201">`Add-Type` génère le code de modèle qui est requis pour prendre en charge les propriétés ou les méthodes.</span><span class="sxs-lookup"><span data-stu-id="a108e-201">`Add-Type` generates the template code that is required to support the properties or methods.</span></span>

<span data-ttu-id="a108e-202">Sur Windows, vous pouvez utiliser cette fonctionnalité pour effectuer des appels d’appel de code non managé (P/Invoke) à des fonctions non managées dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a108e-202">On Windows, you can use this feature to make Platform Invoke (P/Invoke) calls to unmanaged functions in PowerShell.</span></span>

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

### <span data-ttu-id="a108e-203">-Name</span><span class="sxs-lookup"><span data-stu-id="a108e-203">-Name</span></span>

<span data-ttu-id="a108e-204">Spécifie le nom de la classe à créer.</span><span class="sxs-lookup"><span data-stu-id="a108e-204">Specifies the name of the class to create.</span></span> <span data-ttu-id="a108e-205">Ce paramètre est obligatoire durant la génération d'un type à partir d'une définition de membre.</span><span class="sxs-lookup"><span data-stu-id="a108e-205">This parameter is required when generating a type from a member definition.</span></span>

<span data-ttu-id="a108e-206">Le nom de type et l'espace de noms doivent être uniques au sein d'une session.</span><span class="sxs-lookup"><span data-stu-id="a108e-206">The type name and namespace must be unique within a session.</span></span> <span data-ttu-id="a108e-207">Vous ne pouvez pas décharger un type ni le modifier.</span><span class="sxs-lookup"><span data-stu-id="a108e-207">You can't unload a type or change it.</span></span>
<span data-ttu-id="a108e-208">Pour modifier le code d’un type, vous devez modifier le nom ou démarrer une nouvelle session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a108e-208">To change the code for a type, you must change the name or start a new PowerShell session.</span></span>
<span data-ttu-id="a108e-209">Sinon, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="a108e-209">Otherwise, the command fails.</span></span>

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

### <span data-ttu-id="a108e-210">-Espace de noms</span><span class="sxs-lookup"><span data-stu-id="a108e-210">-Namespace</span></span>

<span data-ttu-id="a108e-211">Spécifie un espace de noms pour le type.</span><span class="sxs-lookup"><span data-stu-id="a108e-211">Specifies a namespace for the type.</span></span>

<span data-ttu-id="a108e-212">Si ce paramètre n’est pas inclus dans la commande, le type est créé dans l’espace de noms **Microsoft. PowerShell. Commands. AddType. AutogeneratedTypes** .</span><span class="sxs-lookup"><span data-stu-id="a108e-212">If this parameter isn't included in the command, the type is created in the **Microsoft.PowerShell.Commands.AddType.AutoGeneratedTypes** namespace.</span></span> <span data-ttu-id="a108e-213">Si le paramètre est inclus dans la commande avec une valeur de chaîne vide ou une valeur de `$Null` , le type est généré dans l’espace de noms global.</span><span class="sxs-lookup"><span data-stu-id="a108e-213">If the parameter is included in the command with an empty string value or a value of `$Null`, the type is generated in the global namespace.</span></span>

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

### <span data-ttu-id="a108e-214">-OutputAssembly</span><span class="sxs-lookup"><span data-stu-id="a108e-214">-OutputAssembly</span></span>

<span data-ttu-id="a108e-215">Génère un fichier DLL pour l'assembly ayant le nom spécifié à l'emplacement approprié.</span><span class="sxs-lookup"><span data-stu-id="a108e-215">Generates a DLL file for the assembly with the specified name in the location.</span></span> <span data-ttu-id="a108e-216">Entrez un chemin d’accès et un nom de fichier facultatifs.</span><span class="sxs-lookup"><span data-stu-id="a108e-216">Enter an optional path and filename.</span></span> <span data-ttu-id="a108e-217">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="a108e-217">Wildcard characters are permitted.</span></span> <span data-ttu-id="a108e-218">Par défaut, `Add-Type` génère l’assembly uniquement en mémoire.</span><span class="sxs-lookup"><span data-stu-id="a108e-218">By default, `Add-Type` generates the assembly only in memory.</span></span>

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

### <span data-ttu-id="a108e-219">-OutputType</span><span class="sxs-lookup"><span data-stu-id="a108e-219">-OutputType</span></span>

<span data-ttu-id="a108e-220">Spécifie le type de sortie de l'assembly de sortie.</span><span class="sxs-lookup"><span data-stu-id="a108e-220">Specifies the output type of the output assembly.</span></span> <span data-ttu-id="a108e-221">Par défaut, aucun type de sortie n'est spécifié.</span><span class="sxs-lookup"><span data-stu-id="a108e-221">By default, no output type is specified.</span></span> <span data-ttu-id="a108e-222">Ce paramètre est valide uniquement quand un assembly de sortie est spécifié dans la commande.</span><span class="sxs-lookup"><span data-stu-id="a108e-222">This parameter is valid only when an output assembly is specified in the command.</span></span> <span data-ttu-id="a108e-223">Pour plus d’informations sur les valeurs, consultez [énumération OutputAssemblyType](/dotnet/api/microsoft.powershell.commands.outputassemblytype).</span><span class="sxs-lookup"><span data-stu-id="a108e-223">For more information about the values, see [OutputAssemblyType Enumeration](/dotnet/api/microsoft.powershell.commands.outputassemblytype).</span></span>

<span data-ttu-id="a108e-224">Les valeurs acceptables pour ce paramètre sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="a108e-224">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="a108e-225">ConsoleApplication</span><span class="sxs-lookup"><span data-stu-id="a108e-225">ConsoleApplication</span></span>
- <span data-ttu-id="a108e-226">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="a108e-226">Library</span></span>
- <span data-ttu-id="a108e-227">Fichier WindowsApplication</span><span class="sxs-lookup"><span data-stu-id="a108e-227">WindowsApplication</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a108e-228">À partir de PowerShell 7,1, `ConsoleApplication` et ne `WindowsApplication` sont pas pris en charge et PowerShell lève une erreur de fin si l’un ou l’autre est spécifié en tant que valeurs pour le paramètre **OutputType** .</span><span class="sxs-lookup"><span data-stu-id="a108e-228">As of PowerShell 7.1, `ConsoleApplication` and `WindowsApplication` are not supported and PowerShell throws a terminating error if either are specified as values for the **OutputType** parameter.</span></span>

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

### <span data-ttu-id="a108e-229">-PassThru</span><span class="sxs-lookup"><span data-stu-id="a108e-229">-PassThru</span></span>

<span data-ttu-id="a108e-230">Retourne un objet **System.Runtime** qui représente les types ajoutés.</span><span class="sxs-lookup"><span data-stu-id="a108e-230">Returns a **System.Runtime** object that represents the types that were added.</span></span> <span data-ttu-id="a108e-231">Par défaut, cette applet de commande ne génère pas de sortie.</span><span class="sxs-lookup"><span data-stu-id="a108e-231">By default, this cmdlet doesn't generate any output.</span></span>

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

### <span data-ttu-id="a108e-232">-Path</span><span class="sxs-lookup"><span data-stu-id="a108e-232">-Path</span></span>

<span data-ttu-id="a108e-233">Spécifie le chemin d'accès aux fichiers de code source ou aux fichiers DLL d'assembly contenant les types.</span><span class="sxs-lookup"><span data-stu-id="a108e-233">Specifies the path to source code files or assembly DLL files that contain the types.</span></span>

<span data-ttu-id="a108e-234">Si vous envoyez des fichiers de code source, `Add-Type` compile le code dans les fichiers et crée un assembly en mémoire des types.</span><span class="sxs-lookup"><span data-stu-id="a108e-234">If you submit source code files, `Add-Type` compiles the code in the files and creates an in-memory assembly of the types.</span></span> <span data-ttu-id="a108e-235">L’extension de fichier spécifiée dans la valeur de **path** détermine le compilateur utilisé par `Add-Type` .</span><span class="sxs-lookup"><span data-stu-id="a108e-235">The file extension specified in the value of **Path** determines the compiler that `Add-Type` uses.</span></span>

<span data-ttu-id="a108e-236">Si vous envoyez un fichier d’assembly, `Add-Type` utilise les types de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="a108e-236">If you submit an assembly file, `Add-Type` takes the types from the assembly.</span></span> <span data-ttu-id="a108e-237">Pour spécifier un assembly en mémoire ou le Global Assembly Cache, utilisez le paramètre **AssemblyName** .</span><span class="sxs-lookup"><span data-stu-id="a108e-237">To specify an in-memory assembly or the global assembly cache, use the **AssemblyName** parameter.</span></span>

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

### <span data-ttu-id="a108e-238">-ReferencedAssemblies</span><span class="sxs-lookup"><span data-stu-id="a108e-238">-ReferencedAssemblies</span></span>

<span data-ttu-id="a108e-239">Spécifie les assemblys dont dépend le type.</span><span class="sxs-lookup"><span data-stu-id="a108e-239">Specifies the assemblies upon which the type depends.</span></span> <span data-ttu-id="a108e-240">Par défaut, `Add-Type` `System.dll` les références et `System.Management.Automation.dll` .</span><span class="sxs-lookup"><span data-stu-id="a108e-240">By default, `Add-Type` references `System.dll` and `System.Management.Automation.dll`.</span></span> <span data-ttu-id="a108e-241">Les assemblys que vous spécifiez à l'aide de ce paramètre sont référencés en plus des assemblys par défaut.</span><span class="sxs-lookup"><span data-stu-id="a108e-241">The assemblies that you specify by using this parameter are referenced in addition to the default assemblies.</span></span>

<span data-ttu-id="a108e-242">À compter de PowerShell 6, **ReferencedAssemblies** n’inclut pas les assemblys .NET par défaut.</span><span class="sxs-lookup"><span data-stu-id="a108e-242">Beginning in PowerShell 6, **ReferencedAssemblies** doesn't include the default .NET assemblies.</span></span> <span data-ttu-id="a108e-243">Vous devez inclure une référence spécifique à celles-ci dans la valeur transmise à ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="a108e-243">You must include a specific reference to them in the value passed to this parameter.</span></span>

<span data-ttu-id="a108e-244">Vous ne pouvez pas utiliser les paramètres **CompilerOptions** et **ReferencedAssemblies** dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="a108e-244">You can't use the **CompilerOptions** and **ReferencedAssemblies** parameters in the same command.</span></span>

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

### <span data-ttu-id="a108e-245">-TypeDefinition</span><span class="sxs-lookup"><span data-stu-id="a108e-245">-TypeDefinition</span></span>

<span data-ttu-id="a108e-246">Spécifie le code source qui contient les définitions de type.</span><span class="sxs-lookup"><span data-stu-id="a108e-246">Specifies the source code that contains the type definitions.</span></span> <span data-ttu-id="a108e-247">Entrez le code source dans une chaîne ou une chaîne here-string, ou entrez une variable qui contient le code source.</span><span class="sxs-lookup"><span data-stu-id="a108e-247">Enter the source code in a string or here-string, or enter a variable that contains the source code.</span></span> <span data-ttu-id="a108e-248">Pour plus d’informations sur les chaînes ici, consultez [about_Quoting_Rules](../Microsoft.PowerShell.Core/about/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="a108e-248">For more information about here-strings, see [about_Quoting_Rules](../Microsoft.PowerShell.Core/about/about_Quoting_Rules.md).</span></span>

<span data-ttu-id="a108e-249">Incluez une déclaration d'espace de noms dans votre définition de type.</span><span class="sxs-lookup"><span data-stu-id="a108e-249">Include a namespace declaration in your type definition.</span></span> <span data-ttu-id="a108e-250">Si vous omettez la déclaration d'espace de noms, votre type risque d'avoir le même nom qu'un autre type ou que le raccourci d'un autre type, ce qui entraînera un remplacement involontaire.</span><span class="sxs-lookup"><span data-stu-id="a108e-250">If you omit the namespace declaration, your type might have the same name as another type or the shortcut for another type, causing an unintentional overwrite.</span></span> <span data-ttu-id="a108e-251">Par exemple, si vous définissez un type appelé **exception** , les scripts qui utilisent une **exception** comme raccourci pour **System. exception** échoueront.</span><span class="sxs-lookup"><span data-stu-id="a108e-251">For example, if you define a type called **Exception** , scripts that use **Exception** as the shortcut for **System.Exception** will fail.</span></span>

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

### <span data-ttu-id="a108e-252">-UsingNamespace</span><span class="sxs-lookup"><span data-stu-id="a108e-252">-UsingNamespace</span></span>

<span data-ttu-id="a108e-253">Spécifie les autres espaces de noms nécessaires pour la classe.</span><span class="sxs-lookup"><span data-stu-id="a108e-253">Specifies other namespaces that are required for the class.</span></span> <span data-ttu-id="a108e-254">C’est très similaire au mot clé C#, `Using` .</span><span class="sxs-lookup"><span data-stu-id="a108e-254">This is much like the C# keyword, `Using`.</span></span>

<span data-ttu-id="a108e-255">Par défaut, `Add-Type` fait référence à l’espace de noms **System** .</span><span class="sxs-lookup"><span data-stu-id="a108e-255">By default, `Add-Type` references the **System** namespace.</span></span> <span data-ttu-id="a108e-256">Lorsque le paramètre **MemberDefinition** est utilisé, `Add-Type` fait également référence à l’espace de noms **System. Runtime. InteropServices** par défaut.</span><span class="sxs-lookup"><span data-stu-id="a108e-256">When the **MemberDefinition** parameter is used, `Add-Type` also references the **System.Runtime.InteropServices** namespace by default.</span></span> <span data-ttu-id="a108e-257">Les espaces de noms que vous ajoutez à l'aide du paramètre **UsingNamespace** sont référencés en plus des espaces de noms par défaut.</span><span class="sxs-lookup"><span data-stu-id="a108e-257">The namespaces that you add by using the **UsingNamespace** parameter are referenced in addition to the default namespaces.</span></span>

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

### <span data-ttu-id="a108e-258">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a108e-258">CommonParameters</span></span>

<span data-ttu-id="a108e-259">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a108e-259">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a108e-260">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="a108e-260">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a108e-261">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="a108e-261">INPUTS</span></span>

### <span data-ttu-id="a108e-262">Aucun</span><span class="sxs-lookup"><span data-stu-id="a108e-262">None</span></span>

<span data-ttu-id="a108e-263">Vous ne pouvez pas envoyer d’objets dans le pipeline vers `Add-Type` .</span><span class="sxs-lookup"><span data-stu-id="a108e-263">You can't send objects down the pipeline to `Add-Type`.</span></span>

## <span data-ttu-id="a108e-264">SORTIES</span><span class="sxs-lookup"><span data-stu-id="a108e-264">OUTPUTS</span></span>

### <span data-ttu-id="a108e-265">None ou System. type</span><span class="sxs-lookup"><span data-stu-id="a108e-265">None or System.Type</span></span>

<span data-ttu-id="a108e-266">Quand vous utilisez le paramètre **PassThru** , `Add-Type` retourne un objet **System. type** qui représente le nouveau type.</span><span class="sxs-lookup"><span data-stu-id="a108e-266">When you use the **PassThru** parameter, `Add-Type` returns a **System.Type** object that represents the new type.</span></span> <span data-ttu-id="a108e-267">Sinon, cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="a108e-267">Otherwise, this cmdlet doesn't generate any output.</span></span>

## <span data-ttu-id="a108e-268">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="a108e-268">NOTES</span></span>

<span data-ttu-id="a108e-269">Les types que vous ajoutez existent uniquement dans la session active.</span><span class="sxs-lookup"><span data-stu-id="a108e-269">The types that you add exist only in the current session.</span></span> <span data-ttu-id="a108e-270">Pour utiliser les types dans toutes les sessions, ajoutez-les à votre profil PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a108e-270">To use the types in all sessions, add them to your PowerShell profile.</span></span> <span data-ttu-id="a108e-271">Pour plus d’informations sur le profil, consultez [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span><span class="sxs-lookup"><span data-stu-id="a108e-271">For more information about the profile, see [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span></span>

<span data-ttu-id="a108e-272">Les noms de types et les espaces de noms doivent être uniques au sein d’une session.</span><span class="sxs-lookup"><span data-stu-id="a108e-272">Type names and namespaces must be unique within a session.</span></span> <span data-ttu-id="a108e-273">Vous ne pouvez pas décharger un type ni le modifier.</span><span class="sxs-lookup"><span data-stu-id="a108e-273">You can't unload a type or change it.</span></span> <span data-ttu-id="a108e-274">Si vous avez besoin de modifier le code d’un type, vous devez modifier le nom ou démarrer une nouvelle session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a108e-274">If you need to change the code for a type, you must change the name or start a new PowerShell session.</span></span>
<span data-ttu-id="a108e-275">Sinon, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="a108e-275">Otherwise, the command fails.</span></span>

<span data-ttu-id="a108e-276">Dans Windows PowerShell (version 5,1 et versions antérieures), vous devez utiliser `Add-Type` pour tout ce qui n’est pas déjà chargé.</span><span class="sxs-lookup"><span data-stu-id="a108e-276">In Windows PowerShell (version 5.1 and below), you need to use `Add-Type` for anything that isn't already loaded.</span></span> <span data-ttu-id="a108e-277">En règle générale, cela s’applique aux assemblys figurant dans le global assembly cache (GAC).</span><span class="sxs-lookup"><span data-stu-id="a108e-277">Most commonly, this applies to assemblies found in the Global Assembly Cache (GAC).</span></span>
<span data-ttu-id="a108e-278">Dans PowerShell 6 et versions ultérieures, il n’y a aucun GAC, de sorte que PowerShell installe ses propres assemblys dans `$PSHome` .</span><span class="sxs-lookup"><span data-stu-id="a108e-278">In PowerShell 6 and higher, there is no GAC, so PowerShell installs its own assemblies in `$PSHome`.</span></span>
<span data-ttu-id="a108e-279">Ces assemblys sont automatiquement chargés à la demande. il n’est donc pas nécessaire d’utiliser `Add-Type` pour les charger.</span><span class="sxs-lookup"><span data-stu-id="a108e-279">These assemblies are automatically loaded on request, so there's no need to use `Add-Type` to load them.</span></span> <span data-ttu-id="a108e-280">Toutefois, l’utilisation de `Add-Type` est toujours autorisée pour permettre aux scripts d’être implicitement compatibles avec n’importe quelle version de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a108e-280">However, using `Add-Type` is still permitted to allow scripts to be implicitly compatible with any version of PowerShell.</span></span>

<span data-ttu-id="a108e-281">Les assemblys dans le GAC peuvent être chargés par nom de type, plutôt que par chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="a108e-281">Assemblies in the GAC can be loaded by type name, rather than by path.</span></span> <span data-ttu-id="a108e-282">Le chargement d’assemblys à partir d’un chemin d’accès arbitraire requiert `Add-Type` , car ces assemblys ne peuvent pas être chargés automatiquement.</span><span class="sxs-lookup"><span data-stu-id="a108e-282">Loading assemblies from an arbitrary path requires `Add-Type`, since those assemblies cannot not be loaded automatically.</span></span>

## <span data-ttu-id="a108e-283">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="a108e-283">RELATED LINKS</span></span>

[<span data-ttu-id="a108e-284">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="a108e-284">about_Profiles</span></span>](../Microsoft.PowerShell.Core/About/about_profiles.md)

[<span data-ttu-id="a108e-285">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="a108e-285">about_Quoting_Rules</span></span>](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md)

[<span data-ttu-id="a108e-286">Add-Member</span><span class="sxs-lookup"><span data-stu-id="a108e-286">Add-Member</span></span>](Add-Member.md)

[<span data-ttu-id="a108e-287">New-Object</span><span class="sxs-lookup"><span data-stu-id="a108e-287">New-Object</span></span>](New-Object.md)

[<span data-ttu-id="a108e-288">OutputAssemblyType</span><span class="sxs-lookup"><span data-stu-id="a108e-288">OutputAssemblyType</span></span>](/dotnet/api/microsoft.powershell.commands.outputassemblytype)

[<span data-ttu-id="a108e-289">Appel de code non managé (P/Invoke)</span><span class="sxs-lookup"><span data-stu-id="a108e-289">Platform Invoke (P/Invoke)</span></span>](/dotnet/standard/native-interop/pinvoke)

[<span data-ttu-id="a108e-290">Where-Object</span><span class="sxs-lookup"><span data-stu-id="a108e-290">Where-Object</span></span>](../Microsoft.PowerShell.Core/Where-Object.md)
