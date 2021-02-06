---
description: Décrit un attribut qui indique le type d'objet retourné par la fonction.
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions_outputtypeattribute?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions_OutputTypeAttribute
ms.openlocfilehash: 82f1615c4a2fe2a24f104d8e5637103dea6e5a0a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596343"
---
# <a name="about-functions-outputtypeattribute"></a><span data-ttu-id="cee15-103">À propos des fonctions OutputTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="cee15-103">About Functions OutputTypeAttribute</span></span>

## <a name="short-description"></a><span data-ttu-id="cee15-104">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="cee15-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="cee15-105">Décrit un attribut qui indique le type d'objet retourné par la fonction.</span><span class="sxs-lookup"><span data-stu-id="cee15-105">Describes an attribute that reports the type of object that the function returns.</span></span>

## <a name="long-description"></a><span data-ttu-id="cee15-106">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="cee15-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="cee15-107">L’attribut OutputType répertorie les types .NET des objets retournées par la fonction.</span><span class="sxs-lookup"><span data-stu-id="cee15-107">The OutputType attribute lists the .NET types of objects that the functions returns.</span></span> <span data-ttu-id="cee15-108">Vous pouvez utiliser son paramètre ParameterSetName facultatif pour répertorier différents types de sortie pour chaque jeu de paramètres.</span><span class="sxs-lookup"><span data-stu-id="cee15-108">You can use its optional ParameterSetName parameter to list different output types for each parameter set.</span></span>

<span data-ttu-id="cee15-109">L’attribut OutputType est pris en charge sur les fonctions simples et avancées.</span><span class="sxs-lookup"><span data-stu-id="cee15-109">The OutputType attribute is supported on simple and advanced functions.</span></span> <span data-ttu-id="cee15-110">Il est indépendant de l’attribut CmdletBinding.</span><span class="sxs-lookup"><span data-stu-id="cee15-110">It is independent of the CmdletBinding attribute.</span></span>

<span data-ttu-id="cee15-111">L’attribut OutputType fournit la valeur de la propriété OutputType de l’objet **System. Management. Automation. FunctionInfo** retourné par l’applet de commande `Get-Command` .</span><span class="sxs-lookup"><span data-stu-id="cee15-111">The OutputType attribute provides the value of the OutputType property of the **System.Management.Automation.FunctionInfo** object that the `Get-Command` cmdlet returns.</span></span>

<span data-ttu-id="cee15-112">La valeur de l’attribut OutputType n’est qu’une note de documentation.</span><span class="sxs-lookup"><span data-stu-id="cee15-112">The OutputType attribute value is only a documentation note.</span></span> <span data-ttu-id="cee15-113">Elle n’est pas dérivée du code de la fonction ou est comparée à la sortie de la fonction réelle.</span><span class="sxs-lookup"><span data-stu-id="cee15-113">It is not derived from the function code or compared to the actual function output.</span></span> <span data-ttu-id="cee15-114">Par conséquent, la valeur peut être inexacte.</span><span class="sxs-lookup"><span data-stu-id="cee15-114">As such, the value might be inaccurate.</span></span>

## <a name="syntax"></a><span data-ttu-id="cee15-115">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="cee15-115">SYNTAX</span></span>

<span data-ttu-id="cee15-116">L’attribut OutputType des fonctions a la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="cee15-116">The OutputType attribute of functions has the following syntax:</span></span>

```
[OutputType([<TypeLiteral>], ParameterSetName="<Name>")]
[OutputType("<TypeNameString>", ParameterSetName="<Name>")]
```

<span data-ttu-id="cee15-117">Le paramètre **ParameterSetName** est facultatif.</span><span class="sxs-lookup"><span data-stu-id="cee15-117">The **ParameterSetName** parameter is optional.</span></span>

<span data-ttu-id="cee15-118">Vous pouvez répertorier plusieurs types dans l’attribut OutputType.</span><span class="sxs-lookup"><span data-stu-id="cee15-118">You can list multiple types in the OutputType attribute.</span></span>

```
[OutputType([<Type1>],[<Type2>],[<Type3>])]
```

<span data-ttu-id="cee15-119">Vous pouvez utiliser le paramètre **ParameterSetName** pour indiquer que des jeux de paramètres différents retournent des types différents.</span><span class="sxs-lookup"><span data-stu-id="cee15-119">You can use the **ParameterSetName** parameter to indicate that different parameter sets return different types.</span></span>

