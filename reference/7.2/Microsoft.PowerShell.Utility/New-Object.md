---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-object?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Object
ms.openlocfilehash: 3b2db400c5a8a1c61ec30ecee07f91d29b5eb3c1
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597786"
---
# <span data-ttu-id="3414f-102">New-Object</span><span class="sxs-lookup"><span data-stu-id="3414f-102">New-Object</span></span>

## <span data-ttu-id="3414f-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="3414f-103">SYNOPSIS</span></span>
<span data-ttu-id="3414f-104">Crée une instance d'un objet Microsoft .NET Framework ou COM.</span><span class="sxs-lookup"><span data-stu-id="3414f-104">Creates an instance of a Microsoft .NET Framework or COM object.</span></span>

## <span data-ttu-id="3414f-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="3414f-105">SYNTAX</span></span>

### <span data-ttu-id="3414f-106">NET (par défaut)</span><span class="sxs-lookup"><span data-stu-id="3414f-106">Net (Default)</span></span>

```
New-Object [-TypeName] <String> [[-ArgumentList] <Object[]>] [-Property <IDictionary>] [<CommonParameters>]
```

### <span data-ttu-id="3414f-107">Com</span><span class="sxs-lookup"><span data-stu-id="3414f-107">Com</span></span>

```
New-Object [-ComObject] <String> [-Strict] [-Property <IDictionary>] [<CommonParameters>]
```

## <span data-ttu-id="3414f-108">Description</span><span class="sxs-lookup"><span data-stu-id="3414f-108">DESCRIPTION</span></span>

<span data-ttu-id="3414f-109">L' `New-Object` applet de commande crée une instance d’un .NET Framework ou d’un objet com.</span><span class="sxs-lookup"><span data-stu-id="3414f-109">The `New-Object` cmdlet creates an instance of a .NET Framework or COM object.</span></span>

<span data-ttu-id="3414f-110">Vous pouvez spécifier le type d'une classe .NET Framework ou un ProgID d'un objet COM.</span><span class="sxs-lookup"><span data-stu-id="3414f-110">You can specify either the type of a .NET Framework class or a ProgID of a COM object.</span></span> <span data-ttu-id="3414f-111">Par défaut, vous tapez le nom complet d'une classe .NET Framework et l'applet de commande retourne une référence à une instance de cette classe.</span><span class="sxs-lookup"><span data-stu-id="3414f-111">By default, you type the fully qualified name of a .NET Framework class and the cmdlet returns a reference to an instance of that class.</span></span> <span data-ttu-id="3414f-112">Pour créer une instance d’un objet COM, utilisez le paramètre **ComObject** et spécifiez le ProgID de l’objet comme valeur.</span><span class="sxs-lookup"><span data-stu-id="3414f-112">To create an instance of a COM object, use the **ComObject** parameter and specify the ProgID of the object as its value.</span></span>

## <span data-ttu-id="3414f-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="3414f-113">EXAMPLES</span></span>

### <span data-ttu-id="3414f-114">Exemple 1 : créer un objet System. version</span><span class="sxs-lookup"><span data-stu-id="3414f-114">Example 1: Create a System.Version object</span></span>

<span data-ttu-id="3414f-115">Cet exemple crée un objet **System. version** à l’aide de la chaîne « 1.2.3.4 » comme constructeur.</span><span class="sxs-lookup"><span data-stu-id="3414f-115">This example creates a **System.Version** object using the "1.2.3.4" string as the constructor.</span></span>

```powershell
New-Object -TypeName System.Version -ArgumentList "1.2.3.4"
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
1      2      3      4
```

### <span data-ttu-id="3414f-116">Exemple 2 : créer un objet COM Internet Explorer</span><span class="sxs-lookup"><span data-stu-id="3414f-116">Example 2: Create an Internet Explorer COM object</span></span>

