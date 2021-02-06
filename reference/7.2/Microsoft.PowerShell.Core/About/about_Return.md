---
description: Quitte l'étendue active (fonction, script ou bloc de script).
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_return?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Return
ms.openlocfilehash: 032f3c694096e11e2800be941eb76b1f442b5088
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595747"
---
# <a name="about-return"></a><span data-ttu-id="41655-103">À propos du retour</span><span class="sxs-lookup"><span data-stu-id="41655-103">About Return</span></span>

## <a name="short-description"></a><span data-ttu-id="41655-104">Description courte</span><span class="sxs-lookup"><span data-stu-id="41655-104">Short description</span></span>

<span data-ttu-id="41655-105">Quitte l'étendue active (fonction, script ou bloc de script).</span><span class="sxs-lookup"><span data-stu-id="41655-105">Exits the current scope, which can be a function, script, or script block.</span></span>

## <a name="long-description"></a><span data-ttu-id="41655-106">Description longue</span><span class="sxs-lookup"><span data-stu-id="41655-106">Long description</span></span>

<span data-ttu-id="41655-107">Le `return` mot clé quitte une fonction, un script ou un bloc de script.</span><span class="sxs-lookup"><span data-stu-id="41655-107">The `return` keyword exits a function, script, or script block.</span></span> <span data-ttu-id="41655-108">Il peut être utilisé pour quitter une étendue à un point spécifique, pour retourner une valeur ou pour indiquer que la fin de l’étendue a été atteinte.</span><span class="sxs-lookup"><span data-stu-id="41655-108">It can be used to exit a scope at a specific point, to return a value, or to indicate that the end of the scope has been reached.</span></span>

<span data-ttu-id="41655-109">Les utilisateurs qui sont familiarisés avec les langages tels que C ou C \# peuvent souhaiter utiliser le `return` mot clé pour rendre une portée explicite.</span><span class="sxs-lookup"><span data-stu-id="41655-109">Users who are familiar with languages like C or C\# might want to use the `return` keyword to make the logic of leaving a scope explicit.</span></span>

<span data-ttu-id="41655-110">Dans PowerShell, les résultats de chaque instruction sont retournés en tant que sortie, même si aucune instruction ne contient le mot clé return.</span><span class="sxs-lookup"><span data-stu-id="41655-110">In PowerShell, the results of each statement are returned as output, even without a statement that contains the Return keyword.</span></span> <span data-ttu-id="41655-111">Les langages tels que C ou C \# retournent uniquement la valeur ou les valeurs spécifiées par le `return` mot clé.</span><span class="sxs-lookup"><span data-stu-id="41655-111">Languages like C or C\# return only the value or values that are specified by the `return` keyword.</span></span>

> [!NOTE]
> <span data-ttu-id="41655-112">À compter de PowerShell 5,0, PowerShell a ajouté le langage pour la définition des classes, à l’aide de la syntaxe formelle.</span><span class="sxs-lookup"><span data-stu-id="41655-112">Beginning in PowerShell 5.0, PowerShell added language for defining classes, by using formal syntax.</span></span>  <span data-ttu-id="41655-113">Dans le contexte d’une classe PowerShell, rien n’est généré à partir d’une méthode, à l’exception de ce que vous spécifiez à l’aide d’une `return` instruction.</span><span class="sxs-lookup"><span data-stu-id="41655-113">In the context of a PowerShell class, nothing is output from a method except what you specify using a `return` statement.</span></span> <span data-ttu-id="41655-114">Vous pouvez en savoir plus sur les classes PowerShell dans [about_Classes](about_Classes.md).</span><span class="sxs-lookup"><span data-stu-id="41655-114">You can read more about PowerShell classes in [about_Classes](about_Classes.md).</span></span>

### <a name="syntax"></a><span data-ttu-id="41655-115">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="41655-115">Syntax</span></span>

<span data-ttu-id="41655-116">La syntaxe du `return` mot clé est la suivante :</span><span class="sxs-lookup"><span data-stu-id="41655-116">The syntax for the `return` keyword is as follows:</span></span>

```
return [<expression>]
```

<span data-ttu-id="41655-117">Le `return` mot clé peut apparaître seul, ou il peut être suivi d’une valeur ou d’une expression, comme suit :</span><span class="sxs-lookup"><span data-stu-id="41655-117">The `return` keyword can appear alone, or it can be followed by a value or expression, as follows:</span></span>

```powershell
return
return $a
return (2 + $a)
```

### <a name="examples"></a><span data-ttu-id="41655-118">Exemples</span><span class="sxs-lookup"><span data-stu-id="41655-118">Examples</span></span>

