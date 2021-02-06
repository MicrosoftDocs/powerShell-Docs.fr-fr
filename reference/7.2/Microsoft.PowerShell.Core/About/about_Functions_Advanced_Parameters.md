---
description: Explique comment ajouter des paramètres aux fonctions avancées.
Locale: en-US
ms.date: 10/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions_advanced_parameters?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions_Advanced_Parameters
ms.openlocfilehash: da21f6fb7d19fa2ffcd9cd6c5eea217792937ae4
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595472"
---
# <a name="about-functions-advanced-parameters"></a><span data-ttu-id="1541a-103">À propos des paramètres avancés des fonctions</span><span class="sxs-lookup"><span data-stu-id="1541a-103">About Functions Advanced Parameters</span></span>

## <a name="short-description"></a><span data-ttu-id="1541a-104">Description courte</span><span class="sxs-lookup"><span data-stu-id="1541a-104">Short description</span></span>

<span data-ttu-id="1541a-105">Explique comment ajouter des paramètres aux fonctions avancées.</span><span class="sxs-lookup"><span data-stu-id="1541a-105">Explains how to add parameters to advanced functions.</span></span>

## <a name="long-description"></a><span data-ttu-id="1541a-106">Description longue</span><span class="sxs-lookup"><span data-stu-id="1541a-106">Long description</span></span>

<span data-ttu-id="1541a-107">Vous pouvez ajouter des paramètres aux fonctions avancées que vous écrivez et utiliser des attributs et des arguments de paramètre pour limiter les valeurs de paramètres que les utilisateurs de fonction envoient avec le paramètre.</span><span class="sxs-lookup"><span data-stu-id="1541a-107">You can add parameters to the advanced functions that you write, and use parameter attributes and arguments to limit the parameter values that function users submit with the parameter.</span></span>

<span data-ttu-id="1541a-108">Les paramètres que vous ajoutez à votre fonction sont accessibles aux utilisateurs en plus des paramètres communs que PowerShell ajoute automatiquement à toutes les applets de commande et fonctions avancées.</span><span class="sxs-lookup"><span data-stu-id="1541a-108">The parameters that you add to your function are available to users in addition to the common parameters that PowerShell adds automatically to all cmdlets and advanced functions.</span></span> <span data-ttu-id="1541a-109">Pour plus d’informations sur les paramètres communs de PowerShell, consultez [about_CommonParameters](about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="1541a-109">For more information about the PowerShell common parameters, see [about_CommonParameters](about_CommonParameters.md).</span></span>

<span data-ttu-id="1541a-110">À compter de PowerShell 3,0, vous pouvez utiliser la projection avec `@Args` pour représenter les paramètres dans une commande.</span><span class="sxs-lookup"><span data-stu-id="1541a-110">Beginning in PowerShell 3.0, you can use splatting with `@Args` to represent the parameters in a command.</span></span> <span data-ttu-id="1541a-111">La projection est valide sur les fonctions simples et avancées.</span><span class="sxs-lookup"><span data-stu-id="1541a-111">Splatting is valid on simple and advanced functions.</span></span> <span data-ttu-id="1541a-112">Pour plus d’informations, consultez [about_Functions](about_Functions.md) et [about_Splatting](about_Splatting.md).</span><span class="sxs-lookup"><span data-stu-id="1541a-112">For more information, see [about_Functions](about_Functions.md) and [about_Splatting](about_Splatting.md).</span></span>

## <a name="type-conversion-of-parameter-values"></a><span data-ttu-id="1541a-113">Conversion de type de valeurs de paramètre</span><span class="sxs-lookup"><span data-stu-id="1541a-113">Type conversion of parameter values</span></span>

<span data-ttu-id="1541a-114">Quand vous fournissez des chaînes en tant qu’arguments à des paramètres qui attendent un type différent, PowerShell convertit implicitement les chaînes en type de cible de paramètre.</span><span class="sxs-lookup"><span data-stu-id="1541a-114">When you supply strings as arguments to parameters that expect a different type, PowerShell implicitly converts the strings to the parameter target type.</span></span>
<span data-ttu-id="1541a-115">Les fonctions avancées effectuent l’analyse indifférente de la culture des valeurs de paramètre.</span><span class="sxs-lookup"><span data-stu-id="1541a-115">Advanced functions perform culture-invariant parsing of parameter values.</span></span>

<span data-ttu-id="1541a-116">En revanche, une conversion dépendante de la culture est effectuée lors de la liaison de paramètre pour les applets de commande compilées.</span><span class="sxs-lookup"><span data-stu-id="1541a-116">By contrast, a culture-sensitive conversion is performed during parameter binding for compiled cmdlets.</span></span>

<span data-ttu-id="1541a-117">Dans cet exemple, nous créons une applet de commande et une fonction de script qui prennent un `[datetime]` paramètre.</span><span class="sxs-lookup"><span data-stu-id="1541a-117">In this example, we create a cmdlet and a script function that take a `[datetime]` parameter.</span></span> <span data-ttu-id="1541a-118">La culture actuelle est modifiée pour utiliser les paramètres allemands.</span><span class="sxs-lookup"><span data-stu-id="1541a-118">The current culture is changed to use German settings.</span></span>
<span data-ttu-id="1541a-119">Une date au format allemand est passée au paramètre.</span><span class="sxs-lookup"><span data-stu-id="1541a-119">A German-formatted date is passed to the parameter.</span></span>

```powershell
# Create a cmdlet that accepts a [datetime] argument.
Add-Type @'
  using System;
  using System.Management.Automation;
  [Cmdlet("Get", "Date_Cmdlet")]
  public class GetFooCmdlet : Cmdlet {

    [Parameter(Position=0)]
    public DateTime Date { get; set; }

    protected override void ProcessRecord() {
      WriteObject(Date);
    }
  }
'@ -PassThru | % Assembly | Import-Module

[cultureinfo]::CurrentCulture = 'de-DE'
$dateStr = '19-06-2018'

Get-Date_Cmdlet $dateStr
```

```Output
Dienstag, 19. Juni 2018 00:00:00
```

<span data-ttu-id="1541a-120">Comme indiqué ci-dessus, les applets de commande utilisent l’analyse dépendante de la culture pour convertir la chaîne.</span><span class="sxs-lookup"><span data-stu-id="1541a-120">As shown above, cmdlets use culture-sensitive parsing to convert the string.</span></span>

```powershell
# Define an equivalent function.
function Get-Date_Func {
  param(
    [DateTime] $Date
  )
  process {
    $Date
  }
}

[cultureinfo]::CurrentCulture = 'de-DE'

# This German-format date string doesn't work with the invariant culture.
# E.g., [datetime] '19-06-2018' breaks.
$dateStr = '19-06-2018'

Get-Date_Func $dateStr
```

<span data-ttu-id="1541a-121">Les fonctions avancées utilisent l’analyse dite indifférente de la culture, ce qui provoque l’erreur suivante.</span><span class="sxs-lookup"><span data-stu-id="1541a-121">Advanced functions use culture-invariant parsing, which results in the following error.</span></span>

```Output
Get-Date_Func: Cannot process argument transformation on parameter 'Date'.
Cannot convert value "19-06-2018" to type "System.DateTime". Error: "String
'19-06-2018' was not recognized as a valid DateTime."
```

## <a name="static-parameters"></a><span data-ttu-id="1541a-122">Paramètres statiques</span><span class="sxs-lookup"><span data-stu-id="1541a-122">Static parameters</span></span>

<span data-ttu-id="1541a-123">Les paramètres statiques sont des paramètres qui sont toujours disponibles dans la fonction.</span><span class="sxs-lookup"><span data-stu-id="1541a-123">Static parameters are parameters that are always available in the function.</span></span>
<span data-ttu-id="1541a-124">La plupart des paramètres dans les applets de commande et les scripts PowerShell sont des paramètres statiques.</span><span class="sxs-lookup"><span data-stu-id="1541a-124">Most parameters in PowerShell cmdlets and scripts are static parameters.</span></span>

<span data-ttu-id="1541a-125">L’exemple suivant illustre la déclaration d’un paramètre **ComputerName** qui présente les caractéristiques suivantes :</span><span class="sxs-lookup"><span data-stu-id="1541a-125">The following example shows the declaration of a **ComputerName** parameter that has the following characteristics:</span></span>

- <span data-ttu-id="1541a-126">Il est obligatoire (obligatoire).</span><span class="sxs-lookup"><span data-stu-id="1541a-126">It's mandatory (required).</span></span>
- <span data-ttu-id="1541a-127">Il prend en entrée le pipeline.</span><span class="sxs-lookup"><span data-stu-id="1541a-127">It takes input from the pipeline.</span></span>
- <span data-ttu-id="1541a-128">Il prend un tableau de chaînes comme entrée.</span><span class="sxs-lookup"><span data-stu-id="1541a-128">It takes an array of strings as input.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true,
    ValueFromPipeline=$true)]
    [String[]]
    $ComputerName
)
```

## <a name="attributes-of-parameters"></a><span data-ttu-id="1541a-129">Attributs des paramètres</span><span class="sxs-lookup"><span data-stu-id="1541a-129">Attributes of parameters</span></span>

<span data-ttu-id="1541a-130">Cette section décrit les attributs que vous pouvez ajouter aux paramètres de fonction.</span><span class="sxs-lookup"><span data-stu-id="1541a-130">This section describes the attributes that you can add to function parameters.</span></span>

<span data-ttu-id="1541a-131">Tous les attributs sont facultatifs.</span><span class="sxs-lookup"><span data-stu-id="1541a-131">All attributes are optional.</span></span> <span data-ttu-id="1541a-132">Toutefois, si vous omettez l’attribut **CmdletBinding** , pour être reconnu comme une fonction avancée, la fonction doit inclure l’attribut **Parameter** .</span><span class="sxs-lookup"><span data-stu-id="1541a-132">However, if you omit the **CmdletBinding** attribute, then to be recognized as an advanced function, the function must include the **Parameter** attribute.</span></span>

<span data-ttu-id="1541a-133">Vous pouvez ajouter un ou plusieurs attributs dans chaque déclaration de paramètre.</span><span class="sxs-lookup"><span data-stu-id="1541a-133">You can add one or multiple attributes in each parameter declaration.</span></span> <span data-ttu-id="1541a-134">Il n’existe aucune limite quant au nombre d’attributs que vous pouvez ajouter à une déclaration de paramètre.</span><span class="sxs-lookup"><span data-stu-id="1541a-134">There's no limit to the number of attributes that you can add to a parameter declaration.</span></span>

### <a name="parameter-attribute"></a><span data-ttu-id="1541a-135">Attribut de paramètre</span><span class="sxs-lookup"><span data-stu-id="1541a-135">Parameter attribute</span></span>

<span data-ttu-id="1541a-136">L’attribut **Parameter** est utilisé pour déclarer les attributs des paramètres de fonction.</span><span class="sxs-lookup"><span data-stu-id="1541a-136">The **Parameter** attribute is used to declare the attributes of function parameters.</span></span>

<span data-ttu-id="1541a-137">L’attribut **Parameter** est facultatif et vous pouvez l’omettre si aucun des paramètres de vos fonctions n’a besoin d’attributs.</span><span class="sxs-lookup"><span data-stu-id="1541a-137">The **Parameter** attribute is optional, and you can omit it if none of the parameters of your functions need attributes.</span></span> <span data-ttu-id="1541a-138">Toutefois, pour être reconnu comme une fonction avancée, plutôt que comme une fonction simple, une fonction doit avoir l’attribut **CmdletBinding** ou l’attribut **Parameter** , ou les deux.</span><span class="sxs-lookup"><span data-stu-id="1541a-138">But, to be recognized as an advanced function, rather than a simple function, a function must have either the **CmdletBinding** attribute or the **Parameter** attribute, or both.</span></span>

<span data-ttu-id="1541a-139">L’attribut **Parameter** possède des arguments qui définissent les caractéristiques du paramètre, par exemple si le paramètre est obligatoire ou facultatif.</span><span class="sxs-lookup"><span data-stu-id="1541a-139">The **Parameter** attribute has arguments that define the characteristics of the parameter, such as whether the parameter is mandatory or optional.</span></span>

<span data-ttu-id="1541a-140">Utilisez la syntaxe suivante pour déclarer l’attribut de **paramètre** , un argument et une valeur d’argument.</span><span class="sxs-lookup"><span data-stu-id="1541a-140">Use the following syntax to declare the **Parameter** attribute, an argument, and an argument value.</span></span> <span data-ttu-id="1541a-141">Les parenthèses qui entourent l’argument et sa valeur doivent suivre le **paramètre** sans espace intermédiaire.</span><span class="sxs-lookup"><span data-stu-id="1541a-141">The parentheses that enclose the argument and its value must follow **Parameter** with no intervening space.</span></span>

```powershell
Param(
    [Parameter(Argument=value)]
    $ParameterName
)
```

<span data-ttu-id="1541a-142">Utilisez des virgules pour séparer les arguments entre parenthèses.</span><span class="sxs-lookup"><span data-stu-id="1541a-142">Use commas to separate arguments within the parentheses.</span></span> <span data-ttu-id="1541a-143">Utilisez la syntaxe suivante pour déclarer deux arguments de l’attribut **Parameter** .</span><span class="sxs-lookup"><span data-stu-id="1541a-143">Use the following syntax to declare two arguments of the **Parameter** attribute.</span></span>

```powershell
Param(
    [Parameter(Argument1=value1,
    Argument2=value2)]
)
```

<span data-ttu-id="1541a-144">Les types d’arguments booléens de l’attribut **Parameter** ont par défaut la **valeur false** en cas d’omission de l’attribut **Parameter** .</span><span class="sxs-lookup"><span data-stu-id="1541a-144">The boolean argument types of the **Parameter** attribute default to **False** when omitted from the **Parameter** attribute.</span></span> <span data-ttu-id="1541a-145">Définissez la valeur de l’argument sur `$true` ou répertoriez simplement l’argument par nom.</span><span class="sxs-lookup"><span data-stu-id="1541a-145">Set the argument value to `$true` or just list the argument by name.</span></span> <span data-ttu-id="1541a-146">Par exemple, les attributs de **paramètre** suivants sont équivalents.</span><span class="sxs-lookup"><span data-stu-id="1541a-146">For example, the following **Parameter** attributes are equivalent.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
)

# Boolean arguments can be defined using this shorthand syntax

Param(
    [Parameter(Mandatory)]
)
```

