---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Utilisation de classes et méthodes statiques
description: Cet article explique comment identifier et utiliser les propriétés et les méthodes des classes statiques .NET.
ms.openlocfilehash: 2e83fe442f7b3fdf62ceaab587450251ac4e7958
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2020
ms.locfileid: "92501250"
---
# <a name="using-static-classes-and-methods"></a><span data-ttu-id="49ca6-104">Utilisation de classes et méthodes statiques</span><span class="sxs-lookup"><span data-stu-id="49ca6-104">Using Static Classes and Methods</span></span>

<span data-ttu-id="49ca6-105">Certaines classes de .NET Framework ne peuvent pas être créées à l’aide de l’applet de commande **New-Object** .</span><span class="sxs-lookup"><span data-stu-id="49ca6-105">Not all .NET Framework classes can be created by using **New-Object** .</span></span> <span data-ttu-id="49ca6-106">Par exemple, si vous essayez de créer un objet **System.Environment** ou **System.Math** avec l’applet de commande **New-Object** , vous obtenez les messages d’erreur suivants :</span><span class="sxs-lookup"><span data-stu-id="49ca6-106">For example, if you try to create a **System.Environment** or a **System.Math** object with **New-Object** , you will get the following error messages:</span></span>

```
PS> New-Object System.Environment
New-Object : Constructor not found. Cannot find an appropriate constructor for
type System.Environment.
At line:1 char:11
+ New-Object  <<<< System.Environment

PS> New-Object System.Math
New-Object : Constructor not found. Cannot find an appropriate constructor for
type System.Math.
At line:1 char:11
+ New-Object  <<<< System.Math
```

<span data-ttu-id="49ca6-107">Ces erreurs se produisent parce qu’il n’existe aucun moyen de créer un objet à partir de ces classes.</span><span class="sxs-lookup"><span data-stu-id="49ca6-107">These errors occur because there is no way to create a new object from these classes.</span></span> <span data-ttu-id="49ca6-108">Ces classes sont des bibliothèques de référence de méthodes et propriétés qui ne changent pas d’état.</span><span class="sxs-lookup"><span data-stu-id="49ca6-108">These classes are reference libraries of methods and properties that do not change state.</span></span> <span data-ttu-id="49ca6-109">Vous n’avez pas besoin de les créer. Vous les utilisez simplement.</span><span class="sxs-lookup"><span data-stu-id="49ca6-109">You don't need to create them, you simply use them.</span></span> <span data-ttu-id="49ca6-110">Les classes et méthodes telles que celles-ci sont appelées *classes statiques* , car elles ne sont pas créées, détruites ou modifiées.</span><span class="sxs-lookup"><span data-stu-id="49ca6-110">Classes and methods such as these are called *static classes* because they are not created, destroyed, or changed.</span></span> <span data-ttu-id="49ca6-111">Par souci de clarté, nous fournirons des exemples qui utilisent des classes statiques.</span><span class="sxs-lookup"><span data-stu-id="49ca6-111">To make this clear we will provide examples that use static classes.</span></span>

## <a name="getting-environment-data-with-systemenvironment"></a><span data-ttu-id="49ca6-112">Obtention de données d’environnement avec System.Environment</span><span class="sxs-lookup"><span data-stu-id="49ca6-112">Getting Environment Data with System.Environment</span></span>

<span data-ttu-id="49ca6-113">En règle générale, la première étape de l’utilisation d’un objet dans Windows PowerShell consiste à utiliser l’applet de commande Get-Member pour découvrir les membres qu’il contient.</span><span class="sxs-lookup"><span data-stu-id="49ca6-113">Usually, the first step in working with an object in Windows PowerShell is to use Get-Member to find out what members it contains.</span></span> <span data-ttu-id="49ca6-114">Avec des classes statiques, le processus est un peu différent, car la classe réelle n’est pas un objet.</span><span class="sxs-lookup"><span data-stu-id="49ca6-114">With static classes, the process is a little different because the actual class is not an object.</span></span>

