---
description: Décrit comment créer et utiliser des fonctions dans PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 2/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions
ms.openlocfilehash: f033bc36bf67a9d01e3f238645b83df7d75c6963
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207661"
---
# <a name="about-functions"></a><span data-ttu-id="225b7-104">À propos des fonctions</span><span class="sxs-lookup"><span data-stu-id="225b7-104">About Functions</span></span>

## <a name="short-description"></a><span data-ttu-id="225b7-105">Description courte</span><span class="sxs-lookup"><span data-stu-id="225b7-105">Short description</span></span>

<span data-ttu-id="225b7-106">Décrit comment créer et utiliser des fonctions dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="225b7-106">Describes how to create and use functions in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="225b7-107">Description longue</span><span class="sxs-lookup"><span data-stu-id="225b7-107">Long description</span></span>

<span data-ttu-id="225b7-108">Une fonction est une liste d’instructions PowerShell qui porte un nom que vous attribuez.</span><span class="sxs-lookup"><span data-stu-id="225b7-108">A function is a list of PowerShell statements that has a name that you assign.</span></span> <span data-ttu-id="225b7-109">Lorsque vous exécutez une fonction, vous tapez le nom de la fonction.</span><span class="sxs-lookup"><span data-stu-id="225b7-109">When you run a function, you type the function name.</span></span> <span data-ttu-id="225b7-110">Les instructions de la liste sont exécutées comme si vous les aviez tapées à l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="225b7-110">The statements in the list run as if you had typed them at the command prompt.</span></span>

<span data-ttu-id="225b7-111">Les fonctions peuvent être aussi simples que :</span><span class="sxs-lookup"><span data-stu-id="225b7-111">Functions can be as simple as:</span></span>

```powershell
function Get-PowerShellProcess { Get-Process PowerShell }
```

<span data-ttu-id="225b7-112">Une fonction peut également être aussi complexe qu’une applet de commande ou un programme d’application.</span><span class="sxs-lookup"><span data-stu-id="225b7-112">A function can also be as complex as a cmdlet or an application program.</span></span>

<span data-ttu-id="225b7-113">Comme les applets de commande, les fonctions peuvent avoir des paramètres.</span><span class="sxs-lookup"><span data-stu-id="225b7-113">Like cmdlets, functions can have parameters.</span></span> <span data-ttu-id="225b7-114">Les paramètres peuvent être des paramètres nommés, positionnels, de commutateur ou dynamiques.</span><span class="sxs-lookup"><span data-stu-id="225b7-114">The parameters can be named, positional, switch, or dynamic parameters.</span></span> <span data-ttu-id="225b7-115">Les paramètres de fonction peuvent être lus à partir de la ligne de commande ou du pipeline.</span><span class="sxs-lookup"><span data-stu-id="225b7-115">Function parameters can be read from the command line or from the pipeline.</span></span>

<span data-ttu-id="225b7-116">Les fonctions peuvent retourner des valeurs qui peuvent être affichées, affectées à des variables ou passées à d’autres fonctions ou applets de commande.</span><span class="sxs-lookup"><span data-stu-id="225b7-116">Functions can return values that can be displayed, assigned to variables, or passed to other functions or cmdlets.</span></span> <span data-ttu-id="225b7-117">Vous pouvez également spécifier une valeur de retour à l’aide du `return` mot clé.</span><span class="sxs-lookup"><span data-stu-id="225b7-117">You can also specify a return value using the `return` keyword.</span></span> <span data-ttu-id="225b7-118">Le `return` mot clé n’affecte pas ou ne supprime pas la sortie retournée par votre fonction.</span><span class="sxs-lookup"><span data-stu-id="225b7-118">The `return` keyword does not affect or suppress other output returned from your function.</span></span> <span data-ttu-id="225b7-119">Toutefois, le `return` mot clé quitte la fonction à cette ligne.</span><span class="sxs-lookup"><span data-stu-id="225b7-119">However, the `return` keyword exits the function at that line.</span></span> <span data-ttu-id="225b7-120">Pour plus d’informations, consultez [about_Return](about_Return.md).</span><span class="sxs-lookup"><span data-stu-id="225b7-120">For more information, see [about_Return](about_Return.md).</span></span>

<span data-ttu-id="225b7-121">La liste des instructions de la fonction peut contenir différents types de listes d’instructions avec les mots clés `Begin` , `Process` et `End` .</span><span class="sxs-lookup"><span data-stu-id="225b7-121">The function's statement list can contain different types of statement lists with the keywords `Begin`, `Process`, and `End`.</span></span> <span data-ttu-id="225b7-122">Ces instructions répertorient différemment l’entrée du pipeline.</span><span class="sxs-lookup"><span data-stu-id="225b7-122">These statement lists handle input from the pipeline differently.</span></span>

<span data-ttu-id="225b7-123">Un filtre est un type spécial de fonction qui utilise le `Filter` mot clé.</span><span class="sxs-lookup"><span data-stu-id="225b7-123">A filter is a special kind of function that uses the `Filter` keyword.</span></span>