<span data-ttu-id="3414f-117">Cet exemple crée deux instances de l’objet COM qui représente l’application Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="3414f-117">This example creates two instances of the COM object that represents the Internet Explorer application.</span></span> <span data-ttu-id="3414f-118">La première instance utilise la table de hachage des paramètres de **propriété** pour appeler la méthode **Navigate2** et définir la propriété **visible** de l’objet sur `$True` pour rendre l’application visible.</span><span class="sxs-lookup"><span data-stu-id="3414f-118">The first instance uses the **Property** parameter hash table to call the **Navigate2** method and set the **Visible** property of the object to `$True` to make the application visible.</span></span>
<span data-ttu-id="3414f-119">La deuxième instance obtient les mêmes résultats avec des commandes individuelles.</span><span class="sxs-lookup"><span data-stu-id="3414f-119">The second instance gets the same results with individual commands.</span></span>

```powershell
$IE1 = New-Object -COMObject InternetExplorer.Application -Property @{Navigate2="www.microsoft.com"; Visible = $True}

# The following command gets the same results as the example above.
$IE2 = New-Object -COMObject InternetExplorer.Application`
$IE2.Navigate2("www.microsoft.com")`
$IE2.Visible = $True`
```

### <span data-ttu-id="3414f-120">Exemple 3 : utiliser le paramètre strict pour générer une erreur sans fin d’achèvement</span><span class="sxs-lookup"><span data-stu-id="3414f-120">Example 3: Use the Strict parameter to generate a non-terminating error</span></span>

<span data-ttu-id="3414f-121">Cet exemple montre que l’ajout du paramètre **strict** fait que l' `New-Object` applet de commande génère une erreur sans fin d’achèvement lorsque l’objet com utilise un assembly d’interopérabilité.</span><span class="sxs-lookup"><span data-stu-id="3414f-121">This example demonstrates that adding the **Strict** parameter causes the `New-Object` cmdlet to generate a non-terminating error when the COM object uses an interop assembly.</span></span>

```powershell
$A = New-Object -COMObject Word.Application -Strict -Property @{Visible = $True}
```

```Output
New-Object : The object written to the pipeline is an instance of the type
"Microsoft.Office.Interop.Word.ApplicationClass" from the component's primary interop assembly. If
this type exposes different members than the IDispatch members, scripts written to work with this
object might not work if the primary interop assembly is not installed.

At line:1 char:14
+ $A = New-Object  <<<< -COM Word.Application -Strict; $a.visible=$true
```

### <span data-ttu-id="3414f-122">Exemple 4 : créer un objet COM pour gérer le bureau Windows</span><span class="sxs-lookup"><span data-stu-id="3414f-122">Example 4: Create a COM object to manage Windows desktop</span></span>

<span data-ttu-id="3414f-123">Cet exemple illustre comment créer et utiliser un objet COM pour gérer votre Bureau Windows.</span><span class="sxs-lookup"><span data-stu-id="3414f-123">This example shows how to create and use a COM object to manage your Windows desktop.</span></span>

<span data-ttu-id="3414f-124">La première commande utilise le paramètre **ComObject** de l' `New-Object` applet de commande pour créer un objet com avec le ProgID **Shell. application** .</span><span class="sxs-lookup"><span data-stu-id="3414f-124">The first command uses the **ComObject** parameter of the `New-Object` cmdlet to create a COM object with the **Shell.Application** ProgID.</span></span> <span data-ttu-id="3414f-125">Elle stocke l’objet résultant dans la `$ObjShell` variable.</span><span class="sxs-lookup"><span data-stu-id="3414f-125">It stores the resulting object in the `$ObjShell` variable.</span></span> <span data-ttu-id="3414f-126">La deuxième commande dirige la `$ObjShell` variable vers l' `Get-Member` applet de commande, qui affiche les propriétés et les méthodes de l’objet com.</span><span class="sxs-lookup"><span data-stu-id="3414f-126">The second command pipes the `$ObjShell` variable to the `Get-Member` cmdlet, which displays the properties and methods of the COM object.</span></span> <span data-ttu-id="3414f-127">Parmi les méthodes, citons la méthode **ToggleDesktop** .</span><span class="sxs-lookup"><span data-stu-id="3414f-127">Among the methods is the **ToggleDesktop** method.</span></span> <span data-ttu-id="3414f-128">La troisième commande appelle la méthode **ToggleDesktop** de l'objet pour réduire les fenêtres ouvertes sur votre Bureau.</span><span class="sxs-lookup"><span data-stu-id="3414f-128">The third command calls the **ToggleDesktop** method of the object to minimize the open windows on your desktop.</span></span>

```powershell
$Objshell = New-Object -COMObject "Shell.Application"
$objshell | Get-Member
$objshell.ToggleDesktop()
```

```Output
   TypeName: System.__ComObject#{866738b9-6cf2-4de8-8767-f794ebe74f4e}