<span data-ttu-id="1541a-147">Si vous utilisez l’attribut de **paramètre** sans arguments, comme alternative à l’utilisation de l’attribut **CmdletBinding** , les parenthèses qui suivent le nom de l’attribut sont toujours requises.</span><span class="sxs-lookup"><span data-stu-id="1541a-147">If you use the **Parameter** attribute without arguments, as an alternative to using the **CmdletBinding** attribute, the parentheses that follow the attribute name are still required.</span></span>

```powershell
Param(
    [Parameter()]
    $ParameterName
)
```

#### <a name="mandatory-argument"></a><span data-ttu-id="1541a-148">Argument obligatoire</span><span class="sxs-lookup"><span data-stu-id="1541a-148">Mandatory argument</span></span>

<span data-ttu-id="1541a-149">L' `Mandatory` argument indique que le paramètre est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="1541a-149">The `Mandatory` argument indicates that the parameter is required.</span></span> <span data-ttu-id="1541a-150">Si cet argument n’est pas spécifié, le paramètre est facultatif.</span><span class="sxs-lookup"><span data-stu-id="1541a-150">If this argument isn't specified, the parameter is optional.</span></span>

<span data-ttu-id="1541a-151">L’exemple suivant déclare le paramètre **ComputerName** .</span><span class="sxs-lookup"><span data-stu-id="1541a-151">The following example declares the **ComputerName** parameter.</span></span> <span data-ttu-id="1541a-152">Elle utilise l' `Mandatory` argument pour rendre le paramètre obligatoire.</span><span class="sxs-lookup"><span data-stu-id="1541a-152">It uses the `Mandatory` argument to make the parameter mandatory.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [String[]]
    $ComputerName
)
```

#### <a name="position-argument"></a><span data-ttu-id="1541a-153">Argument position</span><span class="sxs-lookup"><span data-stu-id="1541a-153">Position argument</span></span>

<span data-ttu-id="1541a-154">L' `Position` argument détermine si le nom du paramètre est requis lorsque le paramètre est utilisé dans une commande.</span><span class="sxs-lookup"><span data-stu-id="1541a-154">The `Position` argument determines whether the parameter name is required when the parameter is used in a command.</span></span> <span data-ttu-id="1541a-155">Lorsqu’une déclaration de paramètre inclut l' `Position` argument, le nom du paramètre peut être omis et PowerShell identifie la valeur du paramètre sans nom par sa position, ou ordre, dans la liste des valeurs de paramètre sans nom dans la commande.</span><span class="sxs-lookup"><span data-stu-id="1541a-155">When a parameter declaration includes the `Position` argument, the parameter name can be omitted and PowerShell identifies the unnamed parameter value by its position, or order, in the list of unnamed parameter values in the command.</span></span>

<span data-ttu-id="1541a-156">Si l' `Position` argument n’est pas spécifié, le nom du paramètre, ou un alias ou une abréviation de nom de paramètre, doit précéder la valeur de paramètre chaque fois que le paramètre est utilisé dans une commande.</span><span class="sxs-lookup"><span data-stu-id="1541a-156">If the `Position` argument isn't specified, the parameter name, or a parameter name alias or abbreviation, must precede the parameter value whenever the parameter is used in a command.</span></span>

<span data-ttu-id="1541a-157">Par défaut, tous les paramètres de fonction sont positionnels.</span><span class="sxs-lookup"><span data-stu-id="1541a-157">By default, all function parameters are positional.</span></span> <span data-ttu-id="1541a-158">PowerShell attribue des numéros de position aux paramètres dans l’ordre dans lequel les paramètres sont déclarés dans la fonction.</span><span class="sxs-lookup"><span data-stu-id="1541a-158">PowerShell assigns position numbers to parameters in the order in which the parameters are declared in the function.</span></span> <span data-ttu-id="1541a-159">Pour désactiver cette fonctionnalité, définissez la valeur de l' `PositionalBinding` argument de l’attribut **CmdletBinding** sur `$False` .</span><span class="sxs-lookup"><span data-stu-id="1541a-159">To disable this feature, set the value of the `PositionalBinding` argument of the **CmdletBinding** attribute to `$False`.</span></span> <span data-ttu-id="1541a-160">L' `Position` argument est prioritaire sur la valeur de l' `PositionalBinding` argument de l’attribut **CmdletBinding** .</span><span class="sxs-lookup"><span data-stu-id="1541a-160">The `Position` argument takes precedence over the value of the `PositionalBinding` argument of the **CmdletBinding** attribute.</span></span> <span data-ttu-id="1541a-161">Pour plus d’informations, consultez `PositionalBinding` dans [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md).</span><span class="sxs-lookup"><span data-stu-id="1541a-161">For more information, see `PositionalBinding` in [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md).</span></span>

<span data-ttu-id="1541a-162">La valeur de l' `Position` argument est spécifiée sous la forme d’un entier.</span><span class="sxs-lookup"><span data-stu-id="1541a-162">The value of the `Position` argument is specified as an integer.</span></span> <span data-ttu-id="1541a-163">Une valeur position égale à **0** représente la première position dans la commande, la valeur position **1** représente la deuxième position dans la commande, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="1541a-163">A position value of **0** represents the first position in the command, a position value of **1** represents the second position in the command, and so on.</span></span>

<span data-ttu-id="1541a-164">Si une fonction n’a pas de paramètres positionnels, PowerShell affecte des positions à chaque paramètre en fonction de l’ordre dans lequel les paramètres sont déclarés.</span><span class="sxs-lookup"><span data-stu-id="1541a-164">If a function has no positional parameters, PowerShell assigns positions to each parameter based on the order in which the parameters are declared.</span></span>
<span data-ttu-id="1541a-165">Toutefois, il est recommandé de ne pas compter sur cette attribution.</span><span class="sxs-lookup"><span data-stu-id="1541a-165">However, as a best practice, don't rely on this assignment.</span></span> <span data-ttu-id="1541a-166">Lorsque vous souhaitez que les paramètres soient positionnels, utilisez l' `Position` argument.</span><span class="sxs-lookup"><span data-stu-id="1541a-166">When you want parameters to be positional, use the `Position` argument.</span></span>

<span data-ttu-id="1541a-167">L’exemple suivant déclare le paramètre **ComputerName** .</span><span class="sxs-lookup"><span data-stu-id="1541a-167">The following example declares the **ComputerName** parameter.</span></span> <span data-ttu-id="1541a-168">Elle utilise l' `Position` argument ayant la valeur **0**.</span><span class="sxs-lookup"><span data-stu-id="1541a-168">It uses the `Position` argument with a value of **0**.</span></span> <span data-ttu-id="1541a-169">Par conséquent, lorsque `-ComputerName` est omis de la commande, sa valeur doit être la première ou la seule valeur de paramètre sans nom dans la commande.</span><span class="sxs-lookup"><span data-stu-id="1541a-169">As a result, when `-ComputerName` is omitted from command, its value must be the first or only unnamed parameter value in the command.</span></span>

```powershell
Param(
    [Parameter(Position=0)]
    [String[]]
    $ComputerName
)
```

#### <a name="parametersetname-argument"></a><span data-ttu-id="1541a-170">Argument ParameterSetName</span><span class="sxs-lookup"><span data-stu-id="1541a-170">ParameterSetName argument</span></span>

<span data-ttu-id="1541a-171">L' `ParameterSetName` argument spécifie le jeu de paramètres auquel appartient un paramètre.</span><span class="sxs-lookup"><span data-stu-id="1541a-171">The `ParameterSetName` argument specifies the parameter set to which a parameter belongs.</span></span> <span data-ttu-id="1541a-172">Si aucun jeu de paramètres n’est spécifié, le paramètre appartient à tous les jeux de paramètres définis par la fonction.</span><span class="sxs-lookup"><span data-stu-id="1541a-172">If no parameter set is specified, the parameter belongs to all the parameter sets defined by the function.</span></span> <span data-ttu-id="1541a-173">Par conséquent, pour être unique, chaque jeu de paramètres doit avoir au moins un paramètre qui n’est pas membre d’un autre jeu de paramètres.</span><span class="sxs-lookup"><span data-stu-id="1541a-173">Therefore, to be unique, each parameter set must have at least one parameter that isn't a member of any other parameter set.</span></span>

> [!NOTE]
> <span data-ttu-id="1541a-174">Pour une applet de commande ou une fonction, il existe une limite de 32 jeux de paramètres.</span><span class="sxs-lookup"><span data-stu-id="1541a-174">For a cmdlet or function, there is a limit of 32 parameter sets.</span></span>

<span data-ttu-id="1541a-175">L’exemple suivant déclare un paramètre **ComputerName** dans le `Computer` jeu de paramètres, un paramètre **username** dans le `User` jeu de paramètres et un paramètre **Summary** dans les deux jeux de paramètres.</span><span class="sxs-lookup"><span data-stu-id="1541a-175">The following example declares a **ComputerName** parameter in the `Computer` parameter set, a **UserName** parameter in the `User` parameter set, and a **Summary** parameter in both parameter sets.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true,
    ParameterSetName="Computer")]
    [String[]]
    $ComputerName,

    [Parameter(Mandatory=$true,
    ParameterSetName="User")]
    [String[]]
    $UserName,

    [Parameter(Mandatory=$false)]
    [Switch]
    $Summary
)
```