<span data-ttu-id="41655-119">L’exemple suivant utilise le `return` mot clé pour quitter une fonction à un point spécifique si une condition est remplie.</span><span class="sxs-lookup"><span data-stu-id="41655-119">The following example uses the `return` keyword to exit a function at a specific point if a conditional is met.</span></span> <span data-ttu-id="41655-120">Les nombres impairs ne sont pas multipliés, car l’instruction return se termine avant que cette instruction puisse s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="41655-120">Odd numbers are not multiplied because the return statement exits before that statement can execute.</span></span>

```powershell
function MultiplyEven
{
    param($number)

    if ($number % 2) { return "$number is not even" }
    $number * 2
}

1..10 | ForEach-Object {MultiplyEven -Number $_}
```

```output
1 is not even
4
3 is not even
8
5 is not even
12
7 is not even
16
9 is not even
20
```

<span data-ttu-id="41655-121">Dans PowerShell, les valeurs peuvent être retournées même si le `return` mot clé n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="41655-121">In PowerShell, values can be returned even if the `return` keyword is not used.</span></span>
<span data-ttu-id="41655-122">Les résultats de chaque instruction sont retournés.</span><span class="sxs-lookup"><span data-stu-id="41655-122">The results of each statement are returned.</span></span> <span data-ttu-id="41655-123">Par exemple, les instructions suivantes retournent la valeur de la `$a` variable :</span><span class="sxs-lookup"><span data-stu-id="41655-123">For example, the following statements return the value of the `$a` variable:</span></span>

```powershell
$a
return
```

<span data-ttu-id="41655-124">L’instruction suivante retourne également la valeur de `$a` :</span><span class="sxs-lookup"><span data-stu-id="41655-124">The following statement also returns the value of `$a`:</span></span>

```powershell
return $a
```

<span data-ttu-id="41655-125">L’exemple suivant comprend une instruction destinée à permettre à l’utilisateur de savoir que la fonction effectue un calcul :</span><span class="sxs-lookup"><span data-stu-id="41655-125">The following example includes a statement intended to let the user know that the function is performing a calculation:</span></span>

```powershell
function calculation {
    param ($value)

    "Please wait. Working on calculation..."
    $value += 73
    return $value
}

$a = calculation 14
```

<span data-ttu-id="41655-126">«Veuillez patienter.</span><span class="sxs-lookup"><span data-stu-id="41655-126">The "Please wait.</span></span> <span data-ttu-id="41655-127">Utilisation du calcul...» la chaîne n’est pas affichée.</span><span class="sxs-lookup"><span data-stu-id="41655-127">Working on calculation..." string is not displayed.</span></span> <span data-ttu-id="41655-128">Au lieu de cela, elle est assignée à la `$a` variable, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="41655-128">Instead, it is assigned to the `$a` variable, as in the following example:</span></span>

```
PS> $a
Please wait. Working on calculation...
87
```

<span data-ttu-id="41655-129">La chaîne d’information et le résultat du calcul sont retournés par la fonction et assignés à la `$a` variable.</span><span class="sxs-lookup"><span data-stu-id="41655-129">Both the informational string and the result of the calculation are returned by the function and assigned to the `$a` variable.</span></span>

<span data-ttu-id="41655-130">Si vous souhaitez afficher un message dans votre fonction, à compter de PowerShell 5,0, vous pouvez utiliser le `Information` flux.</span><span class="sxs-lookup"><span data-stu-id="41655-130">If you would like to display a message within your function, beginning in PowerShell 5.0, you can use the `Information` stream.</span></span> <span data-ttu-id="41655-131">Le code ci-dessous corrige l’exemple ci-dessus à l’aide de l' `Write-Information` applet de commande avec un `InformationAction` de **continue**.</span><span class="sxs-lookup"><span data-stu-id="41655-131">The code below corrects the above example using the `Write-Information` cmdlet with a `InformationAction` of **Continue**.</span></span>

```powershell
function calculation {
    param ($value)

    Write-Information "Please wait. Working on calculation..." -InformationAction Continue
    $value += 73
    return $value
}

$a = calculation 14
```

```output
Please wait. Working on calculation...
C:\PS> $a
87
```

### <a name="return-values-and-the-pipeline"></a><span data-ttu-id="41655-132">Valeurs de retour et pipeline</span><span class="sxs-lookup"><span data-stu-id="41655-132">Return values and the Pipeline</span></span>