Name                 MemberType Definition
----                 ---------- ----------
AddToRecent          Method     void AddToRecent (Variant, string)
BrowseForFolder      Method     Folder BrowseForFolder (int, string, int, Variant)
CanStartStopService  Method     Variant CanStartStopService (string)
CascadeWindows       Method     void CascadeWindows ()
ControlPanelItem     Method     void ControlPanelItem (string)
EjectPC              Method     void EjectPC ()
Explore              Method     void Explore (Variant)
ExplorerPolicy       Method     Variant ExplorerPolicy (string)
FileRun              Method     void FileRun ()
FindComputer         Method     void FindComputer ()
FindFiles            Method     void FindFiles ()
FindPrinter          Method     void FindPrinter (string, string, string)
GetSetting           Method     bool GetSetting (int)
GetSystemInformation Method     Variant GetSystemInformation (string)
Help                 Method     void Help ()
IsRestricted         Method     int IsRestricted (string, string)
IsServiceRunning     Method     Variant IsServiceRunning (string)
MinimizeAll          Method     void MinimizeAll ()
NameSpace            Method     Folder NameSpace (Variant)
Open                 Method     void Open (Variant)
RefreshMenu          Method     void RefreshMenu ()
ServiceStart         Method     Variant ServiceStart (string, Variant)
ServiceStop          Method     Variant ServiceStop (string, Variant)
SetTime              Method     void SetTime ()
ShellExecute         Method     void ShellExecute (string, Variant, Variant, Variant, Variant)
ShowBrowserBar       Method     Variant ShowBrowserBar (string, Variant)
ShutdownWindows      Method     void ShutdownWindows ()
Suspend              Method     void Suspend ()
TileHorizontally     Method     void TileHorizontally ()
TileVertically       Method     void TileVertically ()
ToggleDesktop        Method     void ToggleDesktop ()
TrayProperties       Method     void TrayProperties ()
UndoMinimizeALL      Method     void UndoMinimizeALL ()
Windows              Method     IDispatch Windows ()
WindowsSecurity      Method     void WindowsSecurity ()
WindowSwitcher       Method     void WindowSwitcher ()
Application          Property   IDispatch Application () {get}
Parent               Property   IDispatch Parent () {get}
```

### <span data-ttu-id="3414f-129">Exemple 5 : passer plusieurs arguments à un constructeur</span><span class="sxs-lookup"><span data-stu-id="3414f-129">Example 5: Pass multiple arguments to a constructor</span></span>

<span data-ttu-id="3414f-130">Cet exemple montre comment créer un objet avec un constructeur qui accepte plusieurs paramètres.</span><span class="sxs-lookup"><span data-stu-id="3414f-130">This example shows how to create an object with a constructor that takes multiple parameters.</span></span> <span data-ttu-id="3414f-131">Les paramètres doivent être placés dans un tableau lors de l’utilisation du paramètre **argumentlist** .</span><span class="sxs-lookup"><span data-stu-id="3414f-131">The parameters must be put in an array when using **ArgumentList** parameter.</span></span>

```powershell
$array = @('One', 'Two', 'Three')
$parameters = @{
    TypeName = 'System.Collections.Generic.HashSet[string]'
    ArgumentList = ([string[]]$array, [System.StringComparer]::OrdinalIgnoreCase)
}
$set = New-Object @parameters
```

<span data-ttu-id="3414f-132">PowerShell lie chaque membre du tableau à un paramètre du constructeur.</span><span class="sxs-lookup"><span data-stu-id="3414f-132">PowerShell binds each member of the array to a parameter of the constructor.</span></span>

> [!NOTE]
> <span data-ttu-id="3414f-133">Cet exemple utilise la projection de paramètres pour une meilleure lisibilité.</span><span class="sxs-lookup"><span data-stu-id="3414f-133">This example uses parameter splatting for readability.</span></span> <span data-ttu-id="3414f-134">Pour plus d’informations, consultez [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).</span><span class="sxs-lookup"><span data-stu-id="3414f-134">For more information, see [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).</span></span>

### <span data-ttu-id="3414f-135">Exemple 6 : appel d’un constructeur qui accepte un tableau en tant que paramètre unique</span><span class="sxs-lookup"><span data-stu-id="3414f-135">Example 6: Calling a constructor that takes an array as a single parameter</span></span>

<span data-ttu-id="3414f-136">Cet exemple montre comment créer un objet avec un constructeur qui accepte un paramètre qui est un tableau ou une collection.</span><span class="sxs-lookup"><span data-stu-id="3414f-136">This example shows how to create an object with a constructor that takes a parameter that is an array or collection.</span></span> <span data-ttu-id="3414f-137">Le paramètre de tableau doit être placé dans un wrapper à l’intérieur d’un autre tableau.</span><span class="sxs-lookup"><span data-stu-id="3414f-137">The array parameter must be put in wrapped inside another array.</span></span>

```powershell
$array = @('One', 'Two', 'Three')
# This command throws an exception.
$set = New-Object -TypeName 'System.Collections.Generic.HashSet[string]' -ArgumentList $array
# This command succeeds.
$set = New-Object -TypeName 'System.Collections.Generic.HashSet[string]' -ArgumentList (,[string[]]$array)
$set
```

```Output
New-Object : Cannot find an overload for "HashSet`1" and the argument count: "3".
At line:1 char:8
+ $set = New-Object -TypeName 'System.Collections.Generic.HashSet[strin ...
+        ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : InvalidOperation: (:) [New-Object], MethodException
+ FullyQualifiedErrorId : ConstructorInvokedThrowException,Microsoft.PowerShell.Commands.NewObjectCommand