```
[OutputType([<Type1>], ParameterSetName=("<Set1>","<Set2>"))]
[OutputType([<Type2>], ParameterSetName="<Set3>")]
```

<span data-ttu-id="cee15-120">Placez les instructions de l’attribut OutputType dans la liste des attributs qui précède l' `Param` instruction.</span><span class="sxs-lookup"><span data-stu-id="cee15-120">Place the OutputType attribute statements in the attributes list that precedes the `Param` statement.</span></span>

<span data-ttu-id="cee15-121">L’exemple suivant montre le placement de l’attribut OutputType dans une fonction simple.</span><span class="sxs-lookup"><span data-stu-id="cee15-121">The following example shows the placement of the OutputType attribute in a simple function.</span></span>

```powershell
function SimpleFunction2
{
  [OutputType([<Type>])]
  Param ($Parameter1)

  <function body>
}
```

<span data-ttu-id="cee15-122">L’exemple suivant montre le placement de l’attribut OutputType dans les fonctions avancées.</span><span class="sxs-lookup"><span data-stu-id="cee15-122">The following example shows the placement of the OutputType attribute in advanced functions.</span></span>

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

## <a name="examples"></a><span data-ttu-id="cee15-123">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="cee15-123">EXAMPLES</span></span>

### <a name="example-1-create-a-function-that-has-the-outputtype-of-string"></a><span data-ttu-id="cee15-124">Exemple 1 : créer une fonction qui a le OutputType de String</span><span class="sxs-lookup"><span data-stu-id="cee15-124">Example 1: Create a function that has the OutputType of String</span></span>

```powershell
function Send-Greeting
{
  [OutputType([String])]
  Param ($Name)

  "Hello, $Name"
}
```

<span data-ttu-id="cee15-125">Pour afficher la propriété type de sortie qui en résulte, utilisez l’applet de commande `Get-Command` .</span><span class="sxs-lookup"><span data-stu-id="cee15-125">To see the resulting output type property, use the `Get-Command` cmdlet.</span></span>

```powershell
(Get-Command Send-Greeting).OutputType
```

```Output
Name                                               Type
----                                               ----
System.String                                      System.String
```

### <a name="example-2-use-the-output-attribute-to-indicate-dynamic-output-types"></a><span data-ttu-id="cee15-126">Exemple 2 : utilisation de l’attribut output pour indiquer les types de sortie dynamiques</span><span class="sxs-lookup"><span data-stu-id="cee15-126">Example 2: Use the Output attribute to indicate dynamic output types</span></span>

<span data-ttu-id="cee15-127">La fonction avancée suivante utilise l’attribut OutputType pour indiquer que la fonction retourne des types différents en fonction du jeu de paramètres utilisé dans la commande de fonction.</span><span class="sxs-lookup"><span data-stu-id="cee15-127">The following advanced function uses the OutputType attribute to indicate that the function returns different types depending on the parameter set used in the function command.</span></span>

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

### <a name="example-3-shows-when-an-actual-output-differs-from-the-outputtype"></a><span data-ttu-id="cee15-128">Exemple 3 : indique quand une sortie réelle diffère du OutputType</span><span class="sxs-lookup"><span data-stu-id="cee15-128">Example 3: Shows when an actual output differs from the OutputType</span></span>

<span data-ttu-id="cee15-129">L’exemple suivant montre que la valeur de la propriété type de sortie affiche la valeur de l’attribut OutputType, même si elle est incorrecte.</span><span class="sxs-lookup"><span data-stu-id="cee15-129">The following example demonstrates that the output type property value displays the value of the OutputType attribute, even when it is inaccurate.</span></span>

<span data-ttu-id="cee15-130">La `Get-Time` fonction retourne une chaîne qui contient la forme abrégée de l’heure dans tout objet DateTime.</span><span class="sxs-lookup"><span data-stu-id="cee15-130">The `Get-Time` function returns a string that contains the short form of the time in any DateTime object.</span></span> <span data-ttu-id="cee15-131">Toutefois, l’attribut OutputType indique qu’il retourne un objet **System. DateTime** .</span><span class="sxs-lookup"><span data-stu-id="cee15-131">However, the OutputType attribute reports that it returns a **System.DateTime** object.</span></span>

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

