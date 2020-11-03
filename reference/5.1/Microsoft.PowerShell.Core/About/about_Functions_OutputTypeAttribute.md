---
description: Décrit un attribut qui indique le type d'objet retourné par la fonction.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions_outputtypeattribute?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions_OutputTypeAttribute
ms.openlocfilehash: cff471057a656f4c603d058f9db23a1ea003cd2c
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208026"
---
# <a name="about-functions-outputtypeattribute"></a><span data-ttu-id="93c41-104">À propos des fonctions OutputTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="93c41-104">About Functions OutputTypeAttribute</span></span>

## <a name="short-description"></a><span data-ttu-id="93c41-105">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="93c41-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="93c41-106">Décrit un attribut qui indique le type d'objet retourné par la fonction.</span><span class="sxs-lookup"><span data-stu-id="93c41-106">Describes an attribute that reports the type of object that the function returns.</span></span>

## <a name="long-description"></a><span data-ttu-id="93c41-107">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="93c41-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="93c41-108">L’attribut OutputType répertorie les types .NET des objets retournées par la fonction.</span><span class="sxs-lookup"><span data-stu-id="93c41-108">The OutputType attribute lists the .NET types of objects that the functions returns.</span></span> <span data-ttu-id="93c41-109">Vous pouvez utiliser son paramètre ParameterSetName facultatif pour répertorier différents types de sortie pour chaque jeu de paramètres.</span><span class="sxs-lookup"><span data-stu-id="93c41-109">You can use its optional ParameterSetName parameter to list different output types for each parameter set.</span></span>

<span data-ttu-id="93c41-110">L’attribut OutputType est pris en charge sur les fonctions simples et avancées.</span><span class="sxs-lookup"><span data-stu-id="93c41-110">The OutputType attribute is supported on simple and advanced functions.</span></span> <span data-ttu-id="93c41-111">Il est indépendant de l’attribut CmdletBinding.</span><span class="sxs-lookup"><span data-stu-id="93c41-111">It is independent of the CmdletBinding attribute.</span></span>

<span data-ttu-id="93c41-112">L’attribut OutputType fournit la valeur de la propriété OutputType de l’objet **System. Management. Automation. FunctionInfo** retourné par l’applet de commande `Get-Command` .</span><span class="sxs-lookup"><span data-stu-id="93c41-112">The OutputType attribute provides the value of the OutputType property of the **System.Management.Automation.FunctionInfo** object that the `Get-Command` cmdlet returns.</span></span>

<span data-ttu-id="93c41-113">La valeur de l’attribut OutputType n’est qu’une note de documentation.</span><span class="sxs-lookup"><span data-stu-id="93c41-113">The OutputType attribute value is only a documentation note.</span></span> <span data-ttu-id="93c41-114">Elle n’est pas dérivée du code de la fonction ou est comparée à la sortie de la fonction réelle.</span><span class="sxs-lookup"><span data-stu-id="93c41-114">It is not derived from the function code or compared to the actual function output.</span></span> <span data-ttu-id="93c41-115">Par conséquent, la valeur peut être inexacte.</span><span class="sxs-lookup"><span data-stu-id="93c41-115">As such, the value might be inaccurate.</span></span>

## <a name="syntax"></a><span data-ttu-id="93c41-116">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="93c41-116">SYNTAX</span></span>

<span data-ttu-id="93c41-117">L’attribut OutputType des fonctions a la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="93c41-117">The OutputType attribute of functions has the following syntax:</span></span>

```
[OutputType([<TypeLiteral>], ParameterSetName="<Name>")]
[OutputType("<TypeNameString>", ParameterSetName="<Name>")]
```

<span data-ttu-id="93c41-118">Le paramètre **ParameterSetName** est facultatif.</span><span class="sxs-lookup"><span data-stu-id="93c41-118">The **ParameterSetName** parameter is optional.</span></span>

<span data-ttu-id="93c41-119">Vous pouvez répertorier plusieurs types dans l’attribut OutputType.</span><span class="sxs-lookup"><span data-stu-id="93c41-119">You can list multiple types in the OutputType attribute.</span></span>

```
[OutputType([<Type1>],[<Type2>],[<Type3>])]
```

<span data-ttu-id="93c41-120">Vous pouvez utiliser le paramètre **ParameterSetName** pour indiquer que des jeux de paramètres différents retournent des types différents.</span><span class="sxs-lookup"><span data-stu-id="93c41-120">You can use the **ParameterSetName** parameter to indicate that different parameter sets return different types.</span></span>

```
[OutputType([<Type1>], ParameterSetName=("<Set1>","<Set2>"))]
[OutputType([<Type2>], ParameterSetName="<Set3>")]
```