One
Two
Three
```

<span data-ttu-id="3414f-138">La première tentative de création de l’objet dans cet exemple échoue.</span><span class="sxs-lookup"><span data-stu-id="3414f-138">The first attempt to create the object in this example fails.</span></span> <span data-ttu-id="3414f-139">PowerShell a tenté de lier les trois membres de `$array` aux paramètres du constructeur, mais le constructeur ne prend pas trois paramètres.</span><span class="sxs-lookup"><span data-stu-id="3414f-139">PowerShell attempted to bind the three members of `$array` to parameters of the constructor but the constructor does not take three parameter.</span></span> <span data-ttu-id="3414f-140">L’encapsulation `$array` dans un autre tableau empêche PowerShell de tenter de lier les trois membres de `$array` aux paramètres du constructeur.</span><span class="sxs-lookup"><span data-stu-id="3414f-140">Wrapping `$array` in another array prevents PowerShell from attempting to bind the three members of `$array` to parameters of the constructor.</span></span>

## <span data-ttu-id="3414f-141">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3414f-141">PARAMETERS</span></span>

### <span data-ttu-id="3414f-142">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="3414f-142">-ArgumentList</span></span>

<span data-ttu-id="3414f-143">Spécifie un tableau d’arguments à passer au constructeur de la classe .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3414f-143">Specifies an array of arguments to pass to the constructor of the .NET Framework class.</span></span> <span data-ttu-id="3414f-144">Si le constructeur accepte un seul paramètre qui est un tableau, vous devez encapsuler ce paramètre à l’intérieur d’un autre tableau.</span><span class="sxs-lookup"><span data-stu-id="3414f-144">If the constructor takes a single parameter that is an array, you must wrap that parameter inside another array.</span></span> <span data-ttu-id="3414f-145">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="3414f-145">For example:</span></span>

`$cert = New-Object System.Security.Cryptography.X509Certificates.X509Certificate -ArgumentList (,$bytes)`

<span data-ttu-id="3414f-146">Pour plus d’informations sur le comportement de **argumentlist**, consultez [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md#splatting-with-arrays).</span><span class="sxs-lookup"><span data-stu-id="3414f-146">For more information about the behavior of **ArgumentList**, see [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md#splatting-with-arrays).</span></span>

<span data-ttu-id="3414f-147">L'alias d'**ArgumentList** est **Args**.</span><span class="sxs-lookup"><span data-stu-id="3414f-147">The alias for **ArgumentList** is **Args**.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: Net
Aliases: Args

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3414f-148">-ComObject</span><span class="sxs-lookup"><span data-stu-id="3414f-148">-ComObject</span></span>

<span data-ttu-id="3414f-149">Spécifie l'identificateur programmatique (ProgID) de l'objet COM.</span><span class="sxs-lookup"><span data-stu-id="3414f-149">Specifies the programmatic identifier (ProgID) of the COM object.</span></span>

```yaml
Type: System.String
Parameter Sets: Com
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3414f-150">-Propriété</span><span class="sxs-lookup"><span data-stu-id="3414f-150">-Property</span></span>