<span data-ttu-id="1541a-176">Vous ne pouvez spécifier qu’une seule `ParameterSetName` valeur dans chaque argument et un seul `ParameterSetName` argument dans chaque attribut de **paramètre** .</span><span class="sxs-lookup"><span data-stu-id="1541a-176">You can specify only one `ParameterSetName` value in each argument and only one `ParameterSetName` argument in each **Parameter** attribute.</span></span> <span data-ttu-id="1541a-177">Pour indiquer qu’un paramètre apparaît dans plusieurs jeux de paramètres, ajoutez des attributs de **paramètres** supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="1541a-177">To indicate that a parameter appears in more than one parameter set, add additional **Parameter** attributes.</span></span>

<span data-ttu-id="1541a-178">L’exemple suivant ajoute explicitement le paramètre **Summary** aux `Computer` jeux de `User` paramètres et.</span><span class="sxs-lookup"><span data-stu-id="1541a-178">The following example explicitly adds the **Summary** parameter to the `Computer` and `User` parameter sets.</span></span> <span data-ttu-id="1541a-179">Le paramètre **Summary** est facultatif dans le `Computer` jeu de paramètres et obligatoire dans le `User` jeu de paramètres.</span><span class="sxs-lookup"><span data-stu-id="1541a-179">The **Summary** parameter is optional in the `Computer` parameter set and mandatory in the `User` parameter set.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true,
    ParameterSetName="Computer")]
    [String[]]
    $ComputerName,

    [Parameter(Mandatory=$true,
    ParameterSetName="User")]
    [String[]]
    $UserName,

    [Parameter(Mandatory=$false, ParameterSetName="Computer")]
    [Parameter(Mandatory=$true, ParameterSetName="User")]
    [Switch]
    $Summary
)
```

<span data-ttu-id="1541a-180">Pour plus d’informations sur les jeux de paramètres, consultez [à propos des jeux de paramètres](about_parameter_sets.md).</span><span class="sxs-lookup"><span data-stu-id="1541a-180">For more information about parameter sets, see [About Parameter Sets](about_parameter_sets.md).</span></span>

#### <a name="valuefrompipeline-argument"></a><span data-ttu-id="1541a-181">Argument ValueFromPipeline</span><span class="sxs-lookup"><span data-stu-id="1541a-181">ValueFromPipeline argument</span></span>

<span data-ttu-id="1541a-182">L' `ValueFromPipeline` argument indique que le paramètre accepte l’entrée d’un objet Pipeline.</span><span class="sxs-lookup"><span data-stu-id="1541a-182">The `ValueFromPipeline` argument indicates that the parameter accepts input from a pipeline object.</span></span> <span data-ttu-id="1541a-183">Spécifiez cet argument si la fonction accepte la totalité de l’objet, pas seulement une propriété de l’objet.</span><span class="sxs-lookup"><span data-stu-id="1541a-183">Specify this argument if the function accepts the entire object, not just a property of the object.</span></span>

<span data-ttu-id="1541a-184">L’exemple suivant déclare un paramètre **ComputerName** obligatoire et accepte un objet qui est passé à la fonction à partir du pipeline.</span><span class="sxs-lookup"><span data-stu-id="1541a-184">The following example declares a **ComputerName** parameter that's mandatory and accepts an object that's passed to the function from the pipeline.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true,
    ValueFromPipeline=$true)]
    [String[]]
    $ComputerName
)
```

#### <a name="valuefrompipelinebypropertyname-argument"></a><span data-ttu-id="1541a-185">Argument ValueFromPipelineByPropertyName</span><span class="sxs-lookup"><span data-stu-id="1541a-185">ValueFromPipelineByPropertyName argument</span></span>

<span data-ttu-id="1541a-186">L' `ValueFromPipelineByPropertyName` argument indique que le paramètre accepte l’entrée d’une propriété d’un objet Pipeline.</span><span class="sxs-lookup"><span data-stu-id="1541a-186">The `ValueFromPipelineByPropertyName` argument indicates that the parameter accepts input from a property of a pipeline object.</span></span> <span data-ttu-id="1541a-187">La propriété de l’objet doit avoir le même nom ou alias que le paramètre.</span><span class="sxs-lookup"><span data-stu-id="1541a-187">The object property must have the same name or alias as the parameter.</span></span>

<span data-ttu-id="1541a-188">Par exemple, si la fonction a un paramètre **ComputerName** et que l’objet Redirigé a une propriété **ComputerName** , la valeur de la propriété **ComputerName** est assignée au paramètre **ComputerName** de la fonction.</span><span class="sxs-lookup"><span data-stu-id="1541a-188">For example, if the function has a **ComputerName** parameter, and the piped object has a **ComputerName** property, the value of the **ComputerName** property is assigned to the function's **ComputerName** parameter.</span></span>

<span data-ttu-id="1541a-189">L’exemple suivant déclare un paramètre **ComputerName** obligatoire et accepte l’entrée de la propriété **ComputerName** de l’objet qui est transmise à la fonction via le pipeline.</span><span class="sxs-lookup"><span data-stu-id="1541a-189">The following example declares a **ComputerName** parameter that's mandatory and accepts input from the object's **ComputerName** property that's passed to the function through the pipeline.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true,
    ValueFromPipelineByPropertyName=$true)]
    [String[]]
    $ComputerName
)
```

> [!NOTE]
> <span data-ttu-id="1541a-190">Un paramètre typé qui accepte l’entrée de pipeline ( `by Value` ) ou ( `by PropertyName` ) permet d’utiliser des blocs de script de _liaison différée_ sur le paramètre.</span><span class="sxs-lookup"><span data-stu-id="1541a-190">A typed parameter that accepts pipeline input (`by Value`) or (`by PropertyName`) enables use of _delay-bind_ script blocks on the parameter.</span></span>
>
> <span data-ttu-id="1541a-191">Le bloc _de script de liaison différée_ est exécuté automatiquement pendant la **ParameterBinding**.</span><span class="sxs-lookup"><span data-stu-id="1541a-191">The _delay-bind_ script block is run automatically during **ParameterBinding**.</span></span> <span data-ttu-id="1541a-192">Le résultat est lié au paramètre.</span><span class="sxs-lookup"><span data-stu-id="1541a-192">The result is bound to the parameter.</span></span> <span data-ttu-id="1541a-193">La liaison différée ne fonctionne pas pour les paramètres définis en tant que type `ScriptBlock` ou `System.Object` .</span><span class="sxs-lookup"><span data-stu-id="1541a-193">Delay binding does not work for parameters defined as type `ScriptBlock` or `System.Object`.</span></span> <span data-ttu-id="1541a-194">Le bloc de script est passé _sans_ être appelé.</span><span class="sxs-lookup"><span data-stu-id="1541a-194">The script block is passed through _without_ being invoked.</span></span>
>
> <span data-ttu-id="1541a-195">Vous pouvez en savoir plus sur _les blocs de script de liaison différée_ ici [about_Script_Blocks. MD](about_Script_Blocks.md).</span><span class="sxs-lookup"><span data-stu-id="1541a-195">You can read about _delay-bind_ script blocks here [about_Script_Blocks.md](about_Script_Blocks.md).</span></span>

#### <a name="valuefromremainingarguments-argument"></a><span data-ttu-id="1541a-196">Argument ValueFromRemainingArguments</span><span class="sxs-lookup"><span data-stu-id="1541a-196">ValueFromRemainingArguments argument</span></span>

<span data-ttu-id="1541a-197">L' `ValueFromRemainingArguments` argument indique que le paramètre accepte toutes les valeurs du paramètre de la commande qui ne sont pas assignées à d’autres paramètres de la fonction.</span><span class="sxs-lookup"><span data-stu-id="1541a-197">The `ValueFromRemainingArguments` argument indicates that the parameter accepts all the parameter's values in the command that aren't assigned to other parameters of the function.</span></span>

<span data-ttu-id="1541a-198">L’exemple suivant déclare un paramètre de **valeur** obligatoire et un paramètre **restant** qui accepte toutes les valeurs de paramètres restantes soumises à la fonction.</span><span class="sxs-lookup"><span data-stu-id="1541a-198">The following example declares a **Value** parameter that's mandatory and a **Remaining** parameter that accepts all the remaining parameter values that are submitted to the function.</span></span>

```powershell
function Test-Remainder
{
     param(
         [string]
         [Parameter(Mandatory = $true, Position=0)]
         $Value,
         [string[]]
         [Parameter(Position=1, ValueFromRemainingArguments)]
         $Remaining)
     "Found $($Remaining.Count) elements"
     for ($i = 0; $i -lt $Remaining.Count; $i++)
     {
        "${i}: $($Remaining[$i])"
     }
}
Test-Remainder first one,two
```

```Output
Found 2 elements
0: one
1: two
```

> [!NOTE]
> <span data-ttu-id="1541a-199">Avant PowerShell 6,2, la collection **ValueFromRemainingArguments** était jointe en tant qu’entité unique sous l’index **0**.</span><span class="sxs-lookup"><span data-stu-id="1541a-199">Prior to PowerShell 6.2, the **ValueFromRemainingArguments** collection was joined as single entity under index **0**.</span></span>

#### <a name="helpmessage-argument"></a><span data-ttu-id="1541a-200">Argument HelpMessage</span><span class="sxs-lookup"><span data-stu-id="1541a-200">HelpMessage argument</span></span>

<span data-ttu-id="1541a-201">L' `HelpMessage` argument spécifie une chaîne qui contient une brève description du paramètre ou de sa valeur.</span><span class="sxs-lookup"><span data-stu-id="1541a-201">The `HelpMessage` argument specifies a string that contains a brief description of the parameter or its value.</span></span> <span data-ttu-id="1541a-202">PowerShell affiche ce message dans l’invite qui s’affiche lorsqu’il manque une valeur de paramètre obligatoire dans une commande.</span><span class="sxs-lookup"><span data-stu-id="1541a-202">PowerShell displays this message in the prompt that appears when a mandatory parameter value is missing from a command.</span></span> <span data-ttu-id="1541a-203">Cet argument n’a aucun effet sur les paramètres facultatifs.</span><span class="sxs-lookup"><span data-stu-id="1541a-203">This argument has no effect on optional parameters.</span></span>

<span data-ttu-id="1541a-204">L’exemple suivant déclare un paramètre **ComputerName** obligatoire et un message d’aide qui explique la valeur de paramètre attendue.</span><span class="sxs-lookup"><span data-stu-id="1541a-204">The following example declares a mandatory **ComputerName** parameter and a help message that explains the expected parameter value.</span></span>

<span data-ttu-id="1541a-205">S’il n’existe aucune autre syntaxe d' [aide basée sur les commentaires](./about_comment_based_help.md) pour la fonction (par exemple, `.SYNOPSIS` ), ce message s’affiche également dans la `Get-Help` sortie.</span><span class="sxs-lookup"><span data-stu-id="1541a-205">If there is no other [comment-based help](./about_comment_based_help.md) syntax for the function (for example, `.SYNOPSIS`) then this message also shows up in `Get-Help` output.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true,
    HelpMessage="Enter one or more computer names separated by commas.")]
    [String[]]
    $ComputerName
)
```

