---
description: Décrit l’attribut qui fait fonctionner une fonction comme une applet de commande compilée.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 06/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions_CmdletBindingAttribute
ms.openlocfilehash: c4090910a72e2f68b5a710c76b20cc8af532c04b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207082"
---
# <a name="about-functions-cmdletbindingattribute"></a><span data-ttu-id="32ef1-104">À propos des fonctions CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="32ef1-104">About Functions CmdletBindingAttribute</span></span>

## <a name="short-description"></a><span data-ttu-id="32ef1-105">Description courte</span><span class="sxs-lookup"><span data-stu-id="32ef1-105">Short description</span></span>
<span data-ttu-id="32ef1-106">Décrit l’attribut qui fait fonctionner une fonction comme une applet de commande compilée.</span><span class="sxs-lookup"><span data-stu-id="32ef1-106">Describes the attribute that makes a function work like a compiled cmdlet.</span></span>

## <a name="long-description"></a><span data-ttu-id="32ef1-107">Description longue</span><span class="sxs-lookup"><span data-stu-id="32ef1-107">Long description</span></span>

<span data-ttu-id="32ef1-108">L' `CmdletBinding` attribut est un attribut des fonctions qui les font fonctionner comme des cmdlets compilées écrites en C#.</span><span class="sxs-lookup"><span data-stu-id="32ef1-108">The `CmdletBinding` attribute is an attribute of functions that makes them operate like compiled cmdlets written in C#.</span></span> <span data-ttu-id="32ef1-109">Il permet d’accéder aux fonctionnalités des applets de commande.</span><span class="sxs-lookup"><span data-stu-id="32ef1-109">It provides access to the features of cmdlets.</span></span>

<span data-ttu-id="32ef1-110">PowerShell lie les paramètres des fonctions qui ont l' `CmdletBinding` attribut de la même manière qu’il lie les paramètres des applets de commande compilées.</span><span class="sxs-lookup"><span data-stu-id="32ef1-110">PowerShell binds the parameters of functions that have the `CmdletBinding` attribute in the same way that it binds the parameters of compiled cmdlets.</span></span> <span data-ttu-id="32ef1-111">La `$PSCmdlet` variable automatique est disponible pour les fonctions avec l' `CmdletBinding` attribut, mais la `$Args` variable n’est pas disponible.</span><span class="sxs-lookup"><span data-stu-id="32ef1-111">The `$PSCmdlet` automatic variable is available to functions with the `CmdletBinding` attribute, but the `$Args` variable is not available.</span></span>

<span data-ttu-id="32ef1-112">Dans les fonctions qui ont l' `CmdletBinding` attribut, les paramètres inconnus et les arguments positionnels qui n’ont pas de paramètres positionnels correspondants provoquent l’échec de la liaison de paramètre.</span><span class="sxs-lookup"><span data-stu-id="32ef1-112">In functions that have the `CmdletBinding` attribute, unknown parameters and positional arguments that have no matching positional parameters cause parameter binding to fail.</span></span>

> [!NOTE]
> <span data-ttu-id="32ef1-113">Les applets de commande compilées utilisent l’attribut required `Cmdlet` , qui est similaire à l' `CmdletBinding` attribut décrit dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="32ef1-113">Compiled cmdlets use the required `Cmdlet` attribute, which is similar to the `CmdletBinding` attribute that is described in this topic.</span></span>

## <a name="syntax"></a><span data-ttu-id="32ef1-114">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="32ef1-114">Syntax</span></span>

<span data-ttu-id="32ef1-115">L’exemple suivant illustre le format d’une fonction qui spécifie tous les arguments facultatifs de l' `CmdletBinding` attribut.</span><span class="sxs-lookup"><span data-stu-id="32ef1-115">The following example shows the format of a function that specifies all the optional arguments of the `CmdletBinding` attribute.</span></span> <span data-ttu-id="32ef1-116">Une brève description de chaque argument suit cet exemple.</span><span class="sxs-lookup"><span data-stu-id="32ef1-116">A brief description of each argument follows this example.</span></span>

```powershell
{
    [CmdletBinding(ConfirmImpact=<String>,
    DefaultParameterSetName=<String>,
    HelpURI=<URI>,
    SupportsPaging=<Boolean>,
    SupportsShouldProcess=<Boolean>,
    PositionalBinding=<Boolean>)]

    Param ($Parameter1)
    Begin{}
    Process{}
    End{}
}
```