### <a name="referring-to-the-static-systemenvironment-class"></a><span data-ttu-id="49ca6-115">Référence à la classe statique System.Environment</span><span class="sxs-lookup"><span data-stu-id="49ca6-115">Referring to the Static System.Environment Class</span></span>

<span data-ttu-id="49ca6-116">Vous pouvez faire référence à une classe statique en entourant le nom de la classe de crochets.</span><span class="sxs-lookup"><span data-stu-id="49ca6-116">You can refer to a static class by surrounding the class name with square brackets.</span></span> <span data-ttu-id="49ca6-117">Par exemple, vous pouvez faire référence à la classe **System.Environment** en tapant le nom entre crochets.</span><span class="sxs-lookup"><span data-stu-id="49ca6-117">For example, you can refer to **System.Environment** by typing the name within brackets.</span></span> <span data-ttu-id="49ca6-118">Cela a pour effet d’afficher des informations de type générique :</span><span class="sxs-lookup"><span data-stu-id="49ca6-118">Doing so displays some generic type information:</span></span>

```
PS> [System.Environment]

IsPublic IsSerial Name                                     BaseType
-------- -------- ----                                     --------
True     False    Environment                              System.Object
```

> [!NOTE]
> <span data-ttu-id="49ca6-119">Comme mentionné précédemment, Windows PowerShell ajoute automatiquement «  **System.**  »</span><span class="sxs-lookup"><span data-stu-id="49ca6-119">As we mentioned previously, Windows PowerShell automatically prepends ' **System.** '</span></span> <span data-ttu-id="49ca6-120">aux noms de type lorsque vous utilisez l’applet de commande **New-Object** .</span><span class="sxs-lookup"><span data-stu-id="49ca6-120">to type names when you use **New-Object** .</span></span> <span data-ttu-id="49ca6-121">La même chose se produisant en cas d’utilisation d’un nom de type entre crochets, vous pouvez spécifier **\[System.Environment]** en tant que **\[Environment]** .</span><span class="sxs-lookup"><span data-stu-id="49ca6-121">The same thing happens when using a bracketed type name, so you can specify **\[System.Environment]** as **\[Environment]** .</span></span>

<span data-ttu-id="49ca6-122">La classe **System.Environment** contient des informations générales sur l’environnement de travail pour le processus actuel, c’est-à-dire powershell.exe lorsque vous travaillez dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="49ca6-122">The **System.Environment** class contains general information about the working environment for the current process, which is powershell.exe when working within Windows PowerShell.</span></span>

<span data-ttu-id="49ca6-123">Si vous essayez d’afficher les détails de cette classe en tapant **\[System.Environment] | Get-Member** , le type d’objet est signalé comme étant **System.RuntimeType** , pas **System.Environment**  :</span><span class="sxs-lookup"><span data-stu-id="49ca6-123">If you try to view details of this class by typing **\[System.Environment] | Get-Member** , the object type is reported as being **System.RuntimeType** , not **System.Environment** :</span></span>

```
PS> [System.Environment] | Get-Member

   TypeName: System.RuntimeType
```

<span data-ttu-id="49ca6-124">Pour afficher les membres statiques avec Get-Member, spécifiez le paramètre **Static** paramètre :</span><span class="sxs-lookup"><span data-stu-id="49ca6-124">To view static members with Get-Member, specify the **Static** parameter:</span></span>