<span data-ttu-id="41655-133">Lorsque vous retournez une collection à partir d’un bloc de script ou d’une fonction, PowerShell dérouler automatiquement les membres et les transmet un par un à un autre via le pipeline.</span><span class="sxs-lookup"><span data-stu-id="41655-133">When you return a collection from your script block or function, PowerShell automatically unrolls the members and passes them one at a time through the pipeline.</span></span> <span data-ttu-id="41655-134">Cela est dû au traitement « un à la fois » de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="41655-134">This is due to PowerShell's one-at-a-time processing.</span></span> <span data-ttu-id="41655-135">Pour plus d’informations, consultez [about_Pipelines](about_pipelines.md).</span><span class="sxs-lookup"><span data-stu-id="41655-135">For more information, see [about_pipelines](about_pipelines.md).</span></span>

<span data-ttu-id="41655-136">Ce concept est illustré par l’exemple de fonction suivant qui retourne un tableau de nombres.</span><span class="sxs-lookup"><span data-stu-id="41655-136">This concept is illustrated by the following sample function that returns an array of numbers.</span></span> <span data-ttu-id="41655-137">La sortie de la fonction est dirigée vers l' `Measure-Object` applet de commande qui compte le nombre d’objets dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="41655-137">The output from the function is piped to the `Measure-Object` cmdlet which counts the number of objects in the pipeline.</span></span>

```powershell
function Test-Return
{
    $array = 1,2,3
    return $array
}
Test-Return | Measure-Object
```

```Output
Count    : 3
Average  :
Sum      :
Maximum  :
Minimum  :
Property :
```

<span data-ttu-id="41655-138">Pour forcer un bloc de script ou une fonction à retourner une collection en tant qu’objet unique au pipeline, utilisez l’une des deux méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="41655-138">To force a script block or function to return collection as a single object to the pipeline, use one of the following two methods:</span></span>

- <span data-ttu-id="41655-139">Expression de tableau unaire</span><span class="sxs-lookup"><span data-stu-id="41655-139">Unary array expression</span></span>

  <span data-ttu-id="41655-140">À l’aide d’une expression unaire, vous pouvez envoyer votre valeur de retour dans le pipeline en tant qu’objet unique, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="41655-140">Utilizing a unary expression you can send your return value down the pipeline as a single object as illustrated by the following example.</span></span>

  ```powershell
  function Test-Return
  {
      $array = 1,2,3
      return (, $array)
  }
  Test-Return | Measure-Object
  ```

  ```Output
  Count    : 1
  Average  :
  Sum      :
  Maximum  :
  Minimum  :
  Property :
  ```

- <span data-ttu-id="41655-141">`Write-Output` avec le paramètre **noenumerate** .</span><span class="sxs-lookup"><span data-stu-id="41655-141">`Write-Output` with **NoEnumerate** parameter.</span></span>

  <span data-ttu-id="41655-142">Vous pouvez également utiliser l' `Write-Output` applet de commande avec le paramètre **noenum** .</span><span class="sxs-lookup"><span data-stu-id="41655-142">You can also use the `Write-Output` cmdlet with the **NoEnumerate** parameter.</span></span> <span data-ttu-id="41655-143">L’exemple ci-dessous utilise l' `Measure-Object` applet de commande pour compter les objets envoyés au pipeline à partir de l’exemple de fonction par le `return` mot clé.</span><span class="sxs-lookup"><span data-stu-id="41655-143">The example below uses the `Measure-Object` cmdlet to count the objects sent to the pipeline from the sample function by the `return` keyword.</span></span>

  ```powershell
  function Test-Return
  {
      $array = 1, 2, 3
      return Write-Output -NoEnumerate $array
  }

  Test-Return | Measure-Object
  ```

  ```Output
  Count    : 1
  Average  :
  Sum      :
  Maximum  :
  Minimum  :
  Property :
  ```

## <a name="see-also"></a><span data-ttu-id="41655-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="41655-144">See also</span></span>

[<span data-ttu-id="41655-145">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="41655-145">about_Language_Keywords</span></span>](about_Language_Keywords.md)

[<span data-ttu-id="41655-146">about_Functions</span><span class="sxs-lookup"><span data-stu-id="41655-146">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="41655-147">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="41655-147">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="41655-148">À propos des classes</span><span class="sxs-lookup"><span data-stu-id="41655-148">about_Classes</span></span>](about_Classes.md)

[<span data-ttu-id="41655-149">Write-Information</span><span class="sxs-lookup"><span data-stu-id="41655-149">Write-Information</span></span>](xref:Microsoft.PowerShell.Utility.Write-Information)

[<span data-ttu-id="41655-150">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="41655-150">about_Script_Blocks</span></span>](about_Script_Blocks.md)