### <a name="alias-attribute"></a><span data-ttu-id="1541a-206">Alias (attribut)</span><span class="sxs-lookup"><span data-stu-id="1541a-206">Alias attribute</span></span>

<span data-ttu-id="1541a-207">L’attribut **alias** établit un autre nom pour le paramètre.</span><span class="sxs-lookup"><span data-stu-id="1541a-207">The **Alias** attribute establishes an alternate name for the parameter.</span></span>
<span data-ttu-id="1541a-208">Il n’existe aucune limite quant au nombre d’alias que vous pouvez assigner à un paramètre.</span><span class="sxs-lookup"><span data-stu-id="1541a-208">There's no limit to the number of aliases that you can assign to a parameter.</span></span>

<span data-ttu-id="1541a-209">L’exemple suivant montre une déclaration de paramètre qui ajoute les alias **CN** et **MachineName** au paramètre **ComputerName** obligatoire.</span><span class="sxs-lookup"><span data-stu-id="1541a-209">The following example shows a parameter declaration that adds the **CN** and **MachineName** aliases to the mandatory **ComputerName** parameter.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [Alias("CN","MachineName")]
    [String[]]
    $ComputerName
)
```

### <a name="supportswildcards-attribute"></a><span data-ttu-id="1541a-210">Attribut SupportsWildcards</span><span class="sxs-lookup"><span data-stu-id="1541a-210">SupportsWildcards attribute</span></span>

<span data-ttu-id="1541a-211">L’attribut **SupportsWildcards** est utilisé pour indiquer que le paramètre accepte les valeurs de caractères génériques.</span><span class="sxs-lookup"><span data-stu-id="1541a-211">The **SupportsWildcards** attribute is used to indicate that the parameter accepts wildcard values.</span></span> <span data-ttu-id="1541a-212">L’exemple suivant illustre une déclaration de paramètre pour un paramètre de **chemin d’accès** obligatoire qui prend en charge les valeurs de caractère générique.</span><span class="sxs-lookup"><span data-stu-id="1541a-212">The following example shows a parameter declaration for a mandatory **Path** parameter that supports wildcard values.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [SupportsWildcards()]
    [String[]]
    $Path
)
```

<span data-ttu-id="1541a-213">L’utilisation de cet attribut n’active pas automatiquement la prise en charge des caractères génériques.</span><span class="sxs-lookup"><span data-stu-id="1541a-213">Using this attribute does not automatically enable wildcard support.</span></span> <span data-ttu-id="1541a-214">Le développeur d’applets de commande doit implémenter le code pour gérer l’entrée de caractères génériques.</span><span class="sxs-lookup"><span data-stu-id="1541a-214">The cmdlet developer must implement the code to handle the wildcard input.</span></span> <span data-ttu-id="1541a-215">Les caractères génériques pris en charge peuvent varier en fonction de l’API ou du fournisseur PowerShell sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="1541a-215">The wildcards supported can vary according to the underlying API or PowerShell provider.</span></span> <span data-ttu-id="1541a-216">Pour plus d’informations, consultez [about_Wildcards](about_Wildcards.md).</span><span class="sxs-lookup"><span data-stu-id="1541a-216">For more information, see [about_Wildcards](about_Wildcards.md).</span></span>

### <a name="parameter-and-variable-validation-attributes"></a><span data-ttu-id="1541a-217">Attributs de validation des paramètres et des variables</span><span class="sxs-lookup"><span data-stu-id="1541a-217">Parameter and variable validation attributes</span></span>

<span data-ttu-id="1541a-218">Les attributs de validation dirigent PowerShell pour tester les valeurs de paramètres que les utilisateurs envoient lorsqu’ils appellent la fonction Advanced.</span><span class="sxs-lookup"><span data-stu-id="1541a-218">Validation attributes direct PowerShell to test the parameter values that users submit when they call the advanced function.</span></span> <span data-ttu-id="1541a-219">Si les valeurs de paramètre échouent au test, une erreur est générée et la fonction n’est pas appelée.</span><span class="sxs-lookup"><span data-stu-id="1541a-219">If the parameter values fail the test, an error is generated and the function isn't called.</span></span> <span data-ttu-id="1541a-220">La validation de paramètre s’applique uniquement à l’entrée fournie et toutes les autres valeurs telles que les valeurs par défaut ne sont pas validées.</span><span class="sxs-lookup"><span data-stu-id="1541a-220">Parameter validation is only applied to the input provided and any other values like default values are not validated.</span></span>

<span data-ttu-id="1541a-221">Vous pouvez également utiliser les attributs de validation pour limiter les valeurs que les utilisateurs peuvent spécifier pour les variables.</span><span class="sxs-lookup"><span data-stu-id="1541a-221">You can also use the validation attributes to restrict the values that users can specify for variables.</span></span> <span data-ttu-id="1541a-222">Quand vous utilisez un convertisseur de type avec un attribut de validation, le convertisseur de type doit être défini avant l’attribut.</span><span class="sxs-lookup"><span data-stu-id="1541a-222">When you use a type converter along with a validation attribute, the type converter has to be defined before the attribute.</span></span>

```powershell
[int32][AllowNull()] $number = 7
```

### <a name="allownull-validation-attribute"></a><span data-ttu-id="1541a-223">Attribut de validation AllowNull a</span><span class="sxs-lookup"><span data-stu-id="1541a-223">AllowNull validation attribute</span></span>

<span data-ttu-id="1541a-224">L’attribut **AllowNull a** permet à la valeur d’un paramètre obligatoire d’être `$null` .</span><span class="sxs-lookup"><span data-stu-id="1541a-224">The **AllowNull** attribute allows the value of a mandatory parameter to be `$null`.</span></span> <span data-ttu-id="1541a-225">L’exemple suivant déclare un paramètre **ComputerInfo** Hashtable qui peut avoir une valeur **null** .</span><span class="sxs-lookup"><span data-stu-id="1541a-225">The following example declares a hashtable **ComputerInfo** parameter that can have a **null** value.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [AllowNull()]
    [hashtable]
    $ComputerInfo
)
```

> [!NOTE]
> <span data-ttu-id="1541a-226">L’attribut **AllowNull a** ne fonctionne pas si le convertisseur de type est défini sur String, car le type chaîne n’accepte pas de valeur null.</span><span class="sxs-lookup"><span data-stu-id="1541a-226">The **AllowNull** attribute doesn't work if the type converter is set to string as the string type will not accept a null value.</span></span> <span data-ttu-id="1541a-227">Vous pouvez utiliser l’attribut **AllowEmptyString** pour ce scénario.</span><span class="sxs-lookup"><span data-stu-id="1541a-227">You can use the **AllowEmptyString** attribute for this scenario.</span></span>

### <a name="allowemptystring-validation-attribute"></a><span data-ttu-id="1541a-228">Attribut de validation AllowEmptyString</span><span class="sxs-lookup"><span data-stu-id="1541a-228">AllowEmptyString validation attribute</span></span>

<span data-ttu-id="1541a-229">L’attribut **AllowEmptyString** permet à la valeur d’un paramètre obligatoire d’être une chaîne vide ( `""` ).</span><span class="sxs-lookup"><span data-stu-id="1541a-229">The **AllowEmptyString** attribute allows the value of a mandatory parameter to be an empty string (`""`).</span></span> <span data-ttu-id="1541a-230">L’exemple suivant déclare un paramètre **ComputerName** qui peut avoir une valeur de chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="1541a-230">The following example declares a **ComputerName** parameter that can have an empty string value.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [AllowEmptyString()]
    [String]
    $ComputerName
)
```

### <a name="allowemptycollection-validation-attribute"></a><span data-ttu-id="1541a-231">Attribut de validation AllowEmptyCollection</span><span class="sxs-lookup"><span data-stu-id="1541a-231">AllowEmptyCollection validation attribute</span></span>

<span data-ttu-id="1541a-232">L’attribut **AllowEmptyCollection** permet à la valeur d’un paramètre obligatoire d’être une collection vide `@()` .</span><span class="sxs-lookup"><span data-stu-id="1541a-232">The **AllowEmptyCollection** attribute allows the value of a mandatory parameter to be an empty collection `@()`.</span></span> <span data-ttu-id="1541a-233">L’exemple suivant déclare un paramètre **ComputerName** qui peut avoir une valeur de collection vide.</span><span class="sxs-lookup"><span data-stu-id="1541a-233">The following example declares a **ComputerName** parameter that can have an empty collection value.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [AllowEmptyCollection()]
    [String[]]
    $ComputerName
)
```

### <a name="validatecount-validation-attribute"></a><span data-ttu-id="1541a-234">Attribut de validation ValidateCount</span><span class="sxs-lookup"><span data-stu-id="1541a-234">ValidateCount validation attribute</span></span>

<span data-ttu-id="1541a-235">L’attribut **ValidateCount** spécifie le nombre minimal et maximal de valeurs de paramètre acceptées par un paramètre.</span><span class="sxs-lookup"><span data-stu-id="1541a-235">The **ValidateCount** attribute specifies the minimum and maximum number of parameter values that a parameter accepts.</span></span> <span data-ttu-id="1541a-236">PowerShell génère une erreur si le nombre de valeurs de paramètre dans la commande qui appelle la fonction est en dehors de cette plage.</span><span class="sxs-lookup"><span data-stu-id="1541a-236">PowerShell generates an error if the number of parameter values in the command that calls the function is outside that range.</span></span>

<span data-ttu-id="1541a-237">La déclaration de paramètre suivante crée un paramètre **ComputerName** qui prend une à cinq valeurs de paramètre.</span><span class="sxs-lookup"><span data-stu-id="1541a-237">The following parameter declaration creates a **ComputerName** parameter that takes one to five parameter values.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateCount(1,5)]
    [String[]]
    $ComputerName
)
```