## <a name="confirmimpact"></a><span data-ttu-id="32ef1-117">ConfirmImpact</span><span class="sxs-lookup"><span data-stu-id="32ef1-117">ConfirmImpact</span></span>

<span data-ttu-id="32ef1-118">L’argument **ConfirmImpact** spécifie quand l’action de la fonction doit être confirmée par un appel à la méthode **ShouldProcess** .</span><span class="sxs-lookup"><span data-stu-id="32ef1-118">The **ConfirmImpact** argument specifies when the action of the function should be confirmed by a call to the **ShouldProcess** method.</span></span> <span data-ttu-id="32ef1-119">L’appel à la méthode **ShouldProcess** affiche une invite de confirmation uniquement lorsque l’argument **ConfirmImpact** est supérieur ou égal à la valeur de la `$ConfirmPreference` variable de préférence.</span><span class="sxs-lookup"><span data-stu-id="32ef1-119">The call to the **ShouldProcess** method displays a confirmation prompt only when the **ConfirmImpact** argument is equal to or greater than the value of the `$ConfirmPreference` preference variable.</span></span> <span data-ttu-id="32ef1-120">(La valeur par défaut de l’argument est **Medium** .) Spécifiez cet argument uniquement lorsque l’argument **SupportsShouldProcess** est également spécifié.</span><span class="sxs-lookup"><span data-stu-id="32ef1-120">(The default value of the argument is **Medium** .) Specify this argument only when the **SupportsShouldProcess** argument is also specified.</span></span>

<span data-ttu-id="32ef1-121">Pour plus d’informations sur les demandes de confirmation, consultez [demande de confirmation](/powershell/scripting/developer/cmdlet/requesting-confirmation).</span><span class="sxs-lookup"><span data-stu-id="32ef1-121">For more information about confirmation requests, see [Requesting Confirmation](/powershell/scripting/developer/cmdlet/requesting-confirmation).</span></span>

## <a name="defaultparametersetname"></a><span data-ttu-id="32ef1-122">DefaultParameterSetName</span><span class="sxs-lookup"><span data-stu-id="32ef1-122">DefaultParameterSetName</span></span>

<span data-ttu-id="32ef1-123">L’argument **DefaultParameterSetName** spécifie le nom du jeu de paramètres que PowerShell essaiera d’utiliser lorsqu’il ne peut pas déterminer le jeu de paramètres à utiliser.</span><span class="sxs-lookup"><span data-stu-id="32ef1-123">The **DefaultParameterSetName** argument specifies the name of the parameter set that PowerShell will attempt to use when it cannot determine which parameter set to use.</span></span> <span data-ttu-id="32ef1-124">Vous pouvez éviter ce problème en définissant le paramètre unique de chaque paramètre sur un paramètre obligatoire.</span><span class="sxs-lookup"><span data-stu-id="32ef1-124">You can avoid this issue by making the unique parameter of each parameter set a mandatory parameter.</span></span>

## <a name="helpuri"></a><span data-ttu-id="32ef1-125">HelpURI</span><span class="sxs-lookup"><span data-stu-id="32ef1-125">HelpURI</span></span>

<span data-ttu-id="32ef1-126">L’argument **HelpURI** spécifie l’adresse Internet de la version en ligne de la rubrique d’aide qui décrit la fonction.</span><span class="sxs-lookup"><span data-stu-id="32ef1-126">The **HelpURI** argument specifies the internet address of the online version of the help topic that describes the function.</span></span> <span data-ttu-id="32ef1-127">La valeur de l’argument **HelpURI** doit commencer par « http » ou « HTTPS ».</span><span class="sxs-lookup"><span data-stu-id="32ef1-127">The value of the **HelpURI** argument must begin with "http" or "https".</span></span>

<span data-ttu-id="32ef1-128">La valeur de l’argument **HelpURI** est utilisée pour la valeur de la propriété **HelpURI** de l’objet **CommandInfo** qui `Get-Command` retourne pour la fonction.</span><span class="sxs-lookup"><span data-stu-id="32ef1-128">The **HelpURI** argument value is used for the value of the **HelpURI** property of the **CommandInfo** object that `Get-Command` returns for the function.</span></span>