```
PS> [System.Environment] | Get-Member -Static

   TypeName: System.Environment

Name                       MemberType Definition
----                       ---------- ----------
Equals                     Method     static System.Boolean Equals(Object ob...
Exit                       Method     static System.Void Exit(Int32 exitCode)
...
CommandLine                Property   static System.String CommandLine {get;}
CurrentDirectory           Property   static System.String CurrentDirectory ...
ExitCode                   Property   static System.Int32 ExitCode {get;set;}
HasShutdownStarted         Property   static System.Boolean HasShutdownStart...
MachineName                Property   static System.String MachineName {get;}
NewLine                    Property   static System.String NewLine {get;}
OSVersion                  Property   static System.OperatingSystem OSVersio...
ProcessorCount             Property   static System.Int32 ProcessorCount {get;}
StackTrace                 Property   static System.String StackTrace {get;}
SystemDirectory            Property   static System.String SystemDirectory {...
TickCount                  Property   static System.Int32 TickCount {get;}
UserDomainName             Property   static System.String UserDomainName {g...
UserInteractive            Property   static System.Boolean UserInteractive ...
UserName                   Property   static System.String UserName {get;}
Version                    Property   static System.Version Version {get;}
WorkingSet                 Property   static System.Int64 WorkingSet {get;}
TickCount                               ExitCode
```

<span data-ttu-id="49ca6-125">Nous pouvons désormais sélectionner des propriétés à afficher à partir de System.Environment.</span><span class="sxs-lookup"><span data-stu-id="49ca6-125">We can now select properties to view from System.Environment.</span></span>

### <a name="displaying-static-properties-of-systemenvironment"></a><span data-ttu-id="49ca6-126">Affichage de propriétés statiques de System.Environment</span><span class="sxs-lookup"><span data-stu-id="49ca6-126">Displaying Static Properties of System.Environment</span></span>

<span data-ttu-id="49ca6-127">Les propriétés de System.Environment sont également statiques, et doivent être spécifiées d’une autre façon que des propriétés normales.</span><span class="sxs-lookup"><span data-stu-id="49ca6-127">The properties of System.Environment are also static, and must be specified in a different way than normal properties.</span></span> <span data-ttu-id="49ca6-128">Nous utilisons **::** pour indiquer à Windows PowerShell que nous souhaitons travailler avec une méthode ou propriété statique.</span><span class="sxs-lookup"><span data-stu-id="49ca6-128">We use **::** to indicate to Windows PowerShell that we want to work with a static method or property.</span></span> <span data-ttu-id="49ca6-129">Pour afficher la commande utilisée pour lancer Windows PowerShell, nous vérifions la propriété **CommandLine** en tapant ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="49ca6-129">To see the command that was used to launch Windows PowerShell, we check the **CommandLine** property by typing:</span></span>

```
PS> [System.Environment]::Commandline
"C:\Program Files\Windows PowerShell\v1.0\powershell.exe"
```

<span data-ttu-id="49ca6-130">Pour vérifier la version du système d’exploitation, affichez la propriété OSVersion en tapant ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="49ca6-130">To check the operating system version, display the OSVersion property by typing:</span></span>

```
PS> [System.Environment]::OSVersion

           Platform ServicePack         Version             VersionString
           -------- -----------         -------             -------------
            Win32NT Service Pack 2      5.1.2600.131072     Microsoft Windows...
```

<span data-ttu-id="49ca6-131">Nous pouvons vérifier si l’ordinateur est en cours d’arrêt en affichant la propriété **HasShutdownStarted**  :</span><span class="sxs-lookup"><span data-stu-id="49ca6-131">We can check whether the computer is in the process of shutting down by displaying the **HasShutdownStarted** property:</span></span>

```
PS> [System.Environment]::HasShutdownStarted
False
```

## <a name="doing-math-with-systemmath"></a><span data-ttu-id="49ca6-132">Opérations mathématiques avec System.Math</span><span class="sxs-lookup"><span data-stu-id="49ca6-132">Doing Math with System.Math</span></span>

<span data-ttu-id="49ca6-133">La classe statique System.Math est utile pour effectuer certaines opérations mathématiques.</span><span class="sxs-lookup"><span data-stu-id="49ca6-133">The System.Math static class is useful for performing some mathematical operations.</span></span> <span data-ttu-id="49ca6-134">Les membres importants de **System.Math** sont essentiellement des méthodes que nous pouvons afficher à l’aide de l’applet de commande **Get-Member** .</span><span class="sxs-lookup"><span data-stu-id="49ca6-134">The important members of **System.Math** are mostly methods, which we can display by using **Get-Member** .</span></span>