### <a name="validatelength-validation-attribute"></a><span data-ttu-id="1541a-238">Attribut de validation ValidateLength</span><span class="sxs-lookup"><span data-stu-id="1541a-238">ValidateLength validation attribute</span></span>

<span data-ttu-id="1541a-239">L’attribut **ValidateLength** spécifie le nombre minimal et le nombre maximal de caractères dans une valeur de paramètre ou de variable.</span><span class="sxs-lookup"><span data-stu-id="1541a-239">The **ValidateLength** attribute specifies the minimum and maximum number of characters in a parameter or variable value.</span></span> <span data-ttu-id="1541a-240">PowerShell génère une erreur si la longueur d’une valeur spécifiée pour un paramètre ou une variable est en dehors de la plage.</span><span class="sxs-lookup"><span data-stu-id="1541a-240">PowerShell generates an error if the length of a value specified for a parameter or a variable is outside of the range.</span></span>

<span data-ttu-id="1541a-241">Dans l’exemple suivant, chaque nom d’ordinateur doit comporter un à dix caractères.</span><span class="sxs-lookup"><span data-stu-id="1541a-241">In the following example, each computer name must have one to ten characters.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateLength(1,10)]
    [String[]]
    $ComputerName
)
```

<span data-ttu-id="1541a-242">Dans l’exemple suivant, la valeur de la variable `$number` doit être au minimum d’un caractère et comporter un maximum de dix caractères.</span><span class="sxs-lookup"><span data-stu-id="1541a-242">In the following example, the value of the variable `$number` must be a minimum of one character in length, and a maximum of ten characters.</span></span>

```powershell
[Int32][ValidateLength(1,10)]$number = '01'
```

> [!NOTE]
> <span data-ttu-id="1541a-243">Dans cet exemple, la valeur de `01` est incluse entre guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="1541a-243">In this example, the value of `01` is wrapped in single quotes.</span></span> <span data-ttu-id="1541a-244">L’attribut **ValidateLength** n’accepte pas de nombre sans encapsuler les guillemets.</span><span class="sxs-lookup"><span data-stu-id="1541a-244">The **ValidateLength** attribute won't accept a number without being wrapped in quotes.</span></span>

### <a name="validatepattern-validation-attribute"></a><span data-ttu-id="1541a-245">Attribut de validation ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="1541a-245">ValidatePattern validation attribute</span></span>

<span data-ttu-id="1541a-246">L’attribut **ValidatePattern** spécifie une expression régulière qui est comparée à la valeur du paramètre ou de la variable.</span><span class="sxs-lookup"><span data-stu-id="1541a-246">The **ValidatePattern** attribute specifies a regular expression that's compared to the parameter or variable value.</span></span> <span data-ttu-id="1541a-247">PowerShell génère une erreur si la valeur ne correspond pas au modèle d’expression régulière.</span><span class="sxs-lookup"><span data-stu-id="1541a-247">PowerShell generates an error if the value doesn't match the regular expression pattern.</span></span>

<span data-ttu-id="1541a-248">Dans l’exemple suivant, la valeur de paramètre doit contenir un nombre à quatre chiffres, et chaque chiffre doit être un nombre zéro à neuf.</span><span class="sxs-lookup"><span data-stu-id="1541a-248">In the following example, the parameter value must contain a four-digit number, and each digit must be a number zero to nine.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidatePattern("[0-9][0-9][0-9][0-9]")]
    [String[]]
    $ComputerName
)
```

<span data-ttu-id="1541a-249">Dans l’exemple suivant, la valeur de la variable `$number` doit être exactement un nombre à quatre chiffres, et chaque chiffre doit être un nombre zéro à neuf.</span><span class="sxs-lookup"><span data-stu-id="1541a-249">In the following example, the value of the variable `$number` must be exactly a four-digit number, and each digit must be a number zero to nine.</span></span>

```powershell
[Int32][ValidatePattern("^[0-9][0-9][0-9][0-9]$")]$number = 1111
```

### <a name="validaterange-validation-attribute"></a><span data-ttu-id="1541a-250">Attribut de validation ValidateRange</span><span class="sxs-lookup"><span data-stu-id="1541a-250">ValidateRange validation attribute</span></span>

<span data-ttu-id="1541a-251">L’attribut **ValidateRange** spécifie une plage numérique ou une valeur d’énumération **ValidateRangeKind** pour chaque valeur de paramètre ou de variable.</span><span class="sxs-lookup"><span data-stu-id="1541a-251">The **ValidateRange** attribute specifies a numeric range or a **ValidateRangeKind** enum value for each parameter or variable value.</span></span>
<span data-ttu-id="1541a-252">PowerShell génère une erreur si une valeur est en dehors de cette plage.</span><span class="sxs-lookup"><span data-stu-id="1541a-252">PowerShell generates an error if any value is outside that range.</span></span>

<span data-ttu-id="1541a-253">L’énumération **ValidateRangeKind** autorise les valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="1541a-253">The **ValidateRangeKind** enum allows for the following values:</span></span>

- <span data-ttu-id="1541a-254">**Positif** : nombre supérieur à zéro.</span><span class="sxs-lookup"><span data-stu-id="1541a-254">**Positive** - A number greater than zero.</span></span>
- <span data-ttu-id="1541a-255">**Negative** : nombre inférieur à zéro.</span><span class="sxs-lookup"><span data-stu-id="1541a-255">**Negative** - A number less than zero.</span></span>
- <span data-ttu-id="1541a-256">Non **positif** : nombre inférieur ou égal à zéro.</span><span class="sxs-lookup"><span data-stu-id="1541a-256">**NonPositive** - A number less than or equal to zero.</span></span>
- <span data-ttu-id="1541a-257">Non **négatif** : nombre supérieur ou égal à zéro.</span><span class="sxs-lookup"><span data-stu-id="1541a-257">**NonNegative** - A number greater than or equal to zero.</span></span>

<span data-ttu-id="1541a-258">Dans l’exemple suivant, la valeur du paramètre **tentatives** doit être comprise entre zéro et dix.</span><span class="sxs-lookup"><span data-stu-id="1541a-258">In the following example, the value of the **Attempts** parameter must be between zero and ten.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateRange(0,10)]
    [Int]
    $Attempts
)
```

<span data-ttu-id="1541a-259">Dans l’exemple suivant, la valeur de la variable `$number` doit être comprise entre zéro et dix.</span><span class="sxs-lookup"><span data-stu-id="1541a-259">In the following example, the value of the variable `$number` must be between zero and ten.</span></span>

```powershell
[Int32][ValidateRange(0,10)]$number = 5
```

<span data-ttu-id="1541a-260">Dans l’exemple suivant, la valeur de la variable `$number` doit être supérieure à zéro.</span><span class="sxs-lookup"><span data-stu-id="1541a-260">In the following example, the value of the variable `$number` must be greater than zero.</span></span>

```powershell
[Int32][ValidateRange("Positive")]$number = 1
```

### <a name="validatescript-validation-attribute"></a><span data-ttu-id="1541a-261">Attribut de validation ValidateScript</span><span class="sxs-lookup"><span data-stu-id="1541a-261">ValidateScript validation attribute</span></span>

<span data-ttu-id="1541a-262">L’attribut **ValidateScript** spécifie un script utilisé pour valider une valeur de paramètre ou de variable.</span><span class="sxs-lookup"><span data-stu-id="1541a-262">The **ValidateScript** attribute specifies a script that is used to validate a parameter or variable value.</span></span> <span data-ttu-id="1541a-263">PowerShell dirige la valeur vers le script et génère une erreur si le script retourne `$false` ou si le script lève une exception.</span><span class="sxs-lookup"><span data-stu-id="1541a-263">PowerShell pipes the value to the script, and generates an error if the script returns `$false` or if the script throws an exception.</span></span>

<span data-ttu-id="1541a-264">Lorsque vous utilisez l’attribut **ValidateScript** , la valeur qui est validée est mappée à la `$_` variable.</span><span class="sxs-lookup"><span data-stu-id="1541a-264">When you use the **ValidateScript** attribute, the value that's being validated is mapped to the `$_` variable.</span></span> <span data-ttu-id="1541a-265">Vous pouvez utiliser la `$_` variable pour faire référence à la valeur dans le script.</span><span class="sxs-lookup"><span data-stu-id="1541a-265">You can use the `$_` variable to refer to the value in the script.</span></span>

<span data-ttu-id="1541a-266">Dans l’exemple suivant, la valeur du paramètre **EventDate** doit être supérieure ou égale à la date actuelle.</span><span class="sxs-lookup"><span data-stu-id="1541a-266">In the following example, the value of the **EventDate** parameter must be greater than or equal to the current date.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateScript({$_ -ge (Get-Date)})]
    [DateTime]
    $EventDate
)
```

<span data-ttu-id="1541a-267">Dans l’exemple suivant, la valeur de la variable `$date` doit être supérieure ou égale à la date et à l’heure actuelles.</span><span class="sxs-lookup"><span data-stu-id="1541a-267">In the following example, the value of the variable `$date` must be greater than or equal to the current date and time.</span></span>

```powershell
[DateTime][ValidateScript({$_ -ge (Get-Date)})]$date = (Get-Date)
```

> [!NOTE]
> <span data-ttu-id="1541a-268">Si vous utilisez **ValidateScript**, vous ne pouvez pas passer une `$null` valeur au paramètre.</span><span class="sxs-lookup"><span data-stu-id="1541a-268">If you use **ValidateScript**, you cannot pass a `$null` value to the parameter.</span></span> <span data-ttu-id="1541a-269">Lorsque vous transmettez une valeur null, **ValidateScript** ne peut pas valider l’argument.</span><span class="sxs-lookup"><span data-stu-id="1541a-269">When you pass a null value **ValidateScript** can't validate the argument.</span></span>

### <a name="validateset-attribute"></a><span data-ttu-id="1541a-270">Attribut ValidateSet</span><span class="sxs-lookup"><span data-stu-id="1541a-270">ValidateSet attribute</span></span>