<span data-ttu-id="32ef1-129">Toutefois, lorsque des fichiers d’aide sont installés sur l’ordinateur et que la valeur du premier lien de la section **relatedlinks** du fichier d’aide est un URI, ou que la valeur de la première `.Link` directive dans l’aide basée sur les commentaires est un URI, l’URI du fichier d’aide est utilisé comme valeur de la propriété **HelpUri** de la fonction.</span><span class="sxs-lookup"><span data-stu-id="32ef1-129">However, when help files are installed on the computer and the value of the first link in the **RelatedLinks** section of the help file is a URI, or the value of the first `.Link` directive in comment-based help is a URI, the URI in the help file is used as the value of the **HelpUri** property of the function.</span></span>

<span data-ttu-id="32ef1-130">L' `Get-Help` applet de commande utilise la valeur de la propriété **HelpURI** pour rechercher la version en ligne de la rubrique d’aide de la fonction lorsque le paramètre **Online** de `Get-Help` est spécifié dans une commande.</span><span class="sxs-lookup"><span data-stu-id="32ef1-130">The `Get-Help` cmdlet uses the value of the **HelpURI** property to locate the online version of the function help topic when the **Online** parameter of `Get-Help` is specified in a command.</span></span>

## <a name="supportspaging"></a><span data-ttu-id="32ef1-131">SupportsPaging</span><span class="sxs-lookup"><span data-stu-id="32ef1-131">SupportsPaging</span></span>

<span data-ttu-id="32ef1-132">L’argument **SupportsPaging** ajoute les paramètres **First** , **Skip** et **IncludeTotalCount** à la fonction.</span><span class="sxs-lookup"><span data-stu-id="32ef1-132">The **SupportsPaging** argument adds the **First** , **Skip** , and **IncludeTotalCount** parameters to the function.</span></span> <span data-ttu-id="32ef1-133">Ces paramètres permettent aux utilisateurs de sélectionner une sortie à partir d’un jeu de résultats très volumineux.</span><span class="sxs-lookup"><span data-stu-id="32ef1-133">These parameters allow users to select output from a very large result set.</span></span> <span data-ttu-id="32ef1-134">Cet argument est conçu pour les applets de commande et les fonctions qui retournent des données à partir de banques de données volumineuses prenant en charge la sélection de données, par exemple une base de données SQL.</span><span class="sxs-lookup"><span data-stu-id="32ef1-134">This argument is designed for cmdlets and functions that return data from large data stores that support data selection, such as an SQL database.</span></span>

<span data-ttu-id="32ef1-135">Cet argument a été introduit dans Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="32ef1-135">This argument was introduced in Windows PowerShell 3.0.</span></span>

- <span data-ttu-id="32ef1-136">**First** : obtient uniquement les « n » premiers objets.</span><span class="sxs-lookup"><span data-stu-id="32ef1-136">**First** : Gets only the first 'n' objects.</span></span>
- <span data-ttu-id="32ef1-137">**Ignorer** : ignore les « n » premiers objets, puis obtient les objets restants.</span><span class="sxs-lookup"><span data-stu-id="32ef1-137">**Skip** :  Ignores the first 'n' objects and then gets the remaining objects.</span></span>
- <span data-ttu-id="32ef1-138">**IncludeTotalCount** : indique le nombre d’objets dans le jeu de données (un entier) suivis des objets.</span><span class="sxs-lookup"><span data-stu-id="32ef1-138">**IncludeTotalCount** : Reports the number of objects in the data set (an integer) followed by the objects.</span></span> <span data-ttu-id="32ef1-139">Si l’applet de commande ne peut pas déterminer le nombre total, elle retourne « nombre total inconnu ».</span><span class="sxs-lookup"><span data-stu-id="32ef1-139">If the cmdlet cannot determine the total count, it returns "Unknown total count".</span></span>

<span data-ttu-id="32ef1-140">PowerShell comprend **NewTotalCount** , une méthode d’assistance qui obtient la valeur de nombre total à retourner et comprend une estimation de la précision de la valeur du nombre total.</span><span class="sxs-lookup"><span data-stu-id="32ef1-140">PowerShell includes **NewTotalCount** , a helper method that gets the total count value to return and includes an estimate of the accuracy of the total count value.</span></span>