> [!NOTE]
> <span data-ttu-id="49ca6-135">System.Math dispose de plusieurs méthodes portant le même nom, mais qui se distinguent par le type de leurs paramètres.</span><span class="sxs-lookup"><span data-stu-id="49ca6-135">System.Math has several methods with the same name, but they are distinguished by the type of their parameters.</span></span>

<span data-ttu-id="49ca6-136">Tapez la commande suivante pour répertorier les méthodes de la classe **System.Math** .</span><span class="sxs-lookup"><span data-stu-id="49ca6-136">Type the following command to list the methods of the **System.Math** class.</span></span>

```
PS> [System.Math] | Get-Member -Static -MemberType Methods

   TypeName: System.Math

Name            MemberType Definition
----            ---------- ----------
Abs             Method     static System.Single Abs(Single value), static Sy...
Acos            Method     static System.Double Acos(Double d)
Asin            Method     static System.Double Asin(Double d)
Atan            Method     static System.Double Atan(Double d)
Atan2           Method     static System.Double Atan2(Double y, Double x)
BigMul          Method     static System.Int64 BigMul(Int32 a, Int32 b)
Ceiling         Method     static System.Double Ceiling(Double a), static Sy...
Cos             Method     static System.Double Cos(Double d)
Cosh            Method     static System.Double Cosh(Double value)
DivRem          Method     static System.Int32 DivRem(Int32 a, Int32 b, Int3...
Equals          Method     static System.Boolean Equals(Object objA, Object ...
Exp             Method     static System.Double Exp(Double d)
Floor           Method     static System.Double Floor(Double d), static Syst...
IEEERemainder   Method     static System.Double IEEERemainder(Double x, Doub...
Log             Method     static System.Double Log(Double d), static System...
Log10           Method     static System.Double Log10(Double d)
Max             Method     static System.SByte Max(SByte val1, SByte val2), ...
Min             Method     static System.SByte Min(SByte val1, SByte val2), ...
Pow             Method     static System.Double Pow(Double x, Double y)
ReferenceEquals Method     static System.Boolean ReferenceEquals(Object objA...
Round           Method     static System.Double Round(Double a), static Syst...
Sign            Method     static System.Int32 Sign(SByte value), static Sys...
Sin             Method     static System.Double Sin(Double a)
Sinh            Method     static System.Double Sinh(Double value)
Sqrt            Method     static System.Double Sqrt(Double d)
Tan             Method     static System.Double Tan(Double a)
Tanh            Method     static System.Double Tanh(Double value)
Truncate        Method     static System.Decimal Truncate(Decimal d), static...
```

<span data-ttu-id="49ca6-137">Cette opération affiche plusieurs méthodes mathématiques.</span><span class="sxs-lookup"><span data-stu-id="49ca6-137">This displays several mathematical methods.</span></span> <span data-ttu-id="49ca6-138">Voici une liste de commandes qui illustrent le fonctionnement de certaines méthodes courantes :</span><span class="sxs-lookup"><span data-stu-id="49ca6-138">Here is a list of commands that demonstrate how some of the common methods work:</span></span>

```
PS> [System.Math]::Sqrt(9)
3
PS> [System.Math]::Pow(2,3)
8
PS> [System.Math]::Floor(3.3)
3
PS> [System.Math]::Floor(-3.3)
-4
PS> [System.Math]::Ceiling(3.3)
4
PS> [System.Math]::Ceiling(-3.3)
-3
PS> [System.Math]::Max(2,7)
7
PS> [System.Math]::Min(2,7)
2
PS> [System.Math]::Truncate(9.3)
9
PS> [System.Math]::Truncate(-9.3)
-9
```
