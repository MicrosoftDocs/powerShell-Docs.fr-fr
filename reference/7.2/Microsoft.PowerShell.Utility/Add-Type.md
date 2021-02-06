---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/add-type?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-Type
ms.openlocfilehash: d55925b0580542459e62e60108f855508232f232
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598980"
---
# <span data-ttu-id="230ec-102">Add-Type</span><span class="sxs-lookup"><span data-stu-id="230ec-102">Add-Type</span></span>

## <span data-ttu-id="230ec-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="230ec-103">SYNOPSIS</span></span>
<span data-ttu-id="230ec-104">Ajoute une classe Microsoft .NET Core à une session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="230ec-104">Adds a Microsoft .NET Core class to a PowerShell session.</span></span>

## <span data-ttu-id="230ec-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="230ec-105">SYNTAX</span></span>

### <span data-ttu-id="230ec-106">FromSource (par défaut)</span><span class="sxs-lookup"><span data-stu-id="230ec-106">FromSource (Default)</span></span>

```
Add-Type [-TypeDefinition] <String> [-Language <Language>] [-ReferencedAssemblies <String[]>]
 [-OutputAssembly <String>] [-OutputType <OutputAssemblyType>] [-PassThru] [-IgnoreWarnings]
 [-CompilerOptions <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="230ec-107">FromMember</span><span class="sxs-lookup"><span data-stu-id="230ec-107">FromMember</span></span>

```
Add-Type [-Name] <String> [-MemberDefinition] <String[]> [-Namespace <String>]
 [-UsingNamespace <String[]>] [-Language <Language>] [-ReferencedAssemblies <String[]>]
 [-OutputAssembly <String>] [-OutputType <OutputAssemblyType>] [-PassThru] [-IgnoreWarnings]
 [-CompilerOptions <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="230ec-108">FromPath</span><span class="sxs-lookup"><span data-stu-id="230ec-108">FromPath</span></span>

```
Add-Type [-Path] <String[]> [-ReferencedAssemblies <String[]>] [-OutputAssembly <String>]
 [-OutputType <OutputAssemblyType>] [-PassThru] [-IgnoreWarnings] [-CompilerOptions <String[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="230ec-109">FromLiteralPath</span><span class="sxs-lookup"><span data-stu-id="230ec-109">FromLiteralPath</span></span>

```
Add-Type -LiteralPath <String[]> [-ReferencedAssemblies <String[]>] [-OutputAssembly <String>]
 [-OutputType <OutputAssemblyType>] [-PassThru] [-IgnoreWarnings] [-CompilerOptions <String[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="230ec-110">FromAssemblyName</span><span class="sxs-lookup"><span data-stu-id="230ec-110">FromAssemblyName</span></span>

```
Add-Type -AssemblyName <String[]> [-PassThru] [<CommonParameters>]
```

## <span data-ttu-id="230ec-111">Description</span><span class="sxs-lookup"><span data-stu-id="230ec-111">DESCRIPTION</span></span>

<span data-ttu-id="230ec-112">L' `Add-Type` applet de commande vous permet de définir une classe de base Microsoft .net dans votre session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="230ec-112">The `Add-Type` cmdlet lets you define a Microsoft .NET Core class in your PowerShell session.</span></span> <span data-ttu-id="230ec-113">Vous pouvez ensuite instancier des objets, à l’aide de l’applet de commande `New-Object` , et utiliser les objets comme vous le feriez pour n’importe quel objet .net core.</span><span class="sxs-lookup"><span data-stu-id="230ec-113">You can then instantiate objects, by using the `New-Object` cmdlet, and use the objects just as you would use any .NET Core object.</span></span> <span data-ttu-id="230ec-114">Si vous ajoutez une `Add-Type` commande à votre profil PowerShell, la classe est disponible dans toutes les sessions PowerShell.</span><span class="sxs-lookup"><span data-stu-id="230ec-114">If you add an `Add-Type` command to your PowerShell profile, the class is available in all PowerShell sessions.</span></span>

<span data-ttu-id="230ec-115">Vous pouvez spécifier le type en désignant un assembly existant ou des fichiers de code source. Par ailleurs, vous pouvez spécifier le code source inline ou enregistré dans une variable.</span><span class="sxs-lookup"><span data-stu-id="230ec-115">You can specify the type by specifying an existing assembly or source code files, or you can specify the source code inline or saved in a variable.</span></span> <span data-ttu-id="230ec-116">Vous pouvez même spécifier uniquement une méthode et `Add-Type` définit et génère la classe.</span><span class="sxs-lookup"><span data-stu-id="230ec-116">You can even specify only a method and `Add-Type` defines and generates the class.</span></span> <span data-ttu-id="230ec-117">Sur Windows, vous pouvez utiliser cette fonctionnalité pour effectuer des appels d’appel de code non managé (P/Invoke) à des fonctions non managées dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="230ec-117">On Windows, you can use this feature to make Platform Invoke (P/Invoke) calls to unmanaged functions in PowerShell.</span></span> <span data-ttu-id="230ec-118">Si vous spécifiez le code source, `Add-Type` compile le code source spécifié et génère un assembly en mémoire qui contient les nouveaux types .net core.</span><span class="sxs-lookup"><span data-stu-id="230ec-118">If you specify source code, `Add-Type` compiles the specified source code and generates an in-memory assembly that contains the new .NET Core types.</span></span>

<span data-ttu-id="230ec-119">Vous pouvez utiliser les paramètres de `Add-Type` pour spécifier un autre langage et un autre compilateur, C# est l’option par défaut, les options du compilateur, les dépendances de l’assembly, l’espace de noms de la classe, les noms du type et l’assembly résultant.</span><span class="sxs-lookup"><span data-stu-id="230ec-119">You can use the parameters of `Add-Type` to specify an alternate language and compiler, C# is the default, compiler options, assembly dependencies, the class namespace, the names of the type, and the resulting assembly.</span></span>

<span data-ttu-id="230ec-120">À compter de PowerShell 7, `Add-Type` ne compile pas un type si un type portant le même nom existe déjà.</span><span class="sxs-lookup"><span data-stu-id="230ec-120">Beginning in PowerShell 7, `Add-Type` does not compile a type if a type with the same name already exists.</span></span> <span data-ttu-id="230ec-121">Recherche également les `Add-Type` assemblys dans un `ref` dossier sous le dossier qui contient `pwsh.dll` .</span><span class="sxs-lookup"><span data-stu-id="230ec-121">Also, `Add-Type` looks for assemblies in a `ref` folder under the folder that contains `pwsh.dll`.</span></span>

## <span data-ttu-id="230ec-122">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="230ec-122">EXAMPLES</span></span>

### <span data-ttu-id="230ec-123">Exemple 1 : ajouter un type .NET à une session</span><span class="sxs-lookup"><span data-stu-id="230ec-123">Example 1: Add a .NET type to a session</span></span>

<span data-ttu-id="230ec-124">Cet exemple ajoute la classe **BasicTest** à la session en spécifiant le code source stocké dans une variable.</span><span class="sxs-lookup"><span data-stu-id="230ec-124">This example adds the **BasicTest** class to the session by specifying source code that is stored in a variable.</span></span> <span data-ttu-id="230ec-125">La classe **BasicTest** est utilisée pour ajouter des entiers, créer un objet et multiplier des entiers.</span><span class="sxs-lookup"><span data-stu-id="230ec-125">The **BasicTest** class is used to add integers, create an object, and multiply integers.</span></span>

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

<span data-ttu-id="230ec-126">La `$Source` variable stocke le code source de la classe.</span><span class="sxs-lookup"><span data-stu-id="230ec-126">The `$Source` variable stores the source code for the class.</span></span> <span data-ttu-id="230ec-127">Le type a une méthode statique appelée `Add` et une méthode non statique appelée `Multiply` .</span><span class="sxs-lookup"><span data-stu-id="230ec-127">The type has a static method called `Add` and a non-static method called `Multiply`.</span></span>

<span data-ttu-id="230ec-128">L' `Add-Type` applet de commande ajoute la classe à la session.</span><span class="sxs-lookup"><span data-stu-id="230ec-128">The `Add-Type` cmdlet adds the class to the session.</span></span> <span data-ttu-id="230ec-129">Comme il utilise le code source en ligne, la commande utilise le paramètre **TypeDefinition** pour spécifier le code dans la `$Source` variable.</span><span class="sxs-lookup"><span data-stu-id="230ec-129">Because it's using inline source code, the command uses the **TypeDefinition** parameter to specify the code in the `$Source` variable.</span></span>

<span data-ttu-id="230ec-130">La `Add` méthode statique de la classe **BasicTest** utilise les caractères double deux-points ( `::` ) pour spécifier un membre statique de la classe.</span><span class="sxs-lookup"><span data-stu-id="230ec-130">The `Add` static method of the **BasicTest** class uses the double-colon characters (`::`) to specify a static member of the class.</span></span> <span data-ttu-id="230ec-131">Les entiers sont ajoutés et la somme est affichée.</span><span class="sxs-lookup"><span data-stu-id="230ec-131">The integers are added and the sum is displayed.</span></span>

<span data-ttu-id="230ec-132">L' `New-Object` applet de commande instancie une instance de la classe **BasicTest** .</span><span class="sxs-lookup"><span data-stu-id="230ec-132">The `New-Object` cmdlet instantiates an instance of the **BasicTest** class.</span></span> <span data-ttu-id="230ec-133">Elle enregistre le nouvel objet dans la `$BasicTestObject` variable.</span><span class="sxs-lookup"><span data-stu-id="230ec-133">It saves the new object in the `$BasicTestObject` variable.</span></span>

<span data-ttu-id="230ec-134">`$BasicTestObject` utilise la `Multiply` méthode.</span><span class="sxs-lookup"><span data-stu-id="230ec-134">`$BasicTestObject` uses the `Multiply` method.</span></span> <span data-ttu-id="230ec-135">Les entiers sont multipliés et le produit est affiché.</span><span class="sxs-lookup"><span data-stu-id="230ec-135">The integers are multiplied and the product is displayed.</span></span>

### <span data-ttu-id="230ec-136">Exemple 2 : examiner un type ajouté</span><span class="sxs-lookup"><span data-stu-id="230ec-136">Example 2: Examine an added type</span></span>

<span data-ttu-id="230ec-137">Cet exemple utilise l' `Get-Member` applet de commande pour examiner les objets `Add-Type` créés par les `New-Object` applets de commande et dans l' **exemple 1**.</span><span class="sxs-lookup"><span data-stu-id="230ec-137">This example uses the `Get-Member` cmdlet to examine the objects that the `Add-Type` and `New-Object` cmdlets created in **Example 1**.</span></span>

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

<span data-ttu-id="230ec-138">L' `Get-Member` applet de commande obtient le type et les membres de la classe **BasicTest** qui ont `Add-Type` été ajoutés à la session.</span><span class="sxs-lookup"><span data-stu-id="230ec-138">The `Get-Member` cmdlet gets the type and members of the **BasicTest** class that `Add-Type` added to the session.</span></span> <span data-ttu-id="230ec-139">La `Get-Member` commande révèle qu’il s’agit d’un objet **System. RuntimeType** , dérivé de la classe **System. Object** .</span><span class="sxs-lookup"><span data-stu-id="230ec-139">The `Get-Member` command reveals that it's a **System.RuntimeType** object, which is derived from the **System.Object** class.</span></span>

<span data-ttu-id="230ec-140">Le `Get-Member` paramètre **static** obtient les propriétés et les méthodes statiques de la classe **BasicTest** .</span><span class="sxs-lookup"><span data-stu-id="230ec-140">The `Get-Member` **Static** parameter gets the static properties and methods of the **BasicTest** class.</span></span> <span data-ttu-id="230ec-141">La sortie indique que la `Add` méthode est incluse.</span><span class="sxs-lookup"><span data-stu-id="230ec-141">The output shows that the `Add` method is included.</span></span>

<span data-ttu-id="230ec-142">L' `Get-Member` applet de commande obtient les membres de l’objet stocké dans la `$BasicTestObject` variable.</span><span class="sxs-lookup"><span data-stu-id="230ec-142">The `Get-Member` cmdlet gets the members of the object stored in the `$BasicTestObject` variable.</span></span>
<span data-ttu-id="230ec-143">`$BasicTestObject` a été créé à l’aide de l' `New-Object` applet de commande avec la classe **BasicTest** .</span><span class="sxs-lookup"><span data-stu-id="230ec-143">`$BasicTestObject` was created by using the `New-Object` cmdlet with the **BasicTest** class.</span></span> <span data-ttu-id="230ec-144">La sortie révèle que la valeur de la `$BasicTestObject` variable est une instance de la classe **BasicTest** et qu’elle comprend un membre appelé `Multiply` .</span><span class="sxs-lookup"><span data-stu-id="230ec-144">The output reveals that the value of the `$BasicTestObject` variable is an instance of the **BasicTest** class and that it includes a member called `Multiply`.</span></span>

### <span data-ttu-id="230ec-145">Exemple 3 : ajouter des types à partir d’un assembly</span><span class="sxs-lookup"><span data-stu-id="230ec-145">Example 3: Add types from an assembly</span></span>

<span data-ttu-id="230ec-146">Cet exemple ajoute les classes de l' `NJsonSchema.dll` assembly à la session active.</span><span class="sxs-lookup"><span data-stu-id="230ec-146">This example adds the classes from the `NJsonSchema.dll` assembly to the current session.</span></span>

```powershell
Set-Location -Path $PSHOME
$AccType = Add-Type -AssemblyName *jsonschema* -PassThru
```

<span data-ttu-id="230ec-147">`Set-Location` utilise le paramètre **path** pour spécifier la `$PSHOME` variable.</span><span class="sxs-lookup"><span data-stu-id="230ec-147">`Set-Location` uses the **Path** parameter to specify the `$PSHOME` variable.</span></span> <span data-ttu-id="230ec-148">La variable référence le répertoire d’installation de PowerShell dans lequel se trouve le fichier DLL.</span><span class="sxs-lookup"><span data-stu-id="230ec-148">The variable references the PowerShell installation directory where the DLL file is located.</span></span>

<span data-ttu-id="230ec-149">La `$AccType` variable stocke un objet créé avec l’applet de commande `Add-Type` .</span><span class="sxs-lookup"><span data-stu-id="230ec-149">The `$AccType` variable stores an object created with the `Add-Type` cmdlet.</span></span> <span data-ttu-id="230ec-150">`Add-Type` utilise le paramètre **AssemblyName** pour spécifier le nom de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="230ec-150">`Add-Type` uses the **AssemblyName** parameter to specify the name of the assembly.</span></span> <span data-ttu-id="230ec-151">Le `*` caractère générique astérisque () vous permet d’accéder à l’assembly approprié même si vous n’êtes pas sûr de son nom ou de son orthographe.</span><span class="sxs-lookup"><span data-stu-id="230ec-151">The asterisk (`*`) wildcard character allows you to get the correct assembly even when you aren't sure of the name or its spelling.</span></span> <span data-ttu-id="230ec-152">Le paramètre **PassThru** génère des objets qui représentent les classes ajoutées à la session.</span><span class="sxs-lookup"><span data-stu-id="230ec-152">The **PassThru** parameter generates objects that represent the classes that are added to the session.</span></span>

### <span data-ttu-id="230ec-153">Exemple 4 : appeler des API Windows natives</span><span class="sxs-lookup"><span data-stu-id="230ec-153">Example 4: Call native Windows APIs</span></span>

<span data-ttu-id="230ec-154">Cet exemple montre comment appeler des API Windows natives dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="230ec-154">This example demonstrates how to call native Windows APIs in PowerShell.</span></span> <span data-ttu-id="230ec-155">`Add-Type` utilise le mécanisme d’appel de code non managé (P/Invoke) pour appeler une fonction dans `User32.dll` à partir de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="230ec-155">`Add-Type` uses the Platform Invoke (P/Invoke) mechanism to call a function in `User32.dll` from PowerShell.</span></span> <span data-ttu-id="230ec-156">Cet exemple fonctionne uniquement sur les ordinateurs exécutant le système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="230ec-156">This example only works on computers running the Windows operating system.</span></span>

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

<span data-ttu-id="230ec-157">La `$Signature` variable stocke la signature C# de la `ShowWindowAsync` fonction.</span><span class="sxs-lookup"><span data-stu-id="230ec-157">The `$Signature` variable stores the C# signature of the `ShowWindowAsync` function.</span></span> <span data-ttu-id="230ec-158">Pour vous assurer que la méthode résultante est visible dans une session PowerShell, le `public` mot clé a été ajouté à la signature standard.</span><span class="sxs-lookup"><span data-stu-id="230ec-158">To ensure that the resulting method is visible in a PowerShell session, the `public` keyword was added to the standard signature.</span></span> <span data-ttu-id="230ec-159">Pour plus d’informations, consultez [fonction ShowWindowAsync](/windows/win32/api/winuser/nf-winuser-showwindowasync).</span><span class="sxs-lookup"><span data-stu-id="230ec-159">For more information, see [ShowWindowAsync function](/windows/win32/api/winuser/nf-winuser-showwindowasync).</span></span>

<span data-ttu-id="230ec-160">La `$ShowWindowAsync` variable stocke l’objet créé par le `Add-Type` paramètre **PassThru** .</span><span class="sxs-lookup"><span data-stu-id="230ec-160">The `$ShowWindowAsync` variable stores the object created by the `Add-Type` **PassThru** parameter.</span></span>
<span data-ttu-id="230ec-161">L' `Add-Type` applet de commande ajoute la `ShowWindowAsync` fonction à la session PowerShell en tant que méthode statique.</span><span class="sxs-lookup"><span data-stu-id="230ec-161">The `Add-Type` cmdlet adds the `ShowWindowAsync` function to the PowerShell session as a static method.</span></span> <span data-ttu-id="230ec-162">La commande utilise le paramètre **MemberDefinition** pour spécifier la définition de méthode enregistrée dans la `$Signature` variable.</span><span class="sxs-lookup"><span data-stu-id="230ec-162">The command uses the **MemberDefinition** parameter to specify the method definition saved in the `$Signature` variable.</span></span> <span data-ttu-id="230ec-163">La commande utilise les paramètres **Name** et **Namespace** pour spécifier le nom et l'espace de noms de la classe.</span><span class="sxs-lookup"><span data-stu-id="230ec-163">The command uses the **Name** and **Namespace** parameters to specify a name and namespace for the class.</span></span> <span data-ttu-id="230ec-164">Le paramètre **PassThru** génère un objet qui représente les types.</span><span class="sxs-lookup"><span data-stu-id="230ec-164">The **PassThru** parameter generates an object that represents the types.</span></span>

<span data-ttu-id="230ec-165">La nouvelle `ShowWindowAsync` méthode statique est utilisée dans les commandes pour réduire et restaurer la console PowerShell.</span><span class="sxs-lookup"><span data-stu-id="230ec-165">The new `ShowWindowAsync` static method is used in the commands to minimize and restore the PowerShell console.</span></span> <span data-ttu-id="230ec-166">La méthode accepte deux paramètres : le handle de fenêtre et un entier qui spécifie le mode d’affichage de la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="230ec-166">The method takes two parameters: the window handle, and an integer that specifies how the window is displayed.</span></span>

<span data-ttu-id="230ec-167">Pour réduire la console PowerShell, `ShowWindowAsync` utilise l' `Get-Process` applet de commande avec la `$PID` variable automatique pour recevoir le processus qui héberge la session PowerShell active.</span><span class="sxs-lookup"><span data-stu-id="230ec-167">To minimize the PowerShell console, `ShowWindowAsync` uses the `Get-Process` cmdlet with the `$PID` automatic variable to get the process that is hosting the current PowerShell session.</span></span> <span data-ttu-id="230ec-168">Elle utilise ensuite la propriété **MainWindowHandle** du processus actuel et la valeur `2` , qui représente la `SW_MINIMIZE` valeur.</span><span class="sxs-lookup"><span data-stu-id="230ec-168">Then it uses the **MainWindowHandle** property of the current process and a value of `2`, which represents the `SW_MINIMIZE` value.</span></span>

<span data-ttu-id="230ec-169">Pour restaurer la fenêtre, `ShowWindowAsync` utilise la valeur `4` pour la position de la fenêtre, qui représente la `SW_RESTORE` valeur.</span><span class="sxs-lookup"><span data-stu-id="230ec-169">To restore the window, `ShowWindowAsync` uses a value of `4` for the window position, which represents the `SW_RESTORE` value.</span></span>

<span data-ttu-id="230ec-170">Pour agrandir la fenêtre, utilisez la valeur de `3` qui est représentée par `SW_MAXIMIZE` .</span><span class="sxs-lookup"><span data-stu-id="230ec-170">To maximize the window, use the value of `3` that represents `SW_MAXIMIZE`.</span></span>

## <span data-ttu-id="230ec-171">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="230ec-171">PARAMETERS</span></span>

### <span data-ttu-id="230ec-172">-AssemblyName</span><span class="sxs-lookup"><span data-stu-id="230ec-172">-AssemblyName</span></span>

<span data-ttu-id="230ec-173">Spécifie le nom d'un assembly qui inclut les types.</span><span class="sxs-lookup"><span data-stu-id="230ec-173">Specifies the name of an assembly that includes the types.</span></span> <span data-ttu-id="230ec-174">`Add-Type` prend les types de l’assembly spécifié.</span><span class="sxs-lookup"><span data-stu-id="230ec-174">`Add-Type` takes the types from the specified assembly.</span></span> <span data-ttu-id="230ec-175">Ce paramètre est obligatoire lorsque vous créez des types basés sur un nom d’assembly.</span><span class="sxs-lookup"><span data-stu-id="230ec-175">This parameter is required when you're creating types based on an assembly name.</span></span>

<span data-ttu-id="230ec-176">Entrez le nom complet ou simple, également appelé « nom partiel », d’un assembly.</span><span class="sxs-lookup"><span data-stu-id="230ec-176">Enter the full or simple name, also known as the partial name, of an assembly.</span></span> <span data-ttu-id="230ec-177">Les caractères génériques sont autorisés dans le nom de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="230ec-177">Wildcard characters are permitted in the assembly name.</span></span> <span data-ttu-id="230ec-178">Si vous entrez un nom simple ou partiel, `Add-Type` le résout en nom complet, puis utilise le nom complet pour charger l’assembly.</span><span class="sxs-lookup"><span data-stu-id="230ec-178">If you enter a simple or partial name, `Add-Type` resolves it to the full name, and then uses the full name to load the assembly.</span></span>

<span data-ttu-id="230ec-179">Ce paramètre n’accepte pas de chemin d’accès ou de nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="230ec-179">This parameter doesn't accept a path or a filename.</span></span> <span data-ttu-id="230ec-180">Pour entrer le chemin d’accès au fichier de bibliothèque de liens dynamiques (DLL) de l’assembly, utilisez le paramètre **path** .</span><span class="sxs-lookup"><span data-stu-id="230ec-180">To enter the path to the assembly dynamic-link library (DLL) file, use the **Path** parameter.</span></span>

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

### <span data-ttu-id="230ec-181">-CompilerOptions</span><span class="sxs-lookup"><span data-stu-id="230ec-181">-CompilerOptions</span></span>

<span data-ttu-id="230ec-182">Spécifie les options du compilateur de code source.</span><span class="sxs-lookup"><span data-stu-id="230ec-182">Specifies the options for the source code compiler.</span></span> <span data-ttu-id="230ec-183">Ces options sont envoyées au compilateur sans révision.</span><span class="sxs-lookup"><span data-stu-id="230ec-183">These options are sent to the compiler without revision.</span></span>

<span data-ttu-id="230ec-184">Ce paramètre vous permet de demander au compilateur de générer un fichier exécutable, d’incorporer des ressources ou de définir des options de ligne de commande, telles que l' `/unsafe` option.</span><span class="sxs-lookup"><span data-stu-id="230ec-184">This parameter allows you to direct the compiler to generate an executable file, embed resources, or set command-line options, such as the `/unsafe` option.</span></span>

<span data-ttu-id="230ec-185">Vous ne pouvez pas utiliser les paramètres **CompilerOptions** et **ReferencedAssemblies** dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="230ec-185">You can't use the **CompilerOptions** and **ReferencedAssemblies** parameters in the same command.</span></span>

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

### <span data-ttu-id="230ec-186">-IgnoreWarnings</span><span class="sxs-lookup"><span data-stu-id="230ec-186">-IgnoreWarnings</span></span>

<span data-ttu-id="230ec-187">Ignore les avertissements du compilateur.</span><span class="sxs-lookup"><span data-stu-id="230ec-187">Ignores compiler warnings.</span></span> <span data-ttu-id="230ec-188">Utilisez ce paramètre pour empêcher `Add-Type` de gérer les avertissements du compilateur comme des erreurs.</span><span class="sxs-lookup"><span data-stu-id="230ec-188">Use this parameter to prevent `Add-Type` from handling compiler warnings as errors.</span></span>

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

### <span data-ttu-id="230ec-189">-Langage</span><span class="sxs-lookup"><span data-stu-id="230ec-189">-Language</span></span>

<span data-ttu-id="230ec-190">Spécifie la langue utilisée dans le code source.</span><span class="sxs-lookup"><span data-stu-id="230ec-190">Specifies the language that is used in the source code.</span></span> <span data-ttu-id="230ec-191">La valeur acceptable pour ce paramètre est **CSharp**.</span><span class="sxs-lookup"><span data-stu-id="230ec-191">The acceptable value for this parameter is **CSharp**.</span></span>

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

### <span data-ttu-id="230ec-192">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="230ec-192">-LiteralPath</span></span>

<span data-ttu-id="230ec-193">Spécifie le chemin d'accès aux fichiers de code source ou aux fichiers DLL d'assembly contenant les types.</span><span class="sxs-lookup"><span data-stu-id="230ec-193">Specifies the path to source code files or assembly DLL files that contain the types.</span></span> <span data-ttu-id="230ec-194">Contrairement à **path**, la valeur du paramètre **LiteralPath** est utilisée exactement telle qu’elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="230ec-194">Unlike **Path**, the value of the **LiteralPath** parameter is used exactly as it's typed.</span></span> <span data-ttu-id="230ec-195">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="230ec-195">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="230ec-196">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="230ec-196">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="230ec-197">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="230ec-197">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="230ec-198">-MemberDefinition</span><span class="sxs-lookup"><span data-stu-id="230ec-198">-MemberDefinition</span></span>

<span data-ttu-id="230ec-199">Spécifie les nouvelles propriétés ou méthodes de la classe.</span><span class="sxs-lookup"><span data-stu-id="230ec-199">Specifies new properties or methods for the class.</span></span> <span data-ttu-id="230ec-200">`Add-Type` génère le code de modèle qui est requis pour prendre en charge les propriétés ou les méthodes.</span><span class="sxs-lookup"><span data-stu-id="230ec-200">`Add-Type` generates the template code that is required to support the properties or methods.</span></span>

<span data-ttu-id="230ec-201">Sur Windows, vous pouvez utiliser cette fonctionnalité pour effectuer des appels d’appel de code non managé (P/Invoke) à des fonctions non managées dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="230ec-201">On Windows, you can use this feature to make Platform Invoke (P/Invoke) calls to unmanaged functions in PowerShell.</span></span>

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

### <span data-ttu-id="230ec-202">-Name</span><span class="sxs-lookup"><span data-stu-id="230ec-202">-Name</span></span>

<span data-ttu-id="230ec-203">Spécifie le nom de la classe à créer.</span><span class="sxs-lookup"><span data-stu-id="230ec-203">Specifies the name of the class to create.</span></span> <span data-ttu-id="230ec-204">Ce paramètre est obligatoire durant la génération d'un type à partir d'une définition de membre.</span><span class="sxs-lookup"><span data-stu-id="230ec-204">This parameter is required when generating a type from a member definition.</span></span>

<span data-ttu-id="230ec-205">Le nom de type et l'espace de noms doivent être uniques au sein d'une session.</span><span class="sxs-lookup"><span data-stu-id="230ec-205">The type name and namespace must be unique within a session.</span></span> <span data-ttu-id="230ec-206">Vous ne pouvez pas décharger un type ni le modifier.</span><span class="sxs-lookup"><span data-stu-id="230ec-206">You can't unload a type or change it.</span></span>
<span data-ttu-id="230ec-207">Pour modifier le code d’un type, vous devez modifier le nom ou démarrer une nouvelle session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="230ec-207">To change the code for a type, you must change the name or start a new PowerShell session.</span></span>
<span data-ttu-id="230ec-208">Sinon, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="230ec-208">Otherwise, the command fails.</span></span>

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

### <span data-ttu-id="230ec-209">-Espace de noms</span><span class="sxs-lookup"><span data-stu-id="230ec-209">-Namespace</span></span>

<span data-ttu-id="230ec-210">Spécifie un espace de noms pour le type.</span><span class="sxs-lookup"><span data-stu-id="230ec-210">Specifies a namespace for the type.</span></span>

<span data-ttu-id="230ec-211">Si ce paramètre n’est pas inclus dans la commande, le type est créé dans l’espace de noms **Microsoft. PowerShell. Commands. AddType. AutogeneratedTypes** .</span><span class="sxs-lookup"><span data-stu-id="230ec-211">If this parameter isn't included in the command, the type is created in the **Microsoft.PowerShell.Commands.AddType.AutoGeneratedTypes** namespace.</span></span> <span data-ttu-id="230ec-212">Si le paramètre est inclus dans la commande avec une valeur de chaîne vide ou une valeur de `$Null` , le type est généré dans l’espace de noms global.</span><span class="sxs-lookup"><span data-stu-id="230ec-212">If the parameter is included in the command with an empty string value or a value of `$Null`, the type is generated in the global namespace.</span></span>

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

### <span data-ttu-id="230ec-213">-OutputAssembly</span><span class="sxs-lookup"><span data-stu-id="230ec-213">-OutputAssembly</span></span>

<span data-ttu-id="230ec-214">Génère un fichier DLL pour l'assembly ayant le nom spécifié à l'emplacement approprié.</span><span class="sxs-lookup"><span data-stu-id="230ec-214">Generates a DLL file for the assembly with the specified name in the location.</span></span> <span data-ttu-id="230ec-215">Entrez un chemin d’accès et un nom de fichier facultatifs.</span><span class="sxs-lookup"><span data-stu-id="230ec-215">Enter an optional path and filename.</span></span> <span data-ttu-id="230ec-216">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="230ec-216">Wildcard characters are permitted.</span></span> <span data-ttu-id="230ec-217">Par défaut, `Add-Type` génère l’assembly uniquement en mémoire.</span><span class="sxs-lookup"><span data-stu-id="230ec-217">By default, `Add-Type` generates the assembly only in memory.</span></span>

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

### <span data-ttu-id="230ec-218">-OutputType</span><span class="sxs-lookup"><span data-stu-id="230ec-218">-OutputType</span></span>

<span data-ttu-id="230ec-219">Spécifie le type de sortie de l'assembly de sortie.</span><span class="sxs-lookup"><span data-stu-id="230ec-219">Specifies the output type of the output assembly.</span></span> <span data-ttu-id="230ec-220">Par défaut, aucun type de sortie n'est spécifié.</span><span class="sxs-lookup"><span data-stu-id="230ec-220">By default, no output type is specified.</span></span> <span data-ttu-id="230ec-221">Ce paramètre est valide uniquement quand un assembly de sortie est spécifié dans la commande.</span><span class="sxs-lookup"><span data-stu-id="230ec-221">This parameter is valid only when an output assembly is specified in the command.</span></span> <span data-ttu-id="230ec-222">Pour plus d’informations sur les valeurs, consultez [énumération OutputAssemblyType](/dotnet/api/microsoft.powershell.commands.outputassemblytype).</span><span class="sxs-lookup"><span data-stu-id="230ec-222">For more information about the values, see [OutputAssemblyType Enumeration](/dotnet/api/microsoft.powershell.commands.outputassemblytype).</span></span>

<span data-ttu-id="230ec-223">Les valeurs acceptables pour ce paramètre sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="230ec-223">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="230ec-224">ConsoleApplication</span><span class="sxs-lookup"><span data-stu-id="230ec-224">ConsoleApplication</span></span>
- <span data-ttu-id="230ec-225">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="230ec-225">Library</span></span>
- <span data-ttu-id="230ec-226">Fichier WindowsApplication</span><span class="sxs-lookup"><span data-stu-id="230ec-226">WindowsApplication</span></span>

> [!IMPORTANT]
> <span data-ttu-id="230ec-227">À partir de PowerShell 7,1, `ConsoleApplication` et ne `WindowsApplication` sont pas pris en charge et PowerShell lève une erreur de fin si l’un ou l’autre est spécifié en tant que valeurs pour le paramètre **OutputType** .</span><span class="sxs-lookup"><span data-stu-id="230ec-227">As of PowerShell 7.1, `ConsoleApplication` and `WindowsApplication` are not supported and PowerShell throws a terminating error if either are specified as values for the **OutputType** parameter.</span></span>

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

### <span data-ttu-id="230ec-228">-PassThru</span><span class="sxs-lookup"><span data-stu-id="230ec-228">-PassThru</span></span>

<span data-ttu-id="230ec-229">Retourne un objet **System.Runtime** qui représente les types ajoutés.</span><span class="sxs-lookup"><span data-stu-id="230ec-229">Returns a **System.Runtime** object that represents the types that were added.</span></span> <span data-ttu-id="230ec-230">Par défaut, cette applet de commande ne génère pas de sortie.</span><span class="sxs-lookup"><span data-stu-id="230ec-230">By default, this cmdlet doesn't generate any output.</span></span>

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

### <span data-ttu-id="230ec-231">-Path</span><span class="sxs-lookup"><span data-stu-id="230ec-231">-Path</span></span>

<span data-ttu-id="230ec-232">Spécifie le chemin d'accès aux fichiers de code source ou aux fichiers DLL d'assembly contenant les types.</span><span class="sxs-lookup"><span data-stu-id="230ec-232">Specifies the path to source code files or assembly DLL files that contain the types.</span></span>

<span data-ttu-id="230ec-233">Si vous envoyez des fichiers de code source, `Add-Type` compile le code dans les fichiers et crée un assembly en mémoire des types.</span><span class="sxs-lookup"><span data-stu-id="230ec-233">If you submit source code files, `Add-Type` compiles the code in the files and creates an in-memory assembly of the types.</span></span> <span data-ttu-id="230ec-234">L’extension de fichier spécifiée dans la valeur de **path** détermine le compilateur utilisé par `Add-Type` .</span><span class="sxs-lookup"><span data-stu-id="230ec-234">The file extension specified in the value of **Path** determines the compiler that `Add-Type` uses.</span></span>

<span data-ttu-id="230ec-235">Si vous envoyez un fichier d’assembly, `Add-Type` utilise les types de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="230ec-235">If you submit an assembly file, `Add-Type` takes the types from the assembly.</span></span> <span data-ttu-id="230ec-236">Pour spécifier un assembly en mémoire ou le Global Assembly Cache, utilisez le paramètre **AssemblyName**.</span><span class="sxs-lookup"><span data-stu-id="230ec-236">To specify an in-memory assembly or the global assembly cache, use the **AssemblyName** parameter.</span></span>

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

### <span data-ttu-id="230ec-237">-ReferencedAssemblies</span><span class="sxs-lookup"><span data-stu-id="230ec-237">-ReferencedAssemblies</span></span>

<span data-ttu-id="230ec-238">Spécifie les assemblys dont dépend le type.</span><span class="sxs-lookup"><span data-stu-id="230ec-238">Specifies the assemblies upon which the type depends.</span></span> <span data-ttu-id="230ec-239">Par défaut, `Add-Type` `System.dll` les références et `System.Management.Automation.dll` .</span><span class="sxs-lookup"><span data-stu-id="230ec-239">By default, `Add-Type` references `System.dll` and `System.Management.Automation.dll`.</span></span> <span data-ttu-id="230ec-240">Les assemblys que vous spécifiez à l'aide de ce paramètre sont référencés en plus des assemblys par défaut.</span><span class="sxs-lookup"><span data-stu-id="230ec-240">The assemblies that you specify by using this parameter are referenced in addition to the default assemblies.</span></span>

<span data-ttu-id="230ec-241">À compter de PowerShell 6, **ReferencedAssemblies** n’inclut pas les assemblys .NET par défaut.</span><span class="sxs-lookup"><span data-stu-id="230ec-241">Beginning in PowerShell 6, **ReferencedAssemblies** doesn't include the default .NET assemblies.</span></span> <span data-ttu-id="230ec-242">Vous devez inclure une référence spécifique à celles-ci dans la valeur transmise à ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="230ec-242">You must include a specific reference to them in the value passed to this parameter.</span></span>

<span data-ttu-id="230ec-243">Vous ne pouvez pas utiliser les paramètres **CompilerOptions** et **ReferencedAssemblies** dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="230ec-243">You can't use the **CompilerOptions** and **ReferencedAssemblies** parameters in the same command.</span></span>

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

### <span data-ttu-id="230ec-244">-TypeDefinition</span><span class="sxs-lookup"><span data-stu-id="230ec-244">-TypeDefinition</span></span>

<span data-ttu-id="230ec-245">Spécifie le code source qui contient les définitions de type.</span><span class="sxs-lookup"><span data-stu-id="230ec-245">Specifies the source code that contains the type definitions.</span></span> <span data-ttu-id="230ec-246">Entrez le code source dans une chaîne ou une chaîne here-string, ou entrez une variable qui contient le code source.</span><span class="sxs-lookup"><span data-stu-id="230ec-246">Enter the source code in a string or here-string, or enter a variable that contains the source code.</span></span> <span data-ttu-id="230ec-247">Pour plus d’informations sur les chaînes ici, consultez [about_Quoting_Rules](../Microsoft.PowerShell.Core/about/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="230ec-247">For more information about here-strings, see [about_Quoting_Rules](../Microsoft.PowerShell.Core/about/about_Quoting_Rules.md).</span></span>

<span data-ttu-id="230ec-248">Incluez une déclaration d'espace de noms dans votre définition de type.</span><span class="sxs-lookup"><span data-stu-id="230ec-248">Include a namespace declaration in your type definition.</span></span> <span data-ttu-id="230ec-249">Si vous omettez la déclaration d'espace de noms, votre type risque d'avoir le même nom qu'un autre type ou que le raccourci d'un autre type, ce qui entraînera un remplacement involontaire.</span><span class="sxs-lookup"><span data-stu-id="230ec-249">If you omit the namespace declaration, your type might have the same name as another type or the shortcut for another type, causing an unintentional overwrite.</span></span> <span data-ttu-id="230ec-250">Par exemple, si vous définissez un type appelé **exception**, les scripts qui utilisent une **exception** comme raccourci pour **System. exception** échoueront.</span><span class="sxs-lookup"><span data-stu-id="230ec-250">For example, if you define a type called **Exception**, scripts that use **Exception** as the shortcut for **System.Exception** will fail.</span></span>

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

### <span data-ttu-id="230ec-251">-UsingNamespace</span><span class="sxs-lookup"><span data-stu-id="230ec-251">-UsingNamespace</span></span>

<span data-ttu-id="230ec-252">Spécifie les autres espaces de noms nécessaires pour la classe.</span><span class="sxs-lookup"><span data-stu-id="230ec-252">Specifies other namespaces that are required for the class.</span></span> <span data-ttu-id="230ec-253">C’est très similaire au mot clé C#, `Using` .</span><span class="sxs-lookup"><span data-stu-id="230ec-253">This is much like the C# keyword, `Using`.</span></span>

<span data-ttu-id="230ec-254">Par défaut, `Add-Type` fait référence à l’espace de noms **System** .</span><span class="sxs-lookup"><span data-stu-id="230ec-254">By default, `Add-Type` references the **System** namespace.</span></span> <span data-ttu-id="230ec-255">Lorsque le paramètre **MemberDefinition** est utilisé, `Add-Type` fait également référence à l’espace de noms **System. Runtime. InteropServices** par défaut.</span><span class="sxs-lookup"><span data-stu-id="230ec-255">When the **MemberDefinition** parameter is used, `Add-Type` also references the **System.Runtime.InteropServices** namespace by default.</span></span> <span data-ttu-id="230ec-256">Les espaces de noms que vous ajoutez à l'aide du paramètre **UsingNamespace** sont référencés en plus des espaces de noms par défaut.</span><span class="sxs-lookup"><span data-stu-id="230ec-256">The namespaces that you add by using the **UsingNamespace** parameter are referenced in addition to the default namespaces.</span></span>

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

### <span data-ttu-id="230ec-257">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="230ec-257">CommonParameters</span></span>

<span data-ttu-id="230ec-258">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="230ec-258">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="230ec-259">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="230ec-259">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="230ec-260">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="230ec-260">INPUTS</span></span>

### <span data-ttu-id="230ec-261">None</span><span class="sxs-lookup"><span data-stu-id="230ec-261">None</span></span>

<span data-ttu-id="230ec-262">Vous ne pouvez pas envoyer d’objets dans le pipeline vers `Add-Type` .</span><span class="sxs-lookup"><span data-stu-id="230ec-262">You can't send objects down the pipeline to `Add-Type`.</span></span>

## <span data-ttu-id="230ec-263">SORTIES</span><span class="sxs-lookup"><span data-stu-id="230ec-263">OUTPUTS</span></span>

### <span data-ttu-id="230ec-264">None ou System. type</span><span class="sxs-lookup"><span data-stu-id="230ec-264">None or System.Type</span></span>

<span data-ttu-id="230ec-265">Quand vous utilisez le paramètre **PassThru** , `Add-Type` retourne un objet **System. type** qui représente le nouveau type.</span><span class="sxs-lookup"><span data-stu-id="230ec-265">When you use the **PassThru** parameter, `Add-Type` returns a **System.Type** object that represents the new type.</span></span> <span data-ttu-id="230ec-266">Sinon, cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="230ec-266">Otherwise, this cmdlet doesn't generate any output.</span></span>

## <span data-ttu-id="230ec-267">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="230ec-267">NOTES</span></span>

<span data-ttu-id="230ec-268">Les types que vous ajoutez existent uniquement dans la session active.</span><span class="sxs-lookup"><span data-stu-id="230ec-268">The types that you add exist only in the current session.</span></span> <span data-ttu-id="230ec-269">Pour utiliser les types dans toutes les sessions, ajoutez-les à votre profil PowerShell.</span><span class="sxs-lookup"><span data-stu-id="230ec-269">To use the types in all sessions, add them to your PowerShell profile.</span></span> <span data-ttu-id="230ec-270">Pour plus d’informations sur le profil, consultez [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span><span class="sxs-lookup"><span data-stu-id="230ec-270">For more information about the profile, see [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span></span>

<span data-ttu-id="230ec-271">Les noms de types et les espaces de noms doivent être uniques au sein d’une session.</span><span class="sxs-lookup"><span data-stu-id="230ec-271">Type names and namespaces must be unique within a session.</span></span> <span data-ttu-id="230ec-272">Vous ne pouvez pas décharger un type ni le modifier.</span><span class="sxs-lookup"><span data-stu-id="230ec-272">You can't unload a type or change it.</span></span> <span data-ttu-id="230ec-273">Si vous avez besoin de modifier le code d’un type, vous devez modifier le nom ou démarrer une nouvelle session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="230ec-273">If you need to change the code for a type, you must change the name or start a new PowerShell session.</span></span>
<span data-ttu-id="230ec-274">Sinon, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="230ec-274">Otherwise, the command fails.</span></span>

<span data-ttu-id="230ec-275">Dans Windows PowerShell (version 5,1 et versions antérieures), vous devez utiliser `Add-Type` pour tout ce qui n’est pas déjà chargé.</span><span class="sxs-lookup"><span data-stu-id="230ec-275">In Windows PowerShell (version 5.1 and below), you need to use `Add-Type` for anything that isn't already loaded.</span></span> <span data-ttu-id="230ec-276">En règle générale, cela s’applique aux assemblys figurant dans le global assembly cache (GAC).</span><span class="sxs-lookup"><span data-stu-id="230ec-276">Most commonly, this applies to assemblies found in the Global Assembly Cache (GAC).</span></span>
<span data-ttu-id="230ec-277">Dans PowerShell 6 et versions ultérieures, il n’y a aucun GAC, de sorte que PowerShell installe ses propres assemblys dans `$PSHome` .</span><span class="sxs-lookup"><span data-stu-id="230ec-277">In PowerShell 6 and higher, there is no GAC, so PowerShell installs its own assemblies in `$PSHome`.</span></span>
<span data-ttu-id="230ec-278">Ces assemblys sont automatiquement chargés à la demande. il n’est donc pas nécessaire d’utiliser `Add-Type` pour les charger.</span><span class="sxs-lookup"><span data-stu-id="230ec-278">These assemblies are automatically loaded on request, so there's no need to use `Add-Type` to load them.</span></span> <span data-ttu-id="230ec-279">Toutefois, l’utilisation de `Add-Type` est toujours autorisée pour permettre aux scripts d’être implicitement compatibles avec n’importe quelle version de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="230ec-279">However, using `Add-Type` is still permitted to allow scripts to be implicitly compatible with any version of PowerShell.</span></span>

<span data-ttu-id="230ec-280">Les assemblys dans le GAC peuvent être chargés par nom de type, plutôt que par chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="230ec-280">Assemblies in the GAC can be loaded by type name, rather than by path.</span></span> <span data-ttu-id="230ec-281">Le chargement d’assemblys à partir d’un chemin d’accès arbitraire requiert `Add-Type` , car ces assemblys ne peuvent pas être chargés automatiquement.</span><span class="sxs-lookup"><span data-stu-id="230ec-281">Loading assemblies from an arbitrary path requires `Add-Type`, since those assemblies cannot not be loaded automatically.</span></span>

## <span data-ttu-id="230ec-282">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="230ec-282">RELATED LINKS</span></span>

[<span data-ttu-id="230ec-283">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="230ec-283">about_Profiles</span></span>](../Microsoft.PowerShell.Core/About/about_profiles.md)

[<span data-ttu-id="230ec-284">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="230ec-284">about_Quoting_Rules</span></span>](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md)

[<span data-ttu-id="230ec-285">Add-Member</span><span class="sxs-lookup"><span data-stu-id="230ec-285">Add-Member</span></span>](Add-Member.md)

[<span data-ttu-id="230ec-286">New-Object</span><span class="sxs-lookup"><span data-stu-id="230ec-286">New-Object</span></span>](New-Object.md)

[<span data-ttu-id="230ec-287">OutputAssemblyType</span><span class="sxs-lookup"><span data-stu-id="230ec-287">OutputAssemblyType</span></span>](/dotnet/api/microsoft.powershell.commands.outputassemblytype)

[<span data-ttu-id="230ec-288">Appel de code non managé (P/Invoke)</span><span class="sxs-lookup"><span data-stu-id="230ec-288">Platform Invoke (P/Invoke)</span></span>](/dotnet/standard/native-interop/pinvoke)

[<span data-ttu-id="230ec-289">Where-Object</span><span class="sxs-lookup"><span data-stu-id="230ec-289">Where-Object</span></span>](../Microsoft.PowerShell.Core/Where-Object.md)