<span data-ttu-id="32ef1-141">L’exemple de fonction suivant montre comment ajouter la prise en charge des paramètres de pagination à une fonction avancée.</span><span class="sxs-lookup"><span data-stu-id="32ef1-141">The following sample function shows how to add support for the paging parameters to an advanced function.</span></span>

```powershell
function Get-Numbers {
    [CmdletBinding(SupportsPaging = $true)]
    param()

    $FirstNumber = [Math]::Min($PSCmdlet.PagingParameters.Skip, 100)
    $LastNumber = [Math]::Min($PSCmdlet.PagingParameters.First +
      $FirstNumber - 1, 100)

    if ($PSCmdlet.PagingParameters.IncludeTotalCount) {
        $TotalCountAccuracy = 1.0
        $TotalCount = $PSCmdlet.PagingParameters.NewTotalCount(100,
          $TotalCountAccuracy)
        Write-Output $TotalCount
    }
    $FirstNumber .. $LastNumber | Write-Output
}
```

## <a name="supportsshouldprocess"></a><span data-ttu-id="32ef1-142">SupportsShouldProcess</span><span class="sxs-lookup"><span data-stu-id="32ef1-142">SupportsShouldProcess</span></span>

<span data-ttu-id="32ef1-143">L’argument **SupportsShouldProcess** ajoute des paramètres **Confirm** et **WhatIf** à la fonction.</span><span class="sxs-lookup"><span data-stu-id="32ef1-143">The **SupportsShouldProcess** argument adds **Confirm** and **WhatIf** parameters to the function.</span></span> <span data-ttu-id="32ef1-144">Le paramètre **Confirm** invite l’utilisateur avant d’exécuter la commande sur chaque objet dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="32ef1-144">The **Confirm** parameter prompts the user before it runs the command on each object in the pipeline.</span></span> <span data-ttu-id="32ef1-145">Le paramètre **WhatIf** répertorie les modifications apportées par la commande, au lieu d’exécuter la commande.</span><span class="sxs-lookup"><span data-stu-id="32ef1-145">The **WhatIf** parameter lists the changes that the command would make, instead of running the command.</span></span>

## <a name="positionalbinding"></a><span data-ttu-id="32ef1-146">PositionalBinding</span><span class="sxs-lookup"><span data-stu-id="32ef1-146">PositionalBinding</span></span>

<span data-ttu-id="32ef1-147">L’argument **PositionalBinding** détermine si les paramètres de la fonction sont positionnels par défaut.</span><span class="sxs-lookup"><span data-stu-id="32ef1-147">The **PositionalBinding** argument determines whether parameters in the function are positional by default.</span></span> <span data-ttu-id="32ef1-148">La valeur par défaut est `$True`.</span><span class="sxs-lookup"><span data-stu-id="32ef1-148">The default value is `$True`.</span></span> <span data-ttu-id="32ef1-149">Vous pouvez utiliser l’argument **PositionalBinding** avec la valeur `$False` pour désactiver la liaison de position.</span><span class="sxs-lookup"><span data-stu-id="32ef1-149">You can use the **PositionalBinding** argument with a value of `$False` to disable positional binding.</span></span>

<span data-ttu-id="32ef1-150">L’argument **PositionalBinding** est introduit dans Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="32ef1-150">The **PositionalBinding** argument is introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="32ef1-151">Lorsque les paramètres sont positionnels, le nom du paramètre est facultatif.</span><span class="sxs-lookup"><span data-stu-id="32ef1-151">When parameters are positional, the parameter name is optional.</span></span>
<span data-ttu-id="32ef1-152">PowerShell associe les valeurs de paramètre sans nom aux paramètres de fonction en fonction de l’ordre ou de la position des valeurs de paramètre sans nom dans la commande de fonction.</span><span class="sxs-lookup"><span data-stu-id="32ef1-152">PowerShell associates unnamed parameter values with the function parameters according to the order or position of the unnamed parameter values in the function command.</span></span>

<span data-ttu-id="32ef1-153">Lorsque les paramètres ne sont pas positionnels (ils sont « nommés »), le nom du paramètre (ou une abréviation ou un alias du nom) est requis dans la commande.</span><span class="sxs-lookup"><span data-stu-id="32ef1-153">When parameters are not positional (they are "named"), the parameter name (or an abbreviation or alias of the name) is required in the command.</span></span>