<span data-ttu-id="93c41-121">Placez les instructions de l’attribut OutputType dans la liste des attributs qui précède l' `Param` instruction.</span><span class="sxs-lookup"><span data-stu-id="93c41-121">Place the OutputType attribute statements in the attributes list that precedes the `Param` statement.</span></span>

<span data-ttu-id="93c41-122">L’exemple suivant montre le placement de l’attribut OutputType dans une fonction simple.</span><span class="sxs-lookup"><span data-stu-id="93c41-122">The following example shows the placement of the OutputType attribute in a simple function.</span></span>

```powershell
function SimpleFunction2
{
  [OutputType([<Type>])]
  Param ($Parameter1)

  <function body>
}
```

<span data-ttu-id="93c41-123">L’exemple suivant montre le placement de l’attribut OutputType dans les fonctions avancées.</span><span class="sxs-lookup"><span data-stu-id="93c41-123">The following example shows the placement of the OutputType attribute in advanced functions.</span></span>

```powershell
function AdvancedFunction1
{
  [OutputType([<Type>])]
  Param (
    [parameter(Mandatory=$true)]
    [String[]]
    $Parameter1
  )

  <function body>
}

function AdvancedFunction2
{
  [CmdletBinding(SupportsShouldProcess=<Boolean>)]
  [OutputType([<Type>])]
  Param (
    [parameter(Mandatory=$true)]
    [String[]]
    $Parameter1
  )

  <function body>
}
```

## <a name="examples"></a><span data-ttu-id="93c41-124">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="93c41-124">EXAMPLES</span></span>

### <a name="example-1-create-a-function-that-has-the-outputtype-of-string"></a><span data-ttu-id="93c41-125">Exemple 1 : créer une fonction qui a le OutputType de String</span><span class="sxs-lookup"><span data-stu-id="93c41-125">Example 1: Create a function that has the OutputType of String</span></span>

```powershell
function Send-Greeting
{
  [OutputType([String])]
  Param ($Name)

  "Hello, $Name"
}
```

<span data-ttu-id="93c41-126">Pour afficher la propriété type de sortie qui en résulte, utilisez l’applet de commande `Get-Command` .</span><span class="sxs-lookup"><span data-stu-id="93c41-126">To see the resulting output type property, use the `Get-Command` cmdlet.</span></span>

```powershell
(Get-Command Send-Greeting).OutputType
```

```Output
Name                                               Type
----                                               ----
System.String                                      System.String
```

### <a name="example-2-use-the-output-attribute-to-indicate-dynamic-output-types"></a><span data-ttu-id="93c41-127">Exemple 2 : utilisation de l’attribut output pour indiquer les types de sortie dynamiques</span><span class="sxs-lookup"><span data-stu-id="93c41-127">Example 2: Use the Output attribute to indicate dynamic output types</span></span>

<span data-ttu-id="93c41-128">La fonction avancée suivante utilise l’attribut OutputType pour indiquer que la fonction retourne des types différents en fonction du jeu de paramètres utilisé dans la commande de fonction.</span><span class="sxs-lookup"><span data-stu-id="93c41-128">The following advanced function uses the OutputType attribute to indicate that the function returns different types depending on the parameter set used in the function command.</span></span>

```powershell
function Get-User
{
  [CmdletBinding(DefaultParameterSetName="ID")]

  [OutputType("System.Int32", ParameterSetName="ID")]
  [OutputType([String], ParameterSetName="Name")]

  Param (
    [parameter(Mandatory=$true, ParameterSetName="ID")]
    [Int[]]
    $UserID,

    [parameter(Mandatory=$true, ParameterSetName="Name")]
    [String[]]
    $UserName
  )

  <function body>
}
```

### <a name="example-3-shows-when-an-actual-output-differs-from-the-outputtype"></a><span data-ttu-id="93c41-129">Exemple 3 : indique quand une sortie réelle diffère du OutputType</span><span class="sxs-lookup"><span data-stu-id="93c41-129">Example 3: Shows when an actual output differs from the OutputType</span></span>

<span data-ttu-id="93c41-130">L’exemple suivant montre que la valeur de la propriété type de sortie affiche la valeur de l’attribut OutputType, même si elle est incorrecte.</span><span class="sxs-lookup"><span data-stu-id="93c41-130">The following example demonstrates that the output type property value displays the value of the OutputType attribute, even when it is inaccurate.</span></span>

<span data-ttu-id="93c41-131">La `Get-Time` fonction retourne une chaîne qui contient la forme abrégée de l’heure dans tout objet DateTime.</span><span class="sxs-lookup"><span data-stu-id="93c41-131">The `Get-Time` function returns a string that contains the short form of the time in any DateTime object.</span></span> <span data-ttu-id="93c41-132">Toutefois, l’attribut OutputType indique qu’il retourne un objet **System. DateTime** .</span><span class="sxs-lookup"><span data-stu-id="93c41-132">However, the OutputType attribute reports that it returns a **System.DateTime** object.</span></span>