<span data-ttu-id="1541a-271">L’attribut **ValidateSet** spécifie un ensemble de valeurs valides pour un paramètre ou une variable et active la saisie semi-automatique via la touche Tab.</span><span class="sxs-lookup"><span data-stu-id="1541a-271">The **ValidateSet** attribute specifies a set of valid values for a parameter or variable and enables tab completion.</span></span> <span data-ttu-id="1541a-272">PowerShell génère une erreur si la valeur d’un paramètre ou d’une variable ne correspond pas à une valeur de l’ensemble.</span><span class="sxs-lookup"><span data-stu-id="1541a-272">PowerShell generates an error if a parameter or variable value doesn't match a value in the set.</span></span> <span data-ttu-id="1541a-273">Dans l’exemple suivant, la valeur du paramètre de **détail** peut uniquement être faible, moyenne ou élevée.</span><span class="sxs-lookup"><span data-stu-id="1541a-273">In the following example, the value of the **Detail** parameter can only be Low, Average, or High.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateSet("Low", "Average", "High")]
    [String[]]
    $Detail
)
```

<span data-ttu-id="1541a-274">Dans l’exemple suivant, la valeur de la variable `$flavor` doit être Chocolate, fraise ou vanille.</span><span class="sxs-lookup"><span data-stu-id="1541a-274">In the following example, the value of the variable `$flavor` must be either Chocolate, Strawberry, or Vanilla.</span></span>

```powershell
[ValidateSet("Chocolate", "Strawberry", "Vanilla")]
[String]$flavor = "Strawberry"
```

<span data-ttu-id="1541a-275">La validation se produit chaque fois que cette variable est assignée même dans le script.</span><span class="sxs-lookup"><span data-stu-id="1541a-275">The validation occurs whenever that variable is assigned even within the script.</span></span> <span data-ttu-id="1541a-276">Par exemple, le code suivant génère une erreur au moment de l’exécution :</span><span class="sxs-lookup"><span data-stu-id="1541a-276">For example, the following results in an error at runtime:</span></span>

```powershell
Param(
    [ValidateSet("hello", "world")]
    [String]$Message
)

$Message = "bye"
```

#### <a name="dynamic-validateset-values"></a><span data-ttu-id="1541a-277">Valeurs validateSet dynamiques</span><span class="sxs-lookup"><span data-stu-id="1541a-277">Dynamic validateSet values</span></span>

<span data-ttu-id="1541a-278">Vous pouvez utiliser une **classe** pour générer dynamiquement les valeurs de **ValidateSet** au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="1541a-278">You can use a **Class** to dynamically generate the values for **ValidateSet** at runtime.</span></span> <span data-ttu-id="1541a-279">Dans l’exemple suivant, les valeurs valides pour la variable `$Sound` sont générées à l’aide d’une **classe** nommée **SoundNames** qui recherche les fichiers audio disponibles dans trois chemins de système de fichiers :</span><span class="sxs-lookup"><span data-stu-id="1541a-279">In the following example, the valid values for the variable `$Sound` are generated via a **Class** named **SoundNames** that checks three filesystem paths for available sound files:</span></span>

```powershell
Class SoundNames : System.Management.Automation.IValidateSetValuesGenerator {
    [String[]] GetValidValues() {
        $SoundPaths = '/System/Library/Sounds/',
            '/Library/Sounds','~/Library/Sounds'
        $SoundNames = ForEach ($SoundPath in $SoundPaths) {
            If (Test-Path $SoundPath) {
                (Get-ChildItem $SoundPath).BaseName
            }
        }
        return [String[]] $SoundNames
    }
}
```

<span data-ttu-id="1541a-280">La `[SoundNames]` classe est ensuite implémentée en tant que valeur **ValidateSet** dynamique comme suit :</span><span class="sxs-lookup"><span data-stu-id="1541a-280">The `[SoundNames]` class is then implemented as a dynamic **ValidateSet** value as follows:</span></span>

```powershell
Param(
    [ValidateSet([SoundNames])]
    [String]$Sound
)
```

### <a name="validatenotnull-validation-attribute"></a><span data-ttu-id="1541a-281">Attribut de validation ValidateNotNull</span><span class="sxs-lookup"><span data-stu-id="1541a-281">ValidateNotNull validation attribute</span></span>

<span data-ttu-id="1541a-282">L’attribut **ValidateNotNull** spécifie que la valeur du paramètre ne peut pas être `$null` .</span><span class="sxs-lookup"><span data-stu-id="1541a-282">The **ValidateNotNull** attribute specifies that the parameter value can't be `$null`.</span></span> <span data-ttu-id="1541a-283">PowerShell génère une erreur si la valeur du paramètre est `$null` .</span><span class="sxs-lookup"><span data-stu-id="1541a-283">PowerShell generates an error if the parameter value is `$null`.</span></span>

<span data-ttu-id="1541a-284">L’attribut **ValidateNotNull** est conçu pour être utilisé lorsque le paramètre est facultatif et que le type n’est pas défini ou possède un convertisseur de type qui ne peut pas convertir implicitement une valeur NULL comme **Object**.</span><span class="sxs-lookup"><span data-stu-id="1541a-284">The **ValidateNotNull** attribute is designed to be used when the parameter is optional and the type is undefined or has a type converter that can't implicitly convert a null value like **object**.</span></span> <span data-ttu-id="1541a-285">Si vous spécifiez un type qui convertit implicitement une valeur null telle qu’une **chaîne**, la valeur null est convertie en une chaîne vide même lors de l’utilisation de l’attribut **ValidateNotNull** .</span><span class="sxs-lookup"><span data-stu-id="1541a-285">If you specify a type that that will implicitly convert a null value such as a **string**, the null value is converted to an empty string even when using the **ValidateNotNull** attribute.</span></span> <span data-ttu-id="1541a-286">Pour ce scénario, utilisez **ValidateNotNullOrEmpty**</span><span class="sxs-lookup"><span data-stu-id="1541a-286">For this scenario use the **ValidateNotNullOrEmpty**</span></span>

<span data-ttu-id="1541a-287">Dans l’exemple suivant, la valeur du paramètre **ID** ne peut pas être `$null` .</span><span class="sxs-lookup"><span data-stu-id="1541a-287">In the following example, the value of the **ID** parameter can't be `$null`.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$false)]
    [ValidateNotNull()]
    $ID
)
```

### <a name="validatenotnullorempty-validation-attribute"></a><span data-ttu-id="1541a-288">Attribut de validation ValidateNotNullOrEmpty</span><span class="sxs-lookup"><span data-stu-id="1541a-288">ValidateNotNullOrEmpty validation attribute</span></span>

<span data-ttu-id="1541a-289">L’attribut **ValidateNotNullOrEmpty** spécifie que la valeur du paramètre ne peut pas être `$null` et ne peut pas être une chaîne vide ( `""` ).</span><span class="sxs-lookup"><span data-stu-id="1541a-289">The **ValidateNotNullOrEmpty** attribute specifies that the parameter value can't be `$null` and can't be an empty string (`""`).</span></span> <span data-ttu-id="1541a-290">PowerShell génère une erreur si le paramètre est utilisé dans un appel de fonction, mais que sa valeur est `$null` , une chaîne vide ( `""` ) ou un tableau vide `@()` .</span><span class="sxs-lookup"><span data-stu-id="1541a-290">PowerShell generates an error if the parameter is used in a function call, but its value is `$null`, an empty string (`""`), or an empty array `@()`.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateNotNullOrEmpty()]
    [String[]]
    $UserName
)
```

### <a name="validatedrive-validation-attribute"></a><span data-ttu-id="1541a-291">Attribut de validation ValidateDrive</span><span class="sxs-lookup"><span data-stu-id="1541a-291">ValidateDrive validation attribute</span></span>

<span data-ttu-id="1541a-292">L’attribut **ValidateDrive** spécifie que la valeur de paramètre doit représenter le chemin d’accès, qui fait référence à des lecteurs autorisés uniquement.</span><span class="sxs-lookup"><span data-stu-id="1541a-292">The **ValidateDrive** attribute specifies that the parameter value must represent the path, that's referring to allowed drives only.</span></span> <span data-ttu-id="1541a-293">PowerShell génère une erreur si la valeur du paramètre fait référence à des lecteurs autres que le autorisé.</span><span class="sxs-lookup"><span data-stu-id="1541a-293">PowerShell generates an error if the parameter value refers to drives other than the allowed.</span></span> <span data-ttu-id="1541a-294">L’existence du chemin d’accès, à l’exception du lecteur lui-même, n’est pas vérifiée.</span><span class="sxs-lookup"><span data-stu-id="1541a-294">Existence of the path, except for the drive itself, isn't verified.</span></span>

<span data-ttu-id="1541a-295">Si vous utilisez un chemin d’accès relatif, le lecteur actif doit figurer dans la liste des lecteurs autorisés.</span><span class="sxs-lookup"><span data-stu-id="1541a-295">If you use relative path, the current drive must be in the allowed drive list.</span></span>

```powershell
Param(
    [ValidateDrive("C", "D", "Variable", "Function")]
    [String]$Path
)
```

### <a name="validateuserdrive-validation-attribute"></a><span data-ttu-id="1541a-296">Attribut de validation ValidateUserDrive</span><span class="sxs-lookup"><span data-stu-id="1541a-296">ValidateUserDrive validation attribute</span></span>

<span data-ttu-id="1541a-297">L’attribut **ValidateUserDrive** spécifie que la valeur du paramètre doit représenter le chemin d’accès, qui fait référence au `User` lecteur.</span><span class="sxs-lookup"><span data-stu-id="1541a-297">The **ValidateUserDrive** attribute specifies that the parameter value must represent the path, that is referring to `User` drive.</span></span> <span data-ttu-id="1541a-298">PowerShell génère une erreur si le chemin d’accès fait référence à un autre lecteur.</span><span class="sxs-lookup"><span data-stu-id="1541a-298">PowerShell generates an error if the path refers to a different drive.</span></span> <span data-ttu-id="1541a-299">L’attribut validation vérifie uniquement l’existence de la partie lecteur du chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="1541a-299">The validation attribute only tests for the existence of the drive portion of the path.</span></span>

<span data-ttu-id="1541a-300">Si vous utilisez le chemin d’accès relatif, le lecteur actif doit être `User` .</span><span class="sxs-lookup"><span data-stu-id="1541a-300">If you use relative path, the current drive must be `User`.</span></span>

```powershell
function Test-UserDrivePath{
    [OutputType([bool])]
    Param(
      [Parameter(Mandatory=, Position=0)][ValidateUserDrive()][String]$Path
      )
    $True
}