<span data-ttu-id="225b7-124">Les fonctions peuvent également agir comme des applets de commande.</span><span class="sxs-lookup"><span data-stu-id="225b7-124">Functions can also act like cmdlets.</span></span> <span data-ttu-id="225b7-125">Vous pouvez créer une fonction qui fonctionne comme une applet de commande sans utiliser la `C#` programmation.</span><span class="sxs-lookup"><span data-stu-id="225b7-125">You can create a function that works just like a cmdlet without using `C#` programming.</span></span> <span data-ttu-id="225b7-126">Pour plus d’informations, consultez [about_Functions_Advanced](about_Functions_Advanced.md).</span><span class="sxs-lookup"><span data-stu-id="225b7-126">For more information, see [about_Functions_Advanced](about_Functions_Advanced.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="225b7-127">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="225b7-127">Syntax</span></span>

<span data-ttu-id="225b7-128">Voici la syntaxe d’une fonction :</span><span class="sxs-lookup"><span data-stu-id="225b7-128">The following is the syntax for a function:</span></span>

```
function [<scope:>]<name> [([type]$parameter1[,[type]$parameter2])]
{
  param([type]$parameter1 [,[type]$parameter2])
  dynamicparam {<statement list>}
  begin {<statement list>}
  process {<statement list>}
  end {<statement list>}
}
```

<span data-ttu-id="225b7-129">Une fonction comprend les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="225b7-129">A function includes the following items:</span></span>

- <span data-ttu-id="225b7-130">`Function`Mot clé</span><span class="sxs-lookup"><span data-stu-id="225b7-130">A `Function` keyword</span></span>
- <span data-ttu-id="225b7-131">Une étendue (facultatif)</span><span class="sxs-lookup"><span data-stu-id="225b7-131">A scope (optional)</span></span>
- <span data-ttu-id="225b7-132">Un nom que vous sélectionnez</span><span class="sxs-lookup"><span data-stu-id="225b7-132">A name that you select</span></span>
- <span data-ttu-id="225b7-133">N’importe quel nombre de paramètres nommés (facultatif)</span><span class="sxs-lookup"><span data-stu-id="225b7-133">Any number of named parameters (optional)</span></span>
- <span data-ttu-id="225b7-134">Une ou plusieurs commandes PowerShell placées entre accolades `{}`</span><span class="sxs-lookup"><span data-stu-id="225b7-134">One or more PowerShell commands enclosed in braces `{}`</span></span>

<span data-ttu-id="225b7-135">Pour plus d’informations sur le `Dynamicparam` mot clé et les paramètres dynamiques dans les fonctions, consultez [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).</span><span class="sxs-lookup"><span data-stu-id="225b7-135">For more information about the `Dynamicparam` keyword and dynamic parameters in functions, see [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).</span></span>

## <a name="simple-functions"></a><span data-ttu-id="225b7-136">Fonctions simples</span><span class="sxs-lookup"><span data-stu-id="225b7-136">Simple Functions</span></span>

<span data-ttu-id="225b7-137">Les fonctions n’ont pas besoin d’être compliquées pour être utiles.</span><span class="sxs-lookup"><span data-stu-id="225b7-137">Functions do not have to be complicated to be useful.</span></span> <span data-ttu-id="225b7-138">Les fonctions les plus simples ont le format suivant :</span><span class="sxs-lookup"><span data-stu-id="225b7-138">The simplest functions have the following format:</span></span>

```
function <function-name> {statements}
```

<span data-ttu-id="225b7-139">Par exemple, la fonction suivante démarre PowerShell avec l’option Exécuter en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="225b7-139">For example, the following function starts PowerShell with the Run as Administrator option.</span></span>

```powershell
function Start-PSAdmin {Start-Process PowerShell -Verb RunAs}
```

<span data-ttu-id="225b7-140">Pour utiliser la fonction, tapez : `Start-PSAdmin`</span><span class="sxs-lookup"><span data-stu-id="225b7-140">To use the function, type: `Start-PSAdmin`</span></span>

<span data-ttu-id="225b7-141">Pour ajouter des instructions à la fonction, tapez chaque instruction sur une ligne distincte ou utilisez un point-virgule `;` pour séparer les instructions.</span><span class="sxs-lookup"><span data-stu-id="225b7-141">To add statements to the function, type each statement on a separate line, or use a semi-colon `;` to separate the statements.</span></span>

<span data-ttu-id="225b7-142">Par exemple, la fonction suivante recherche tous les `.jpg` fichiers dans les répertoires de l’utilisateur actuel qui ont été modifiés après la date de début.</span><span class="sxs-lookup"><span data-stu-id="225b7-142">For example, the following function finds all `.jpg` files in the current user's directories that were changed after the start date.</span></span>

```powershell
function Get-NewPix
{
  $start = Get-Date -Month 1 -Day 1 -Year 2010
  $allpix = Get-ChildItem -Path $env:UserProfile\*.jpg -Recurse
  $allpix | Where-Object {$_.LastWriteTime -gt $Start}
}
```

<span data-ttu-id="225b7-143">Vous pouvez créer une boîte à outils de petites fonctions utiles.</span><span class="sxs-lookup"><span data-stu-id="225b7-143">You can create a toolbox of useful small functions.</span></span> <span data-ttu-id="225b7-144">Ajoutez ces fonctions à votre profil PowerShell, comme décrit dans [about_Profiles](about_Profiles.md) et versions ultérieures dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="225b7-144">Add these functions to your PowerShell profile, as described in [about_Profiles](about_Profiles.md) and later in this topic.</span></span>

## <a name="function-names"></a><span data-ttu-id="225b7-145">Noms de fonction</span><span class="sxs-lookup"><span data-stu-id="225b7-145">Function Names</span></span>

<span data-ttu-id="225b7-146">Vous pouvez assigner n’importe quel nom à une fonction, mais les fonctions que vous partagez avec d’autres utilisateurs doivent suivre les règles d’affectation de noms qui ont été établies pour toutes les commandes PowerShell.</span><span class="sxs-lookup"><span data-stu-id="225b7-146">You can assign any name to a function, but functions that you share with others should follow the naming rules that have been established for all PowerShell commands.</span></span>

<span data-ttu-id="225b7-147">Les noms de fonctions doivent être constitués d’une paire verbe-substantif dans laquelle le verbe identifie l’action exécutée par la fonction et le nom identifie l’élément sur lequel l’applet de commande exécute son action.</span><span class="sxs-lookup"><span data-stu-id="225b7-147">Functions names should consist of a verb-noun pair in which the verb identifies the action that the function performs and the noun identifies the item on which the cmdlet performs its action.</span></span>

<span data-ttu-id="225b7-148">Les fonctions doivent utiliser les verbes standard qui ont été approuvés pour toutes les commandes PowerShell.</span><span class="sxs-lookup"><span data-stu-id="225b7-148">Functions should use the standard verbs that have been approved for all PowerShell commands.</span></span> <span data-ttu-id="225b7-149">Ces verbes nous aident à faire en sorte que les noms de commande restent simples, cohérents et faciles à comprendre pour les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="225b7-149">These verbs help us to keep our command names simple, consistent, and easy for users to understand.</span></span>

<span data-ttu-id="225b7-150">Pour plus d’informations sur les verbes PowerShell standard, consultez [verbes approuvés](/powershell/scripting/developer/cmdlet/approved-verbs-for-windows-powershell-commands) dans le Microsoft docs.</span><span class="sxs-lookup"><span data-stu-id="225b7-150">For more information about the standard PowerShell verbs, see [Approved Verbs](/powershell/scripting/developer/cmdlet/approved-verbs-for-windows-powershell-commands) in the Microsoft Docs.</span></span>

## <a name="functions-with-parameters"></a><span data-ttu-id="225b7-151">Fonctions avec paramètres</span><span class="sxs-lookup"><span data-stu-id="225b7-151">Functions with Parameters</span></span>

<span data-ttu-id="225b7-152">Vous pouvez utiliser des paramètres avec des fonctions, y compris des paramètres nommés, des paramètres positionnels, des paramètres de commutateur et des paramètres dynamiques.</span><span class="sxs-lookup"><span data-stu-id="225b7-152">You can use parameters with functions, including named parameters, positional parameters, switch parameters, and dynamic parameters.</span></span> <span data-ttu-id="225b7-153">Pour plus d’informations sur les paramètres dynamiques dans les fonctions, consultez [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).</span><span class="sxs-lookup"><span data-stu-id="225b7-153">For more information about dynamic parameters in functions, see [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).</span></span>

### <a name="named-parameters"></a><span data-ttu-id="225b7-154">paramètres nommés</span><span class="sxs-lookup"><span data-stu-id="225b7-154">Named Parameters</span></span>

<span data-ttu-id="225b7-155">Vous pouvez définir n’importe quel nombre de paramètres nommés.</span><span class="sxs-lookup"><span data-stu-id="225b7-155">You can define any number of named parameters.</span></span> <span data-ttu-id="225b7-156">Vous pouvez inclure une valeur par défaut pour les paramètres nommés, comme décrit plus loin dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="225b7-156">You can include a default value for named parameters, as described later in this topic.</span></span>

<span data-ttu-id="225b7-157">Vous pouvez définir des paramètres à l’intérieur des accolades à l’aide du `Param` mot clé, comme indiqué dans l’exemple de syntaxe suivant :</span><span class="sxs-lookup"><span data-stu-id="225b7-157">You can define parameters inside the braces using the `Param` keyword, as shown in the following sample syntax:</span></span>

```
function <name> {
  param ([type]$parameter1[,[type]$parameter2])
  <statement list>
}
```

<span data-ttu-id="225b7-158">Vous pouvez également définir des paramètres en dehors des accolades sans le `Param` mot clé, comme indiqué dans l’exemple de syntaxe suivant :</span><span class="sxs-lookup"><span data-stu-id="225b7-158">You can also define parameters outside the braces without the `Param` keyword, as shown in the following sample syntax:</span></span>

```powershell
function <name> [([type]$parameter1[,[type]$parameter2])] {
  <statement list>
}
```

<span data-ttu-id="225b7-159">Voici un exemple de cette syntaxe alternative.</span><span class="sxs-lookup"><span data-stu-id="225b7-159">Below is an example of this alternative syntax.</span></span>

```powershell
Function Add-Numbers($one, $two) {
    $one + $two
}
```

<span data-ttu-id="225b7-160">Bien que la première méthode soit préférée, il n’y a aucune différence entre ces deux méthodes.</span><span class="sxs-lookup"><span data-stu-id="225b7-160">While the first method is preferred, there is no difference between these two methods.</span></span>

<span data-ttu-id="225b7-161">Lorsque vous exécutez la fonction, la valeur que vous fournissez pour un paramètre est assignée à une variable qui contient le nom du paramètre.</span><span class="sxs-lookup"><span data-stu-id="225b7-161">When you run the function, the value you supply for a parameter is assigned to a variable that contains the parameter name.</span></span> <span data-ttu-id="225b7-162">La valeur de cette variable peut être utilisée dans la fonction.</span><span class="sxs-lookup"><span data-stu-id="225b7-162">The value of that variable can be used in the function.</span></span>

<span data-ttu-id="225b7-163">L’exemple suivant est une fonction appelée `Get-SmallFiles` .</span><span class="sxs-lookup"><span data-stu-id="225b7-163">The following example is a function called `Get-SmallFiles`.</span></span> <span data-ttu-id="225b7-164">Cette fonction a un `$Size` paramètre.</span><span class="sxs-lookup"><span data-stu-id="225b7-164">This function has a `$Size` parameter.</span></span> <span data-ttu-id="225b7-165">La fonction affiche tous les fichiers qui sont plus petits que la valeur du `$Size` paramètre et exclut les répertoires :</span><span class="sxs-lookup"><span data-stu-id="225b7-165">The function displays all the files that are smaller than the value of the `$Size` parameter, and it excludes directories:</span></span>

```powershell
function Get-SmallFiles {
  Param($Size)
  Get-ChildItem $HOME | Where-Object {
    $_.Length -lt $Size -and !$_.PSIsContainer
  }
}
```

<span data-ttu-id="225b7-166">Dans la fonction, vous pouvez utiliser la `$Size` variable, qui est le nom défini pour le paramètre.</span><span class="sxs-lookup"><span data-stu-id="225b7-166">In the function, you can use the `$Size` variable, which is the name defined for the parameter.</span></span>

<span data-ttu-id="225b7-167">Pour utiliser cette fonction, tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="225b7-167">To use this function, type the following command:</span></span>

```powershell
Get-SmallFiles -Size 50
```

<span data-ttu-id="225b7-168">Vous pouvez également entrer une valeur pour un paramètre nommé sans le nom du paramètre.</span><span class="sxs-lookup"><span data-stu-id="225b7-168">You can also enter a value for a named parameter without the parameter name.</span></span>
<span data-ttu-id="225b7-169">Par exemple, la commande suivante donne le même résultat qu’une commande qui nomme le paramètre **Size** :</span><span class="sxs-lookup"><span data-stu-id="225b7-169">For example, the following command gives the same result as a command that names the **Size** parameter:</span></span>

```powershell
Get-SmallFiles 50
```

<span data-ttu-id="225b7-170">Pour définir une valeur par défaut pour un paramètre, tapez un signe égal et la valeur après le nom du paramètre, comme indiqué dans la variation suivante de l' `Get-SmallFiles` exemple :</span><span class="sxs-lookup"><span data-stu-id="225b7-170">To define a default value for a parameter, type an equal sign and the value after the parameter name, as shown in the following variation of the `Get-SmallFiles` example:</span></span>

```powershell
function Get-SmallFiles ($Size = 100) {
  Get-ChildItem $HOME | Where-Object {
    $_.Length -lt $Size -and !$_.PSIsContainer
  }
}
```

<span data-ttu-id="225b7-171">Si vous tapez `Get-SmallFiles` sans valeur, la fonction assigne 100 à `$size` .</span><span class="sxs-lookup"><span data-stu-id="225b7-171">If you type `Get-SmallFiles` without a value, the function assigns 100 to `$size`.</span></span> <span data-ttu-id="225b7-172">Si vous fournissez une valeur, la fonction utilise cette valeur.</span><span class="sxs-lookup"><span data-stu-id="225b7-172">If you provide a value, the function uses that value.</span></span>

<span data-ttu-id="225b7-173">Si vous le souhaitez, vous pouvez fournir une courte chaîne d’aide qui décrit la valeur par défaut de votre paramètre, en ajoutant l’attribut **PSDefaultValue** à la description de votre paramètre et en spécifiant la propriété **Help** de **PSDefaultValue** .</span><span class="sxs-lookup"><span data-stu-id="225b7-173">Optionally, you can provide a brief help string that describes the default value of your parameter, by adding the **PSDefaultValue** attribute to the description of your parameter, and specifying the **Help** property of **PSDefaultValue** .</span></span> <span data-ttu-id="225b7-174">Pour fournir une chaîne d’aide qui décrit la valeur par défaut (100) du paramètre **Size** dans la `Get-SmallFiles` fonction, ajoutez l’attribut **PSDefaultValue** comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="225b7-174">To provide a help string that describes the default value (100) of the **Size** parameter in the `Get-SmallFiles` function, add the **PSDefaultValue** attribute as shown in the following example.</span></span>

```powershell
function Get-SmallFiles {
  param (
      [PSDefaultValue(Help = '100')]
      $Size = 100
  )
}
```

<span data-ttu-id="225b7-175">Pour plus d’informations sur la classe d’attributs **PSDefaultValue** , consultez [membres d’attribut PSDefaultValue](/dotnet/api/system.management.automation.psdefaultvalueattribute).</span><span class="sxs-lookup"><span data-stu-id="225b7-175">For more information about the **PSDefaultValue** attribute class, see [PSDefaultValue Attribute Members](/dotnet/api/system.management.automation.psdefaultvalueattribute).</span></span>

### <a name="positional-parameters"></a><span data-ttu-id="225b7-176">Paramètres positionnels</span><span class="sxs-lookup"><span data-stu-id="225b7-176">Positional Parameters</span></span>

<span data-ttu-id="225b7-177">Un paramètre positionnel est un paramètre sans nom de paramètre.</span><span class="sxs-lookup"><span data-stu-id="225b7-177">A positional parameter is a parameter without a parameter name.</span></span> <span data-ttu-id="225b7-178">PowerShell utilise l’ordre des valeurs de paramètre pour associer chaque valeur de paramètre à un paramètre dans la fonction.</span><span class="sxs-lookup"><span data-stu-id="225b7-178">PowerShell uses the parameter value order to associate each parameter value with a parameter in the function.</span></span>

<span data-ttu-id="225b7-179">Lorsque vous utilisez des paramètres positionnels, tapez une ou plusieurs valeurs après le nom de la fonction.</span><span class="sxs-lookup"><span data-stu-id="225b7-179">When you use positional parameters, type one or more values after the function name.</span></span> <span data-ttu-id="225b7-180">Les valeurs de paramètres positionnels sont assignées à la `$args` variable tableau.</span><span class="sxs-lookup"><span data-stu-id="225b7-180">Positional parameter values are assigned to the `$args` array variable.</span></span>
<span data-ttu-id="225b7-181">La valeur qui suit le nom de la fonction est assignée à la première position dans le `$args` tableau, `$args[0]` .</span><span class="sxs-lookup"><span data-stu-id="225b7-181">The value that follows the function name is assigned to the first position in the `$args` array, `$args[0]`.</span></span>

<span data-ttu-id="225b7-182">La `Get-Extension` fonction suivante ajoute l' `.txt` extension de nom de fichier à un nom de fichier que vous fournissez :</span><span class="sxs-lookup"><span data-stu-id="225b7-182">The following `Get-Extension` function adds the `.txt` file name extension to a file name that you supply:</span></span>

```powershell
function Get-Extension {
  $name = $args[0] + ".txt"
  $name
}
```

```powershell
Get-Extension myTextFile
```

```Output
myTextFile.txt
```

### <a name="switch-parameters"></a><span data-ttu-id="225b7-183">Paramètres de commutateur</span><span class="sxs-lookup"><span data-stu-id="225b7-183">Switch Parameters</span></span>

<span data-ttu-id="225b7-184">Un commutateur est un paramètre qui ne requiert pas de valeur.</span><span class="sxs-lookup"><span data-stu-id="225b7-184">A switch is a parameter that does not require a value.</span></span> <span data-ttu-id="225b7-185">Au lieu de cela, vous tapez le nom de la fonction suivi du nom du paramètre de commutateur.</span><span class="sxs-lookup"><span data-stu-id="225b7-185">Instead, you type the function name followed by the name of the switch parameter.</span></span>

<span data-ttu-id="225b7-186">Pour définir un paramètre de commutateur, spécifiez le type `[switch]` avant le nom du paramètre, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="225b7-186">To define a switch parameter, specify the type `[switch]` before the parameter name, as shown in the following example:</span></span>

```powershell
function Switch-Item {
  param ([switch]$on)
  if ($on) { "Switch on" }
  else { "Switch off" }
}
```

<span data-ttu-id="225b7-187">Quand vous tapez le `On` paramètre de commutateur après le nom de la fonction, la fonction affiche « activer ».</span><span class="sxs-lookup"><span data-stu-id="225b7-187">When you type the `On` switch parameter after the function name, the function displays "Switch on".</span></span> <span data-ttu-id="225b7-188">Sans le paramètre de commutateur, il affiche « désactiver ».</span><span class="sxs-lookup"><span data-stu-id="225b7-188">Without the switch parameter, it displays "Switch off".</span></span>

```powershell
Switch-Item -on
```

```Output
Switch on
```

```powershell
Switch-Item
```

```Output
Switch off
```

<span data-ttu-id="225b7-189">Vous pouvez également assigner une valeur **booléenne** à un commutateur quand vous exécutez la fonction, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="225b7-189">You can also assign a **Boolean** value to a switch when you run the function, as shown in the following example:</span></span>

```powershell
Switch-Item -on:$true
```

```Output
Switch on
```

```powershell
Switch-Item -on:$false
```

```Output
Switch off
```

## <a name="using-splatting-to-represent-command-parameters"></a><span data-ttu-id="225b7-190">Utilisation de la projection pour représenter les paramètres de commande</span><span class="sxs-lookup"><span data-stu-id="225b7-190">Using Splatting to Represent Command Parameters</span></span>

<span data-ttu-id="225b7-191">Vous pouvez utiliser la projection pour représenter les paramètres d’une commande.</span><span class="sxs-lookup"><span data-stu-id="225b7-191">You can use splatting to represent the parameters of a command.</span></span> <span data-ttu-id="225b7-192">Cette fonctionnalité est introduite dans Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="225b7-192">This feature is introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="225b7-193">Utilisez cette technique dans les fonctions qui appellent des commandes dans la session.</span><span class="sxs-lookup"><span data-stu-id="225b7-193">Use this technique in functions that call commands in the session.</span></span> <span data-ttu-id="225b7-194">Vous n’avez pas besoin de déclarer ou d’énumérer les paramètres de commande, ou de modifier la fonction lorsque les paramètres de commande changent.</span><span class="sxs-lookup"><span data-stu-id="225b7-194">You do not need to declare or enumerate the command parameters, or change the function when command parameters change.</span></span>

<span data-ttu-id="225b7-195">L’exemple de fonction suivant appelle l’applet de commande `Get-Command` .</span><span class="sxs-lookup"><span data-stu-id="225b7-195">The following sample function calls the `Get-Command` cmdlet.</span></span> <span data-ttu-id="225b7-196">La commande utilise `@Args` pour représenter les paramètres de `Get-Command` .</span><span class="sxs-lookup"><span data-stu-id="225b7-196">The command uses `@Args` to represent the parameters of `Get-Command`.</span></span>

```powershell
function Get-MyCommand { Get-Command @Args }
```

<span data-ttu-id="225b7-197">Vous pouvez utiliser tous les paramètres de `Get-Command` lorsque vous appelez la `Get-MyCommand` fonction.</span><span class="sxs-lookup"><span data-stu-id="225b7-197">You can use all of the parameters of `Get-Command` when you call the `Get-MyCommand` function.</span></span> <span data-ttu-id="225b7-198">Les paramètres et les valeurs de paramètre sont passés à la commande à l’aide de `@Args` .</span><span class="sxs-lookup"><span data-stu-id="225b7-198">The parameters and parameter values are passed to the command using `@Args`.</span></span>

```powershell
Get-MyCommand -Name Get-ChildItem
```

```Output
CommandType     Name                ModuleName
-----------     ----                ----------
Cmdlet          Get-ChildItem       Microsoft.PowerShell.Management
```

<span data-ttu-id="225b7-199">La `@Args` fonctionnalité utilise le `$Args` paramètre Automatic, qui représente les paramètres et les valeurs des applets de commande non déclarés des arguments restants.</span><span class="sxs-lookup"><span data-stu-id="225b7-199">The `@Args` feature uses the `$Args` automatic parameter, which represents undeclared cmdlet parameters and values from remaining arguments.</span></span>

<span data-ttu-id="225b7-200">Pour plus d’informations sur la projection, consultez [about_Splatting](about_Splatting.md).</span><span class="sxs-lookup"><span data-stu-id="225b7-200">For more information about splatting, see [about_Splatting](about_Splatting.md).</span></span>

## <a name="piping-objects-to-functions"></a><span data-ttu-id="225b7-201">Canalisation des objets vers les fonctions</span><span class="sxs-lookup"><span data-stu-id="225b7-201">Piping Objects to Functions</span></span>

<span data-ttu-id="225b7-202">Toute fonction peut prendre une entrée du pipeline.</span><span class="sxs-lookup"><span data-stu-id="225b7-202">Any function can take input from the pipeline.</span></span> <span data-ttu-id="225b7-203">Vous pouvez contrôler la façon dont une fonction traite l’entrée à partir du pipeline à l’aide de `Begin` `Process` `End` Mots clés, et.</span><span class="sxs-lookup"><span data-stu-id="225b7-203">You can control how a function processes input from the pipeline using `Begin`, `Process`, and `End` keywords.</span></span> <span data-ttu-id="225b7-204">L’exemple de syntaxe suivant illustre les trois mots clés :</span><span class="sxs-lookup"><span data-stu-id="225b7-204">The following sample syntax shows the three keywords:</span></span>

```
function <name> {
  begin {<statement list>}
  process {<statement list>}
  end {<statement list>}
}
```

<span data-ttu-id="225b7-205">La `Begin` liste d’instructions n’est exécutée qu’une seule fois, au début de la fonction.</span><span class="sxs-lookup"><span data-stu-id="225b7-205">The `Begin` statement list runs one time only, at the beginning of the function.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="225b7-206">Si votre fonction définit un `Begin` `Process` bloc ou, `End` tout votre code doit résider à l’intérieur de ces blocs.</span><span class="sxs-lookup"><span data-stu-id="225b7-206">If your function defines a `Begin`, `Process` or `End` block, all of your code must reside inside those blocks.</span></span> <span data-ttu-id="225b7-207">Aucun code n’est reconnu en dehors des blocs si l' *un* des blocs est défini.</span><span class="sxs-lookup"><span data-stu-id="225b7-207">No code will be recognized outside the blocks if *any* of the blocks are defined.</span></span>

<span data-ttu-id="225b7-208">La `Process` liste d’instructions s’exécute une fois pour chaque objet dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="225b7-208">The `Process` statement list runs one time for each object in the pipeline.</span></span>
<span data-ttu-id="225b7-209">Pendant que le `Process` bloc est en cours d’exécution, chaque objet de pipeline est affecté à la `$_` variable automatique, un objet de pipeline à la fois.</span><span class="sxs-lookup"><span data-stu-id="225b7-209">While the `Process` block is running, each pipeline object is assigned to the `$_` automatic variable, one pipeline object at a time.</span></span>

<span data-ttu-id="225b7-210">Une fois que la fonction a reçu tous les objets dans le pipeline, la `End` liste d’instructions s’exécute une fois.</span><span class="sxs-lookup"><span data-stu-id="225b7-210">After the function receives all the objects in the pipeline, the `End` statement list runs one time.</span></span> <span data-ttu-id="225b7-211">Si aucun `Begin` `Process` mot clé, ou n' `End` est utilisé, toutes les instructions sont traitées comme une `End` liste d’instructions.</span><span class="sxs-lookup"><span data-stu-id="225b7-211">If no `Begin`, `Process`, or `End` keywords are used, all the statements are treated like an `End` statement list.</span></span>

<span data-ttu-id="225b7-212">La fonction suivante utilise le `Process` mot clé.</span><span class="sxs-lookup"><span data-stu-id="225b7-212">The following function uses the `Process` keyword.</span></span> <span data-ttu-id="225b7-213">La fonction affiche des exemples à partir du pipeline :</span><span class="sxs-lookup"><span data-stu-id="225b7-213">The function displays examples from the pipeline:</span></span>

```powershell
function Get-Pipeline
{
  process {"The value is: $_"}
}
```

<span data-ttu-id="225b7-214">Pour illustrer cette fonction, entrez une liste de nombres séparés par des virgules, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="225b7-214">To demonstrate this function, enter an list of numbers separated by commas, as shown in the following example:</span></span>

```powershell
1,2,4 | Get-Pipeline
```

```Output
The value is: 1
The value is: 2
The value is: 4
```

<span data-ttu-id="225b7-215">Lorsque vous utilisez une fonction dans un pipeline, les objets transmis à la fonction sont assignés à la `$input` variable automatique.</span><span class="sxs-lookup"><span data-stu-id="225b7-215">When you use a function in a pipeline, the objects piped to the function are assigned to the `$input` automatic variable.</span></span> <span data-ttu-id="225b7-216">La fonction exécute des instructions avec le `Begin` mot clé avant que des objets proviennent du pipeline.</span><span class="sxs-lookup"><span data-stu-id="225b7-216">The function runs statements with the `Begin` keyword before any objects come from the pipeline.</span></span> <span data-ttu-id="225b7-217">La fonction exécute des instructions avec le `End` mot clé une fois que tous les objets ont été reçus du pipeline.</span><span class="sxs-lookup"><span data-stu-id="225b7-217">The function runs statements with the `End` keyword after all the objects have been received from the pipeline.</span></span>

<span data-ttu-id="225b7-218">L’exemple suivant illustre la `$input` variable automatique avec `Begin` les `End` Mots clés et.</span><span class="sxs-lookup"><span data-stu-id="225b7-218">The following example shows the `$input` automatic variable with `Begin` and `End` keywords.</span></span>

```powershell
function Get-PipelineBeginEnd
{
  begin {"Begin: The input is $input"}
  end {"End:   The input is $input" }
}
```

<span data-ttu-id="225b7-219">Si cette fonction est exécutée à l’aide du pipeline, elle affiche les résultats suivants :</span><span class="sxs-lookup"><span data-stu-id="225b7-219">If this function is run by using the pipeline, it displays the following results:</span></span>

```powershell
1,2,4 | Get-PipelineBeginEnd
```

```Output
Begin: The input is
End:   The input is 1 2 4
```

<span data-ttu-id="225b7-220">Lorsque l' `Begin` instruction s’exécute, la fonction n’a pas d’entrée du pipeline.</span><span class="sxs-lookup"><span data-stu-id="225b7-220">When the `Begin` statement runs, the function does not have the input from the pipeline.</span></span> <span data-ttu-id="225b7-221">L' `End` instruction s’exécute une fois que la fonction a les valeurs.</span><span class="sxs-lookup"><span data-stu-id="225b7-221">The `End` statement runs after the function has the values.</span></span>

<span data-ttu-id="225b7-222">Si la fonction a un `Process` mot clé, chaque objet dans `$input` est supprimé de `$input` et assigné à `$_` .</span><span class="sxs-lookup"><span data-stu-id="225b7-222">If the function has a `Process` keyword, each object in `$input` is removed from `$input` and assigned to `$_`.</span></span> <span data-ttu-id="225b7-223">L’exemple suivant contient une `Process` liste d’instructions :</span><span class="sxs-lookup"><span data-stu-id="225b7-223">The following example has a `Process` statement list:</span></span>

```powershell
function Get-PipelineInput
{
  process {"Processing:  $_ " }
  end {"End:   The input is: $input" }
}
```

<span data-ttu-id="225b7-224">Dans cet exemple, chaque objet qui est dirigé vers la fonction est envoyé à la `Process` liste d’instructions.</span><span class="sxs-lookup"><span data-stu-id="225b7-224">In this example, each object that is piped to the function is sent to the `Process` statement list.</span></span> <span data-ttu-id="225b7-225">Les `Process` instructions s’exécutent sur chaque objet, un objet à la fois.</span><span class="sxs-lookup"><span data-stu-id="225b7-225">The `Process` statements run on each object, one object at a time.</span></span> <span data-ttu-id="225b7-226">La `$input` variable automatique est vide lorsque la fonction atteint le `End` mot clé.</span><span class="sxs-lookup"><span data-stu-id="225b7-226">The `$input` automatic variable is empty when the function reaches the `End` keyword.</span></span>

```powershell
1,2,4 | Get-PipelineInput
```

```Output
Processing:  1
Processing:  2
Processing:  4
End:   The input is:
```

<span data-ttu-id="225b7-227">Pour plus d’informations, consultez [utilisation d’énumérateurs](about_Automatic_Variables.md#using-enumerators)</span><span class="sxs-lookup"><span data-stu-id="225b7-227">For more information, see [Using Enumerators](about_Automatic_Variables.md#using-enumerators)</span></span>

## <a name="filters"></a><span data-ttu-id="225b7-228">Filtres</span><span class="sxs-lookup"><span data-stu-id="225b7-228">Filters</span></span>

<span data-ttu-id="225b7-229">Un filtre est un type de fonction qui s’exécute sur chaque objet dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="225b7-229">A filter is a type of function that runs on each object in the pipeline.</span></span> <span data-ttu-id="225b7-230">Un filtre ressemble à une fonction avec toutes ses instructions dans un `Process` bloc.</span><span class="sxs-lookup"><span data-stu-id="225b7-230">A filter resembles a function with all its statements in a `Process` block.</span></span>

<span data-ttu-id="225b7-231">La syntaxe d’un filtre est la suivante :</span><span class="sxs-lookup"><span data-stu-id="225b7-231">The syntax of a filter is as follows:</span></span>

```
filter [<scope:>]<name> {<statement list>}
```

<span data-ttu-id="225b7-232">Le filtre suivant prend les entrées de journal du pipeline, puis affiche l’entrée entière ou uniquement la partie message de l’entrée :</span><span class="sxs-lookup"><span data-stu-id="225b7-232">The following filter takes log entries from the pipeline and then displays either the whole entry or only the message portion of the entry:</span></span>

```powershell
filter Get-ErrorLog ([switch]$message)
{
  if ($message) { Out-Host -InputObject $_.Message }
  else { $_ }
}
```

## <a name="function-scope"></a><span data-ttu-id="225b7-233">Portée de la fonction</span><span class="sxs-lookup"><span data-stu-id="225b7-233">Function Scope</span></span>

<span data-ttu-id="225b7-234">Une fonction existe dans l’étendue dans laquelle elle a été créée.</span><span class="sxs-lookup"><span data-stu-id="225b7-234">A function exists in the scope in which it was created.</span></span>

<span data-ttu-id="225b7-235">Si une fonction fait partie d’un script, la fonction est disponible pour les instructions de ce script.</span><span class="sxs-lookup"><span data-stu-id="225b7-235">If a function is part of a script, the function is available to statements within that script.</span></span> <span data-ttu-id="225b7-236">Par défaut, une fonction dans un script n’est pas disponible à l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="225b7-236">By default, a function in a script is not available at the command prompt.</span></span>

<span data-ttu-id="225b7-237">Vous pouvez spécifier l’étendue d’une fonction.</span><span class="sxs-lookup"><span data-stu-id="225b7-237">You can specify the scope of a function.</span></span> <span data-ttu-id="225b7-238">Par exemple, la fonction est ajoutée à la portée globale dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="225b7-238">For example, the function is added to the global scope in the following example:</span></span>

```powershell
function global:Get-DependentSvs {
  Get-Service | Where-Object {$_.DependentServices}
}
```

<span data-ttu-id="225b7-239">Quand une fonction est dans la portée globale, vous pouvez utiliser la fonction dans des scripts, dans des fonctions et sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="225b7-239">When a function is in the global scope, you can use the function in scripts, in functions, and at the command line.</span></span>

<span data-ttu-id="225b7-240">Les fonctions créent normalement une étendue.</span><span class="sxs-lookup"><span data-stu-id="225b7-240">Functions normally create a scope.</span></span> <span data-ttu-id="225b7-241">Les éléments créés dans une fonction, tels que les variables, existent uniquement dans l’étendue de la fonction.</span><span class="sxs-lookup"><span data-stu-id="225b7-241">The items created in a function, such as variables, exist only in the function scope.</span></span>

<span data-ttu-id="225b7-242">Pour plus d’informations sur l’étendue dans PowerShell, consultez [about_Scopes](about_Scopes.md).</span><span class="sxs-lookup"><span data-stu-id="225b7-242">For more information about scope in PowerShell, see [about_Scopes](about_Scopes.md).</span></span>

## <a name="finding-and-managing-functions-using-the-function-drive"></a><span data-ttu-id="225b7-243">Recherche et gestion des fonctions à l’aide du lecteur function :</span><span class="sxs-lookup"><span data-stu-id="225b7-243">Finding and Managing Functions Using the Function: Drive</span></span>

<span data-ttu-id="225b7-244">Toutes les fonctions et tous les filtres de PowerShell sont automatiquement stockés dans le `Function:` lecteur.</span><span class="sxs-lookup"><span data-stu-id="225b7-244">All the functions and filters in PowerShell are automatically stored in the `Function:` drive.</span></span> <span data-ttu-id="225b7-245">Ce lecteur est exposé par le fournisseur de **fonctions** PowerShell.</span><span class="sxs-lookup"><span data-stu-id="225b7-245">This drive is exposed by the PowerShell **Function** provider.</span></span>

<span data-ttu-id="225b7-246">Lorsque vous faites référence au `Function:` lecteur, tapez deux-points après la **fonction** , comme vous le feriez pour référencer le `C` `D` lecteur ou d’un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="225b7-246">When referring to the `Function:` drive, type a colon after **Function** , just as you would do when referencing the `C` or `D` drive of a computer.</span></span>

<span data-ttu-id="225b7-247">La commande suivante affiche toutes les fonctions dans la session active de PowerShell :</span><span class="sxs-lookup"><span data-stu-id="225b7-247">The following command displays all the functions in the current session of PowerShell:</span></span>

```powershell
Get-ChildItem function:
```

<span data-ttu-id="225b7-248">Les commandes de la fonction sont stockées sous la forme d’un bloc de script dans la propriété de définition de la fonction.</span><span class="sxs-lookup"><span data-stu-id="225b7-248">The commands in the function are stored as a script block in the definition property of the function.</span></span> <span data-ttu-id="225b7-249">Par exemple, pour afficher les commandes dans la fonction d’aide fournie avec PowerShell, tapez :</span><span class="sxs-lookup"><span data-stu-id="225b7-249">For example, to display the commands in the Help function that comes with PowerShell, type:</span></span>

```powershell
(Get-ChildItem function:help).Definition
```

<span data-ttu-id="225b7-250">Vous pouvez également utiliser la syntaxe suivante.</span><span class="sxs-lookup"><span data-stu-id="225b7-250">You can also use the following syntax.</span></span>

```powershell
$function:help
```

<span data-ttu-id="225b7-251">Pour plus d’informations sur le `Function:` lecteur, consultez la rubrique d’aide pour le fournisseur de **fonctions** .</span><span class="sxs-lookup"><span data-stu-id="225b7-251">For more information about the `Function:` drive, see the help topic for the **Function** provider.</span></span> <span data-ttu-id="225b7-252">Tapez `Get-Help Function`.</span><span class="sxs-lookup"><span data-stu-id="225b7-252">Type `Get-Help Function`.</span></span>

## <a name="reusing-functions-in-new-sessions"></a><span data-ttu-id="225b7-253">Réutilisation des fonctions dans les nouvelles sessions</span><span class="sxs-lookup"><span data-stu-id="225b7-253">Reusing Functions in New Sessions</span></span>

<span data-ttu-id="225b7-254">Quand vous tapez une fonction à l’invite de commandes PowerShell, la fonction devient partie intégrante de la session active.</span><span class="sxs-lookup"><span data-stu-id="225b7-254">When you type a function at the PowerShell command prompt, the function becomes part of the current session.</span></span> <span data-ttu-id="225b7-255">Elle est disponible jusqu’à la fin de la session.</span><span class="sxs-lookup"><span data-stu-id="225b7-255">It is available until the session ends.</span></span>

<span data-ttu-id="225b7-256">Pour utiliser votre fonction dans toutes les sessions PowerShell, ajoutez la fonction à votre profil PowerShell.</span><span class="sxs-lookup"><span data-stu-id="225b7-256">To use your function in all PowerShell sessions, add the function to your PowerShell profile.</span></span> <span data-ttu-id="225b7-257">Pour plus d'informations sur les profils, consultez [about_Profiles](about_Profiles.md).</span><span class="sxs-lookup"><span data-stu-id="225b7-257">For more information about profiles, see [about_Profiles](about_Profiles.md).</span></span>

<span data-ttu-id="225b7-258">Vous pouvez également enregistrer votre fonction dans un fichier de script PowerShell.</span><span class="sxs-lookup"><span data-stu-id="225b7-258">You can also save your function in a PowerShell script file.</span></span> <span data-ttu-id="225b7-259">Tapez votre fonction dans un fichier texte, puis enregistrez le fichier avec l' `.ps1` extension de nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="225b7-259">Type your function in a text file, and then save the file with the `.ps1` file name extension.</span></span>

## <a name="writing-help-for-functions"></a><span data-ttu-id="225b7-260">Écriture de l’aide pour les fonctions</span><span class="sxs-lookup"><span data-stu-id="225b7-260">Writing Help for Functions</span></span>

<span data-ttu-id="225b7-261">L' `Get-Help` applet de commande obtient de l’aide pour les fonctions, ainsi que pour les applets de commande, les fournisseurs et les scripts.</span><span class="sxs-lookup"><span data-stu-id="225b7-261">The `Get-Help` cmdlet gets help for functions, as well as for cmdlets, providers, and scripts.</span></span> <span data-ttu-id="225b7-262">Pour obtenir de l’aide pour une fonction, tapez `Get-Help` suivi du nom de la fonction.</span><span class="sxs-lookup"><span data-stu-id="225b7-262">To get help for a function, type `Get-Help` followed by the function name.</span></span>

<span data-ttu-id="225b7-263">Par exemple, pour obtenir de l’aide pour la `Get-MyDisks` fonction, tapez :</span><span class="sxs-lookup"><span data-stu-id="225b7-263">For example, to get help for the `Get-MyDisks` function, type:</span></span>

```powershell
Get-Help Get-MyDisks
```

<span data-ttu-id="225b7-264">Vous pouvez écrire l’aide d’une fonction à l’aide de l’une des deux méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="225b7-264">You can write help for a function by using either of the two following methods:</span></span>

- <span data-ttu-id="225b7-265">Aide Comment-Based pour les fonctions</span><span class="sxs-lookup"><span data-stu-id="225b7-265">Comment-Based Help for Functions</span></span>

  <span data-ttu-id="225b7-266">Créez une rubrique d’aide en utilisant des mots clés spéciaux dans les commentaires.</span><span class="sxs-lookup"><span data-stu-id="225b7-266">Create a help topic by using special keywords in the comments.</span></span> <span data-ttu-id="225b7-267">Pour créer une aide basée sur des commentaires pour une fonction, les commentaires doivent être placés au début ou à la fin du corps de la fonction ou sur les lignes qui précèdent le mot clé function.</span><span class="sxs-lookup"><span data-stu-id="225b7-267">To create comment-based help for a function, the comments must be placed at the beginning or end of the function body or on the lines preceding the function keyword.</span></span> <span data-ttu-id="225b7-268">Pour plus d’informations sur l’aide basée sur les commentaires, consultez [about_Comment_Based_Help](about_Comment_Based_Help.md).</span><span class="sxs-lookup"><span data-stu-id="225b7-268">For more information about comment-based help, see [about_Comment_Based_Help](about_Comment_Based_Help.md).</span></span>

- <span data-ttu-id="225b7-269">Aide XML-Based pour les fonctions</span><span class="sxs-lookup"><span data-stu-id="225b7-269">XML-Based Help for Functions</span></span>

  <span data-ttu-id="225b7-270">Créez une rubrique d’aide XML, telle que le type qui est généralement créé pour les applets de commande.</span><span class="sxs-lookup"><span data-stu-id="225b7-270">Create an XML-based help topic, such as the type that is typically created for cmdlets.</span></span> <span data-ttu-id="225b7-271">L’aide XML est requise si vous localisez des rubriques d’aide dans plusieurs langues.</span><span class="sxs-lookup"><span data-stu-id="225b7-271">XML-based help is required if you are localizing help topics into multiple languages.</span></span>

  <span data-ttu-id="225b7-272">Pour associer la fonction à la rubrique d’aide basée sur XML, utilisez le `.ExternalHelp` mot clé d’aide basée sur des commentaires.</span><span class="sxs-lookup"><span data-stu-id="225b7-272">To associate the function with the XML-based help topic, use the `.ExternalHelp` comment-based help keyword.</span></span> <span data-ttu-id="225b7-273">Sans ce mot clé, `Get-Help` la rubrique d’aide de la fonction est introuvable et les appels à `Get-Help` pour la fonction retournent uniquement l’aide générée automatiquement.</span><span class="sxs-lookup"><span data-stu-id="225b7-273">Without this keyword, `Get-Help` cannot find the function help topic and calls to `Get-Help` for the function return only auto-generated help.</span></span>

  <span data-ttu-id="225b7-274">Pour plus d’informations sur le `ExternalHelp` mot clé, consultez [about_Comment_Based_Help](about_Comment_Based_Help.md).</span><span class="sxs-lookup"><span data-stu-id="225b7-274">For more information about the `ExternalHelp` keyword, see [about_Comment_Based_Help](about_Comment_Based_Help.md).</span></span> <span data-ttu-id="225b7-275">Pour plus d’informations sur l’aide XML, consultez [Comment écrire l’aide sur les applets](https://go.microsoft.com/fwlink/?LinkID=123415) de commande dans MSDN Library.</span><span class="sxs-lookup"><span data-stu-id="225b7-275">For more information about XML-based help, see [How to Write Cmdlet Help](https://go.microsoft.com/fwlink/?LinkID=123415) in the MSDN library.</span></span>

## <a name="see-also"></a><span data-ttu-id="225b7-276">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="225b7-276">See also</span></span>

[<span data-ttu-id="225b7-277">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="225b7-277">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="225b7-278">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="225b7-278">about_Comment_Based_Help</span></span>](about_Comment_Based_Help.md)

[<span data-ttu-id="225b7-279">about_Functions_Advanced</span><span class="sxs-lookup"><span data-stu-id="225b7-279">about_Functions_Advanced</span></span>](about_Functions_Advanced.md)

[<span data-ttu-id="225b7-280">about_Functions_Advanced_Methods</span><span class="sxs-lookup"><span data-stu-id="225b7-280">about_Functions_Advanced_Methods</span></span>](about_Functions_Advanced_Methods.md)

[<span data-ttu-id="225b7-281">about_Functions_Advanced_Parameters</span><span class="sxs-lookup"><span data-stu-id="225b7-281">about_Functions_Advanced_Parameters</span></span>](about_Functions_Advanced_Parameters.md)

[<span data-ttu-id="225b7-282">about_Functions_CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="225b7-282">about_Functions_CmdletBindingAttribute</span></span>](about_Functions_CmdletBindingAttribute.md)

[<span data-ttu-id="225b7-283">about_Functions_OutputTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="225b7-283">about_Functions_OutputTypeAttribute</span></span>](about_Functions_OutputTypeAttribute.md)

[<span data-ttu-id="225b7-284">about_Parameters</span><span class="sxs-lookup"><span data-stu-id="225b7-284">about_Parameters</span></span>](about_Parameters.md)

[<span data-ttu-id="225b7-285">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="225b7-285">about_Profiles</span></span>](about_Profiles.md)

[<span data-ttu-id="225b7-286">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="225b7-286">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="225b7-287">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="225b7-287">about_Script_Blocks</span></span>](about_Script_Blocks.md)

[<span data-ttu-id="225b7-288">about_Function_provider</span><span class="sxs-lookup"><span data-stu-id="225b7-288">about_Function_provider</span></span>](about_Function_provider.md)