<span data-ttu-id="cee15-132">La `GetType()` méthode confirme que la fonction retourne une chaîne.</span><span class="sxs-lookup"><span data-stu-id="cee15-132">The `GetType()` method confirms that the function returns a string.</span></span>

```powershell
(Get-Time -DateTime (Get-Date)).GetType().FullName
```

```Output
System.String
```

<span data-ttu-id="cee15-133">Toutefois, la propriété OutputType, qui obtient sa valeur de l’attribut OutputType, signale que la fonction retourne un objet **DateTime** .</span><span class="sxs-lookup"><span data-stu-id="cee15-133">However, the OutputType property, which gets its value from the OutputType attribute, reports that the function returns a **DateTime** object.</span></span>

```powershell
(Get-Command Get-Time).OutputType
```

```Output
Name                                      Type
----                                      ----
System.DateTime                           System.DateTime
```

### <a name="example-4-a-function--that-shouldnt-have-output"></a><span data-ttu-id="cee15-134">Exemple 4 : fonction qui ne doit pas avoir de sortie</span><span class="sxs-lookup"><span data-stu-id="cee15-134">Example 4: A function  that shouldn't have output</span></span>

<span data-ttu-id="cee15-135">L’exemple suivant montre une fonction personnalisée qui doit exécuter et agir, mais ne retourne rien.</span><span class="sxs-lookup"><span data-stu-id="cee15-135">The following example shows a custom function that should perform and action but not return anything.</span></span>

```powershell
function Invoke-Notepad
{
  [OutputType([System.Void])]
  Param ()
  & notepad.exe | Out-Null
}
```

## <a name="notes"></a><span data-ttu-id="cee15-136">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="cee15-136">NOTES</span></span>

<span data-ttu-id="cee15-137">La valeur de la propriété OutputType d’un objet **FunctionInfo** est un tableau d’objets **System. Management. Automation. PSTypeName** , dont chacun possède les propriétés Name et type.</span><span class="sxs-lookup"><span data-stu-id="cee15-137">The value of the OutputType property of a **FunctionInfo** object is an array of **System.Management.Automation.PSTypeName** objects, each of which have Name and Type properties.</span></span>

<span data-ttu-id="cee15-138">Pour obtenir uniquement le nom de chaque type de sortie, utilisez une commande au format suivant.</span><span class="sxs-lookup"><span data-stu-id="cee15-138">To get only the name of each output type, use a command with the following format.</span></span>

```powershell
(Get-Command Get-Time).OutputType | ForEach {$_.Name}
```

<span data-ttu-id="cee15-139">La valeur de la propriété OutputType peut être null.</span><span class="sxs-lookup"><span data-stu-id="cee15-139">The value of the OutputType property can be null.</span></span> <span data-ttu-id="cee15-140">Utilisez une valeur NULL lorsque la sortie n’est pas un type .NET, tel qu’un objet **WMI** ou une vue mise en forme d’un objet.</span><span class="sxs-lookup"><span data-stu-id="cee15-140">Use a null value when the output is a not a .NET type, such as a **WMI** object or a formatted view of an object.</span></span>

## <a name="see-also"></a><span data-ttu-id="cee15-141">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="cee15-141">SEE ALSO</span></span>

[<span data-ttu-id="cee15-142">about_Functions</span><span class="sxs-lookup"><span data-stu-id="cee15-142">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="cee15-143">about_Functions_Advanced</span><span class="sxs-lookup"><span data-stu-id="cee15-143">about_Functions_Advanced</span></span>](about_Functions_Advanced.md)

[<span data-ttu-id="cee15-144">about_Functions_Advanced_Methods</span><span class="sxs-lookup"><span data-stu-id="cee15-144">about_Functions_Advanced_Methods</span></span>](about_Functions_Advanced_Methods.md)

[<span data-ttu-id="cee15-145">about_Functions_Advanced_Parameters</span><span class="sxs-lookup"><span data-stu-id="cee15-145">about_Functions_Advanced_Parameters</span></span>](about_Functions_Advanced_Parameters.md)

[<span data-ttu-id="cee15-146">about_Functions_CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="cee15-146">about_Functions_CmdletBindingAttribute</span></span>](about_Functions_CmdletBindingAttribute.md)