Test-UserDrivePath -Path C:\
```

```Output
Test-UserDrivePath: Cannot validate argument on parameter 'Path'. The path
argument drive C does not belong to the set of approved drives: User.
Supply a path argument with an approved drive.
```

```powershell
Test-UserDrivePath -Path 'User:\A_folder_that_does_not_exist'
```

```Output
Test-UserDrivePath: Cannot validate argument on parameter 'Path'. Cannot
find drive. A drive with the name 'User' does not exist.
```

<span data-ttu-id="1541a-301">Vous pouvez définir `User` des lecteurs dans des configurations de session d’administration (JEA) juste assez.</span><span class="sxs-lookup"><span data-stu-id="1541a-301">You can define `User` drive in Just Enough Administration (JEA) session configurations.</span></span> <span data-ttu-id="1541a-302">Pour cet exemple, nous créons le lecteur User :.</span><span class="sxs-lookup"><span data-stu-id="1541a-302">For this example, we create the User: drive.</span></span>

```powershell
New-PSDrive -Name 'User' -PSProvider FileSystem -Root $env:HOMEPATH
```

```Output
Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
User               75.76         24.24 FileSystem    C:\Users\ExampleUser

```powershell
Test-UserDrivePath -Path 'User:\A_folder_that_does_not_exist'
```

```Output
True
```

### <a name="validatetrusteddata-validation-attribute"></a><span data-ttu-id="1541a-303">Attribut de validation ValidateTrustedData</span><span class="sxs-lookup"><span data-stu-id="1541a-303">ValidateTrustedData validation attribute</span></span>

<span data-ttu-id="1541a-304">Cet attribut a été ajouté dans PowerShell 6.1.1.</span><span class="sxs-lookup"><span data-stu-id="1541a-304">This attribute was added in PowerShell 6.1.1.</span></span>

<span data-ttu-id="1541a-305">À ce stade, l’attribut est utilisé en interne par PowerShell lui-même et n’est pas destiné à une utilisation externe.</span><span class="sxs-lookup"><span data-stu-id="1541a-305">At this time, the attribute is used internally by PowerShell itself and is not intended for external usage.</span></span>

## <a name="dynamic-parameters"></a><span data-ttu-id="1541a-306">Paramètres dynamiques</span><span class="sxs-lookup"><span data-stu-id="1541a-306">Dynamic parameters</span></span>

<span data-ttu-id="1541a-307">Les paramètres dynamiques sont des paramètres d’une applet de commande, d’une fonction ou d’un script qui sont disponibles uniquement dans certaines conditions.</span><span class="sxs-lookup"><span data-stu-id="1541a-307">Dynamic parameters are parameters of a cmdlet, function, or script that are available only under certain conditions.</span></span>

<span data-ttu-id="1541a-308">Par exemple, plusieurs applets de commande de fournisseur ont des paramètres qui sont disponibles uniquement lorsque l’applet de commande est utilisée dans le lecteur du fournisseur ou dans un chemin d’accès particulier au lecteur du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="1541a-308">For example, several provider cmdlets have parameters that are available only when the cmdlet is used in the provider drive, or in a particular path of the provider drive.</span></span> <span data-ttu-id="1541a-309">Par exemple, le paramètre d' **encodage** est disponible sur les `Add-Content` `Get-Content` `Set-Content` applets de commande, et uniquement lorsqu’il est utilisé dans un lecteur du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="1541a-309">For example, the **Encoding** parameter is available on the `Add-Content`, `Get-Content`, and `Set-Content` cmdlets only when it's used in a file system drive.</span></span>

<span data-ttu-id="1541a-310">Vous pouvez également créer un paramètre qui apparaît uniquement lorsqu’un autre paramètre est utilisé dans la commande de fonction ou lorsqu’un autre paramètre a une certaine valeur.</span><span class="sxs-lookup"><span data-stu-id="1541a-310">You can also create a parameter that appears only when another parameter is used in the function command or when another parameter has a certain value.</span></span>