<span data-ttu-id="3414f-151">Définit les valeurs de propriété et appelle les méthodes du nouvel objet.</span><span class="sxs-lookup"><span data-stu-id="3414f-151">Sets property values and invokes methods of the new object.</span></span>

<span data-ttu-id="3414f-152">Entrez une table de hachage dans laquelle les clés sont les noms des propriétés ou des méthodes, et les valeurs sont des valeurs de propriété ou des arguments de méthode.</span><span class="sxs-lookup"><span data-stu-id="3414f-152">Enter a hash table in which the keys are the names of properties or methods and the values are property values or method arguments.</span></span> <span data-ttu-id="3414f-153">`New-Object` crée l’objet et définit chaque valeur de propriété et appelle chaque méthode dans l’ordre dans lequel elles apparaissent dans la table de hachage.</span><span class="sxs-lookup"><span data-stu-id="3414f-153">`New-Object` creates the object and sets each property value and invokes each method in the order that they appear in the hash table.</span></span>

<span data-ttu-id="3414f-154">Si le nouvel objet est dérivé de la classe **PSObject** et que vous spécifiez une propriété qui n’existe pas sur l’objet, `New-Object` ajoute la propriété spécifiée à l’objet en tant que NoteProperty.</span><span class="sxs-lookup"><span data-stu-id="3414f-154">If the new object is derived from the **PSObject** class, and you specify a property that does not exist on the object, `New-Object` adds the specified property to the object as a NoteProperty.</span></span> <span data-ttu-id="3414f-155">Si l’objet n’est pas un **PSObject**, la commande génère une erreur sans fin d’achèvement.</span><span class="sxs-lookup"><span data-stu-id="3414f-155">If the object is not a **PSObject**, the command generates a non-terminating error.</span></span>

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3414f-156">-Strict</span><span class="sxs-lookup"><span data-stu-id="3414f-156">-Strict</span></span>

<span data-ttu-id="3414f-157">Indique que l’applet de commande génère une erreur sans fin d’achèvement lorsqu’un objet COM que vous tentez de créer utilise un assembly d’interopérabilité.</span><span class="sxs-lookup"><span data-stu-id="3414f-157">Indicates that the cmdlet generates a non-terminating error when a COM object that you attempt to create uses an interop assembly.</span></span> <span data-ttu-id="3414f-158">Cette fonctionnalité distingue les objets COM réels des objets .NET Framework avec des wrappers CCW (COM-callable wrapper).</span><span class="sxs-lookup"><span data-stu-id="3414f-158">This feature distinguishes actual COM objects from .NET Framework objects with COM-callable wrappers.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Com
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3414f-159">-TypeName</span><span class="sxs-lookup"><span data-stu-id="3414f-159">-TypeName</span></span>