```powershell
function Get-Time
{
  [OutputType([DateTime])]
  Param (
    [parameter(Mandatory=$true)]
    [Datetime]$DateTime
  )

  $DateTime.ToShortTimeString()
}
```

<span data-ttu-id="93c41-133">La `GetType()` méthode confirme que la fonction retourne une chaîne.</span><span class="sxs-lookup"><span data-stu-id="93c41-133">The `GetType()` method confirms that the function returns a string.</span></span>

```powershell
(Get-Time -DateTime (Get-Date)).GetType().FullName
```

```Output
System.String
```

<span data-ttu-id="93c41-134">Toutefois, la propriété OutputType, qui obtient sa valeur de l’attribut OutputType, signale que la fonction retourne un objet **DateTime** .</span><span class="sxs-lookup"><span data-stu-id="93c41-134">However, the OutputType property, which gets its value from the OutputType attribute, reports that the function returns a **DateTime** object.</span></span>

```powershell
(Get-Command Get-Time).OutputType
```

```Output
Name                                      Type
----                                      ----
System.DateTime                           System.DateTime
```

### <a name="example-4-a-function--that-shouldnt-have-output"></a><span data-ttu-id="93c41-135">Exemple 4 : fonction qui ne doit pas avoir de sortie</span><span class="sxs-lookup"><span data-stu-id="93c41-135">Example 4: A function  that shouldn't have output</span></span>

<span data-ttu-id="93c41-136">L’exemple suivant montre une fonction personnalisée qui doit exécuter et agir, mais ne retourne rien.</span><span class="sxs-lookup"><span data-stu-id="93c41-136">The following example shows a custom function that should perform and action but not return anything.</span></span>

```powershell
function Invoke-Notepad
{
  [OutputType([System.Void])]
  Param ()
  & notepad.exe | Out-Null
}
```

## <a name="notes"></a><span data-ttu-id="93c41-137">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="93c41-137">NOTES</span></span>

<span data-ttu-id="93c41-138">La valeur de la propriété OutputType d’un objet **FunctionInfo** est un tableau d’objets **System. Management. Automation. PSTypeName** , dont chacun possède les propriétés Name et type.</span><span class="sxs-lookup"><span data-stu-id="93c41-138">The value of the OutputType property of a **FunctionInfo** object is an array of **System.Management.Automation.PSTypeName** objects, each of which have Name and Type properties.</span></span>

<span data-ttu-id="93c41-139">Pour obtenir uniquement le nom de chaque type de sortie, utilisez une commande au format suivant.</span><span class="sxs-lookup"><span data-stu-id="93c41-139">To get only the name of each output type, use a command with the following format.</span></span>

```powershell
(Get-Command Get-Time).OutputType | ForEach {$_.Name}
```

<span data-ttu-id="93c41-140">La valeur de la propriété OutputType peut être null.</span><span class="sxs-lookup"><span data-stu-id="93c41-140">The value of the OutputType property can be null.</span></span> <span data-ttu-id="93c41-141">Utilisez une valeur NULL lorsque la sortie n’est pas un type .NET, tel qu’un objet **WMI** ou une vue mise en forme d’un objet.</span><span class="sxs-lookup"><span data-stu-id="93c41-141">Use a null value when the output is a not a .NET type, such as a **WMI** object or a formatted view of an object.</span></span>

## <a name="see-also"></a><span data-ttu-id="93c41-142">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="93c41-142">SEE ALSO</span></span>

[<span data-ttu-id="93c41-143">about_Functions</span><span class="sxs-lookup"><span data-stu-id="93c41-143">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="93c41-144">about_Functions_Advanced</span><span class="sxs-lookup"><span data-stu-id="93c41-144">about_Functions_Advanced</span></span>](about_Functions_Advanced.md)

[<span data-ttu-id="93c41-145">about_Functions_Advanced_Methods</span><span class="sxs-lookup"><span data-stu-id="93c41-145">about_Functions_Advanced_Methods</span></span>](about_Functions_Advanced_Methods.md)

[<span data-ttu-id="93c41-146">about_Functions_Advanced_Parameters</span><span class="sxs-lookup"><span data-stu-id="93c41-146">about_Functions_Advanced_Parameters</span></span>](about_Functions_Advanced_Parameters.md)

[<span data-ttu-id="93c41-147">about_Functions_CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="93c41-147">about_Functions_CmdletBindingAttribute</span></span>](about_Functions_CmdletBindingAttribute.md)