<span data-ttu-id="32ef1-154">Quand **PositionalBinding** a la `$True` valeur, les paramètres de fonction sont positionnels par défaut.</span><span class="sxs-lookup"><span data-stu-id="32ef1-154">When **PositionalBinding** is `$True`, function parameters are positional by default.</span></span> <span data-ttu-id="32ef1-155">PowerShell assigne le numéro de position aux paramètres dans l’ordre dans lequel ils sont déclarés dans la fonction.</span><span class="sxs-lookup"><span data-stu-id="32ef1-155">PowerShell assigns position number to the parameters in the order in which they are declared in the function.</span></span>

<span data-ttu-id="32ef1-156">Quand **PositionalBinding** a la `$False` valeur, les paramètres de fonction ne sont pas positionnels par défaut.</span><span class="sxs-lookup"><span data-stu-id="32ef1-156">When **PositionalBinding** is `$False`, function parameters are not positional by default.</span></span> <span data-ttu-id="32ef1-157">À moins que l’argument **position** de l’attribut **Parameter** ne soit déclaré sur le paramètre, le nom du paramètre (ou un alias ou une abréviation) doit être inclus lorsque le paramètre est utilisé dans une fonction.</span><span class="sxs-lookup"><span data-stu-id="32ef1-157">Unless the **Position** argument of the **Parameter** attribute is declared on the parameter, the parameter name (or an alias or abbreviation) must be included when the parameter is used in a function.</span></span>

<span data-ttu-id="32ef1-158">L’argument **position** de l’attribut **Parameter** est prioritaire par rapport à la valeur par défaut de **PositionalBinding** .</span><span class="sxs-lookup"><span data-stu-id="32ef1-158">The **Position** argument of the **Parameter** attribute takes precedence over the **PositionalBinding** default value.</span></span> <span data-ttu-id="32ef1-159">Vous pouvez utiliser l’argument **position** pour spécifier une valeur de position pour un paramètre.</span><span class="sxs-lookup"><span data-stu-id="32ef1-159">You can use the **Position** argument to specify a position value for a parameter.</span></span> <span data-ttu-id="32ef1-160">Pour plus d’informations sur l’argument **position** , consultez [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).</span><span class="sxs-lookup"><span data-stu-id="32ef1-160">For more information about the **Position** argument, see [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).</span></span>

## <a name="notes"></a><span data-ttu-id="32ef1-161">Notes</span><span class="sxs-lookup"><span data-stu-id="32ef1-161">Notes</span></span>

<span data-ttu-id="32ef1-162">L’argument **SupportsTransactions** n’est pas pris en charge dans les fonctions avancées.</span><span class="sxs-lookup"><span data-stu-id="32ef1-162">The **SupportsTransactions** argument is not supported in advanced functions.</span></span>

## <a name="keywords"></a><span data-ttu-id="32ef1-163">Mots clés</span><span class="sxs-lookup"><span data-stu-id="32ef1-163">Keywords</span></span>

<span data-ttu-id="32ef1-164">about_Functions_CmdletBinding_Attribute</span><span class="sxs-lookup"><span data-stu-id="32ef1-164">about_Functions_CmdletBinding_Attribute</span></span>

## <a name="see-also"></a><span data-ttu-id="32ef1-165">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="32ef1-165">See also</span></span>

[<span data-ttu-id="32ef1-166">about_Functions</span><span class="sxs-lookup"><span data-stu-id="32ef1-166">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="32ef1-167">about_Functions_Advanced</span><span class="sxs-lookup"><span data-stu-id="32ef1-167">about_Functions_Advanced</span></span>](about_Functions_Advanced.md)

[<span data-ttu-id="32ef1-168">about_Functions_Advanced_Methods</span><span class="sxs-lookup"><span data-stu-id="32ef1-168">about_Functions_Advanced_Methods</span></span>](about_Functions_Advanced_Methods.md)

[<span data-ttu-id="32ef1-169">about_Functions_Advanced_Parameters</span><span class="sxs-lookup"><span data-stu-id="32ef1-169">about_Functions_Advanced_Parameters</span></span>](about_Functions_Advanced_Parameters.md)

[<span data-ttu-id="32ef1-170">about_Functions_OutputTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="32ef1-170">about_Functions_OutputTypeAttribute</span></span>](about_Functions_OutputTypeAttribute.md)