<span data-ttu-id="3414f-160">Spécifie le nom complet de la classe .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3414f-160">Specifies the fully qualified name of the .NET Framework class.</span></span> <span data-ttu-id="3414f-161">Vous ne pouvez pas spécifier à la fois le paramètre **TypeName** et le paramètre **ComObject** .</span><span class="sxs-lookup"><span data-stu-id="3414f-161">You cannot specify both the **TypeName** parameter and the **ComObject** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: Net
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3414f-162">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3414f-162">CommonParameters</span></span>

<span data-ttu-id="3414f-163">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3414f-163">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3414f-164">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="3414f-164">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3414f-165">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="3414f-165">INPUTS</span></span>

### <span data-ttu-id="3414f-166">None</span><span class="sxs-lookup"><span data-stu-id="3414f-166">None</span></span>

<span data-ttu-id="3414f-167">Vous ne pouvez pas diriger d'entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="3414f-167">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="3414f-168">SORTIES</span><span class="sxs-lookup"><span data-stu-id="3414f-168">OUTPUTS</span></span>

### <span data-ttu-id="3414f-169">Object</span><span class="sxs-lookup"><span data-stu-id="3414f-169">Object</span></span>

<span data-ttu-id="3414f-170">`New-Object` retourne l’objet créé.</span><span class="sxs-lookup"><span data-stu-id="3414f-170">`New-Object` returns the object that is created.</span></span>

## <span data-ttu-id="3414f-171">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="3414f-171">NOTES</span></span>

- <span data-ttu-id="3414f-172">`New-Object` fournit les fonctionnalités les plus couramment utilisées de la fonction VBScript CreateObject.</span><span class="sxs-lookup"><span data-stu-id="3414f-172">`New-Object` provides the most commonly-used functionality of the VBScript CreateObject function.</span></span> <span data-ttu-id="3414f-173">Une instruction comme `Set objShell = CreateObject("Shell.Application")` dans VBScript peut être traduite en `$objShell = New-Object -COMObject "Shell.Application"` PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3414f-173">A statement like `Set objShell = CreateObject("Shell.Application")` in VBScript can be translated to `$objShell = New-Object -COMObject "Shell.Application"` in PowerShell.</span></span>
- <span data-ttu-id="3414f-174">`New-Object` développe les fonctionnalités disponibles dans l’environnement d’exécution de scripts Windows en facilitant l’utilisation des objets .NET Framework à partir de la ligne de commande et dans les scripts.</span><span class="sxs-lookup"><span data-stu-id="3414f-174">`New-Object` expands upon the functionality available in the Windows Script Host environment by making it easy to work with .NET Framework objects from the command line and within scripts.</span></span>

## <span data-ttu-id="3414f-175">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="3414f-175">RELATED LINKS</span></span>

[<span data-ttu-id="3414f-176">about_Object_Creation</span><span class="sxs-lookup"><span data-stu-id="3414f-176">about_Object_Creation</span></span>](../Microsoft.PowerShell.Core/About/about_Object_Creation.md)

[<span data-ttu-id="3414f-177">Compare-Object</span><span class="sxs-lookup"><span data-stu-id="3414f-177">Compare-Object</span></span>](Compare-Object.md)

[<span data-ttu-id="3414f-178">Group-Object</span><span class="sxs-lookup"><span data-stu-id="3414f-178">Group-Object</span></span>](Group-Object.md)

[<span data-ttu-id="3414f-179">Measure-Object</span><span class="sxs-lookup"><span data-stu-id="3414f-179">Measure-Object</span></span>](Measure-Object.md)

[<span data-ttu-id="3414f-180">Select-Object</span><span class="sxs-lookup"><span data-stu-id="3414f-180">Select-Object</span></span>](Select-Object.md)

[<span data-ttu-id="3414f-181">Sort-Object</span><span class="sxs-lookup"><span data-stu-id="3414f-181">Sort-Object</span></span>](Sort-Object.md)

[<span data-ttu-id="3414f-182">Tee-Object</span><span class="sxs-lookup"><span data-stu-id="3414f-182">Tee-Object</span></span>](Tee-Object.md)