<span data-ttu-id="1541a-311">Les paramètres dynamiques peuvent être utiles, mais ils peuvent être utilisés uniquement lorsque cela est nécessaire, car ils peuvent être difficiles à découvrir par les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="1541a-311">Dynamic parameters can be useful, but use them only when necessary, because they can be difficult for users to discover.</span></span> <span data-ttu-id="1541a-312">Pour trouver un paramètre dynamique, l’utilisateur doit se trouver dans le chemin d’accès du fournisseur, utiliser le paramètre **argumentlist** de l’applet de commande `Get-Command` ou utiliser le paramètre **path** de `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="1541a-312">To find a dynamic parameter, the user must be in the provider path, use the **ArgumentList** parameter of the `Get-Command` cmdlet, or use the **Path** parameter of `Get-Help`.</span></span>

<span data-ttu-id="1541a-313">Pour créer un paramètre dynamique pour une fonction ou un script, utilisez le `DynamicParam` mot clé.</span><span class="sxs-lookup"><span data-stu-id="1541a-313">To create a dynamic parameter for a function or script, use the `DynamicParam` keyword.</span></span>

<span data-ttu-id="1541a-314">La syntaxe est la suivante :</span><span class="sxs-lookup"><span data-stu-id="1541a-314">The syntax is as follows:</span></span>

`DynamicParam {<statement-list>}`

<span data-ttu-id="1541a-315">Dans la liste instruction, utilisez une `If` instruction pour spécifier les conditions dans lesquelles le paramètre est disponible dans la fonction.</span><span class="sxs-lookup"><span data-stu-id="1541a-315">In the statement list, use an `If` statement to specify the conditions under which the parameter is available in the function.</span></span>

<span data-ttu-id="1541a-316">Utilisez l' `New-Object` applet de commande pour créer un objet **System. Management. Automation. RuntimeDefinedParameter** pour représenter le paramètre et spécifier son nom.</span><span class="sxs-lookup"><span data-stu-id="1541a-316">Use the `New-Object` cmdlet to create a **System.Management.Automation.RuntimeDefinedParameter** object to represent the parameter and specify its name.</span></span>

<span data-ttu-id="1541a-317">Vous pouvez utiliser une `New-Object` commande pour créer un objet **System. Management. Automation. ParameterAttribute** pour représenter les attributs du paramètre, par exemple **obligatoire**, **position** ou **ValueFromPipeline** ou son jeu de paramètres.</span><span class="sxs-lookup"><span data-stu-id="1541a-317">You can use a `New-Object` command to create a **System.Management.Automation.ParameterAttribute** object to represent attributes of the parameter, such as **Mandatory**, **Position**, or **ValueFromPipeline** or its parameter set.</span></span>

<span data-ttu-id="1541a-318">L’exemple suivant montre un exemple de fonction avec des paramètres standard nommés **Name** et **path**, ainsi qu’un paramètre dynamique facultatif nommé **DP1**.</span><span class="sxs-lookup"><span data-stu-id="1541a-318">The following example shows a sample function with standard parameters named **Name** and **Path**, and an optional dynamic parameter named **DP1**.</span></span> <span data-ttu-id="1541a-319">Le paramètre **DP1** est dans le `PSet1` jeu de paramètres et a un type de `Int32` .</span><span class="sxs-lookup"><span data-stu-id="1541a-319">The **DP1** parameter is in the `PSet1` parameter set and has a type of `Int32`.</span></span>
<span data-ttu-id="1541a-320">Le paramètre **DP1** est disponible dans la `Get-Sample` fonction uniquement lorsque la valeur du paramètre **path** commence par `HKLM:` , ce qui indique qu’il est utilisé dans le `HKEY_LOCAL_MACHINE` lecteur du Registre.</span><span class="sxs-lookup"><span data-stu-id="1541a-320">The **DP1** parameter is available in the `Get-Sample` function only when the value of the **Path** parameter starts with `HKLM:`, indicating that it's being used in the `HKEY_LOCAL_MACHINE` registry drive.</span></span>

```powershell
function Get-Sample {
  [CmdletBinding()]
  Param([String]$Name, [String]$Path)

  DynamicParam
  {
    if ($Path.StartsWith("HKLM:"))
    {
      $attributes = New-Object -Type `
        System.Management.Automation.ParameterAttribute
      $attributes.ParameterSetName = "PSet1"
      $attributes.Mandatory = $false
      $attributeCollection = New-Object `
        -Type System.Collections.ObjectModel.Collection[System.Attribute]
      $attributeCollection.Add($attributes)

      $dynParam1 = New-Object -Type `
        System.Management.Automation.RuntimeDefinedParameter("DP1", [Int32],
          $attributeCollection)

      $paramDictionary = New-Object `
        -Type System.Management.Automation.RuntimeDefinedParameterDictionary
      $paramDictionary.Add("DP1", $dynParam1)
      return $paramDictionary
    }
  }
}
```

<span data-ttu-id="1541a-321">Pour plus d’informations, consultez [RuntimeDefinedParameter](/dotnet/api/system.management.automation.runtimedefinedparameter).</span><span class="sxs-lookup"><span data-stu-id="1541a-321">For more information, see [RuntimeDefinedParameter](/dotnet/api/system.management.automation.runtimedefinedparameter).</span></span>

## <a name="switch-parameters"></a><span data-ttu-id="1541a-322">Paramètres de commutateur</span><span class="sxs-lookup"><span data-stu-id="1541a-322">Switch parameters</span></span>

<span data-ttu-id="1541a-323">Les paramètres de commutateur sont des paramètres sans valeur de paramètre.</span><span class="sxs-lookup"><span data-stu-id="1541a-323">Switch parameters are parameters with no parameter value.</span></span> <span data-ttu-id="1541a-324">Ils sont efficaces uniquement lorsqu’ils sont utilisés et n’ont qu’un seul effet.</span><span class="sxs-lookup"><span data-stu-id="1541a-324">They're effective only when they're used and have only one effect.</span></span>

<span data-ttu-id="1541a-325">Par exemple, le paramètre **Noprofiler** de **powershell.exe** est un paramètre de commutateur.</span><span class="sxs-lookup"><span data-stu-id="1541a-325">For example, the **NoProfile** parameter of **powershell.exe** is a switch parameter.</span></span>

<span data-ttu-id="1541a-326">Pour créer un paramètre de commutateur dans une fonction, spécifiez le `Switch` type dans la définition de paramètre.</span><span class="sxs-lookup"><span data-stu-id="1541a-326">To create a switch parameter in a function, specify the `Switch` type in the parameter definition.</span></span>

<span data-ttu-id="1541a-327">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="1541a-327">For example:</span></span>

```powershell
Param([Switch]<ParameterName>)
```

<span data-ttu-id="1541a-328">Vous pouvez également utiliser une autre méthode :</span><span class="sxs-lookup"><span data-stu-id="1541a-328">Or, you can use an another method:</span></span>

```powershell
Param(
    [Parameter(Mandatory=$false)]
    [Switch]
    $<ParameterName>
)
```

<span data-ttu-id="1541a-329">Les paramètres de commutateur sont faciles à utiliser et sont préférés aux paramètres booléens, qui ont une syntaxe plus difficile.</span><span class="sxs-lookup"><span data-stu-id="1541a-329">Switch parameters are easy to use and are preferred over Boolean parameters, which have a more difficult syntax.</span></span>

<span data-ttu-id="1541a-330">Par exemple, pour utiliser un paramètre de commutateur, l’utilisateur tape le paramètre dans la commande.</span><span class="sxs-lookup"><span data-stu-id="1541a-330">For example, to use a switch parameter, the user types the parameter in the command.</span></span>

`-IncludeAll`

<span data-ttu-id="1541a-331">Pour utiliser un paramètre booléen, l’utilisateur tape le paramètre et une valeur booléenne.</span><span class="sxs-lookup"><span data-stu-id="1541a-331">To use a Boolean parameter, the user types the parameter and a Boolean value.</span></span>

`-IncludeAll:$true`

<span data-ttu-id="1541a-332">Lorsque vous créez des paramètres de commutateur, choisissez le nom du paramètre avec soin.</span><span class="sxs-lookup"><span data-stu-id="1541a-332">When creating switch parameters, choose the parameter name carefully.</span></span> <span data-ttu-id="1541a-333">Assurez-vous que le nom du paramètre communique l’effet du paramètre à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="1541a-333">Be sure that the parameter name communicates the effect of the parameter to the user.</span></span>
<span data-ttu-id="1541a-334">Évitez les termes ambigus, tels que le **filtre** ou le **maximum** qui peut impliquer une valeur, est requis.</span><span class="sxs-lookup"><span data-stu-id="1541a-334">Avoid ambiguous terms, such as **Filter** or **Maximum** that might imply a value is required.</span></span>

## <a name="argumentcompleter-attribute"></a><span data-ttu-id="1541a-335">Attribut ArgumentCompleter</span><span class="sxs-lookup"><span data-stu-id="1541a-335">ArgumentCompleter attribute</span></span>

<span data-ttu-id="1541a-336">L’attribut **ArgumentCompleter** vous permet d’ajouter des valeurs de saisie semi-automatique par tabulation à un paramètre spécifique.</span><span class="sxs-lookup"><span data-stu-id="1541a-336">The **ArgumentCompleter** attribute allows you to add tab completion values to a specific parameter.</span></span> <span data-ttu-id="1541a-337">Un attribut **ArgumentCompleter** doit être défini pour chaque paramètre nécessitant la saisie semi-automatique par tabulation.</span><span class="sxs-lookup"><span data-stu-id="1541a-337">An **ArgumentCompleter** attribute must be defined for each parameter that needs tab completion.</span></span> <span data-ttu-id="1541a-338">Comme pour **DynamicParameters**, les valeurs disponibles sont calculées au moment de l’exécution lorsque l’utilisateur appuie sur la touche <kbd>Tab</kbd> après le nom du paramètre.</span><span class="sxs-lookup"><span data-stu-id="1541a-338">Similar to **DynamicParameters**, the available values are calculated at runtime when the user presses <kbd>Tab</kbd> after the parameter name.</span></span>

<span data-ttu-id="1541a-339">Pour ajouter un attribut **ArgumentCompleter** , vous devez définir un bloc de script qui détermine les valeurs.</span><span class="sxs-lookup"><span data-stu-id="1541a-339">To add an **ArgumentCompleter** attribute, you need to define a script block that determines the values.</span></span> <span data-ttu-id="1541a-340">Le bloc de script doit prendre les paramètres suivants dans l’ordre indiqué ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="1541a-340">The script block must take the following parameters in the order specified below.</span></span> <span data-ttu-id="1541a-341">Les noms du paramètre n’ont pas d’importance, car les valeurs sont fournies à l’emplacement.</span><span class="sxs-lookup"><span data-stu-id="1541a-341">The parameter's names don't matter as the values are provided positionally.</span></span>

<span data-ttu-id="1541a-342">La syntaxe est la suivante :</span><span class="sxs-lookup"><span data-stu-id="1541a-342">The syntax is as follows:</span></span>

```powershell
Param(
    [Parameter(Mandatory)]
    [ArgumentCompleter({
        param ( $commandName,
                $parameterName,
                $wordToComplete,
                $commandAst,
                $fakeBoundParameters )
        # Perform calculation of tab completed values here.
    })]
)
```

### <a name="argumentcompleter-script-block"></a><span data-ttu-id="1541a-343">Bloc de script ArgumentCompleter</span><span class="sxs-lookup"><span data-stu-id="1541a-343">ArgumentCompleter script block</span></span>

<span data-ttu-id="1541a-344">Les paramètres de bloc de script sont définis avec les valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="1541a-344">The script block parameters are set to the following values:</span></span>

- <span data-ttu-id="1541a-345">`$commandName` (Position 0)-ce paramètre est défini sur le nom de la commande pour laquelle le bloc de script fournit la saisie semi-automatique par tabulation.</span><span class="sxs-lookup"><span data-stu-id="1541a-345">`$commandName` (Position 0) - This parameter is set to the name of the command for which the script block is providing tab completion.</span></span>
- <span data-ttu-id="1541a-346">`$parameterName` (Position 1)-ce paramètre est défini sur le paramètre dont la valeur nécessite la saisie semi-automatique par tabulation.</span><span class="sxs-lookup"><span data-stu-id="1541a-346">`$parameterName` (Position 1) - This parameter is set to the parameter whose value requires tab completion.</span></span>
- <span data-ttu-id="1541a-347">`$wordToComplete` (Position 2)-ce paramètre est défini sur la valeur que l’utilisateur a fournie avant d’appuyer sur la touche <kbd>Tab</kbd>. Votre bloc de script doit utiliser cette valeur pour déterminer les valeurs de saisie semi-automatique de l’onglet.</span><span class="sxs-lookup"><span data-stu-id="1541a-347">`$wordToComplete` (Position 2) - This parameter is set to value the user has provided before they pressed <kbd>Tab</kbd>. Your script block should use this value to determine tab completion values.</span></span>
- <span data-ttu-id="1541a-348">`$commandAst` (Position 3)-ce paramètre est défini sur l’arborescence de syntaxe abstraite (AST) pour la ligne d’entrée actuelle.</span><span class="sxs-lookup"><span data-stu-id="1541a-348">`$commandAst` (Position 3) - This parameter is set to the Abstract Syntax Tree (AST) for the current input line.</span></span> <span data-ttu-id="1541a-349">Pour plus d’informations, consultez la [classe AST](/dotnet/api/system.management.automation.language.ast).</span><span class="sxs-lookup"><span data-stu-id="1541a-349">For more information, see [Ast Class](/dotnet/api/system.management.automation.language.ast).</span></span>
- <span data-ttu-id="1541a-350">`$fakeBoundParameters` (Position 4)-ce paramètre est défini sur une valeur Hashtable contenant le `$PSBoundParameters` pour l’applet de commande, avant que l’utilisateur ait appuyé sur la touche <kbd>Tab</kbd>. Pour plus d’informations, consultez [about_Automatic_Variables](about_Automatic_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="1541a-350">`$fakeBoundParameters` (Position 4) - This parameter is set to a hashtable containing the `$PSBoundParameters` for the cmdlet, before the user pressed <kbd>Tab</kbd>. For more information, see [about_Automatic_Variables](about_Automatic_Variables.md).</span></span>

<span data-ttu-id="1541a-351">Le bloc de script **ArgumentCompleter** doit dérouler les valeurs à l’aide du pipeline, tel que `ForEach-Object` , `Where-Object` ou une autre méthode appropriée.</span><span class="sxs-lookup"><span data-stu-id="1541a-351">The **ArgumentCompleter** script block must unroll the values using the pipeline, such as `ForEach-Object`, `Where-Object`, or another suitable method.</span></span>
<span data-ttu-id="1541a-352">Le retour d’un tableau de valeurs amène PowerShell à traiter l’intégralité du tableau comme **une** valeur de saisie semi-automatique de tabulation.</span><span class="sxs-lookup"><span data-stu-id="1541a-352">Returning an array of values causes PowerShell to treat the entire array as **one** tab completion value.</span></span>

<span data-ttu-id="1541a-353">L’exemple suivant ajoute la saisie semi-automatique via la touche Tab au paramètre **value** .</span><span class="sxs-lookup"><span data-stu-id="1541a-353">The following example adds tab completion to the **Value** parameter.</span></span> <span data-ttu-id="1541a-354">Si seul le paramètre **value** est spécifié, toutes les valeurs possibles, ou arguments, pour **value** sont affichées.</span><span class="sxs-lookup"><span data-stu-id="1541a-354">If only the **Value** parameter is specified, all possible values, or arguments, for **Value** are displayed.</span></span> <span data-ttu-id="1541a-355">Lorsque le paramètre de **type** est spécifié, le paramètre de **valeur** affiche uniquement les valeurs possibles pour ce type.</span><span class="sxs-lookup"><span data-stu-id="1541a-355">When the **Type** parameter is specified, the **Value** parameter only displays the possible values for that type.</span></span>

<span data-ttu-id="1541a-356">En outre, l' `-like` opérateur s’assure que si l’utilisateur tape la commande suivante et utilise la saisie semi-automatique via la <kbd>touche Tab</kbd> , seul **Apple** est retourné.</span><span class="sxs-lookup"><span data-stu-id="1541a-356">In addition, the `-like` operator ensures that if the user types the following command and uses <kbd>Tab</kbd> completion, only **Apple** is returned.</span></span>

`Test-ArgumentCompleter -Type Fruits -Value A`

```powershell
function Test-ArgumentCompleter {
[CmdletBinding()]
 param (
        [Parameter(Mandatory=$true)]
        [ValidateSet('Fruits', 'Vegetables')]
        $Type,
        [Parameter(Mandatory=$true)]
        [ArgumentCompleter( {
            param ( $commandName,
                    $parameterName,
                    $wordToComplete,
                    $commandAst,
                    $fakeBoundParameters )

            $possibleValues = @{
                Fruits = @('Apple', 'Orange', 'Banana')
                Vegetables = @('Tomato', 'Squash', 'Corn')
            }
            if ($fakeBoundParameters.ContainsKey('Type'))
            {
                $possibleValues[$fakeBoundParameters.Type] | Where-Object {
                    $_ -like "$wordToComplete*"
                }
            }
            else
            {
                $possibleValues.Values | ForEach-Object {$_}
            }
        } )]
        $Value
      )
}
```

## <a name="see-also"></a><span data-ttu-id="1541a-357">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1541a-357">See also</span></span>

[<span data-ttu-id="1541a-358">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="1541a-358">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="1541a-359">about_Functions</span><span class="sxs-lookup"><span data-stu-id="1541a-359">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="1541a-360">about_Functions_Advanced</span><span class="sxs-lookup"><span data-stu-id="1541a-360">about_Functions_Advanced</span></span>](about_Functions_Advanced.md)

[<span data-ttu-id="1541a-361">about_Functions_Advanced_Methods</span><span class="sxs-lookup"><span data-stu-id="1541a-361">about_Functions_Advanced_Methods</span></span>](about_Functions_Advanced_Methods.md)

[<span data-ttu-id="1541a-362">about_Functions_CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="1541a-362">about_Functions_CmdletBindingAttribute</span></span>](about_Functions_CmdletBindingAttribute.md)

[<span data-ttu-id="1541a-363">about_Functions_OutputTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="1541a-363">about_Functions_OutputTypeAttribute</span></span>](about_Functions_OutputTypeAttribute.md)
