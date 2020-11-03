---
description: Décrit les diagrammes de syntaxe utilisés dans PowerShell.
keywords: powershell,applet de commande
ms.date: 06/27/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_command_syntax?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Command_Syntax
ms.openlocfilehash: a9da31213e76f5d28fbcb2cf4f4f6e9c49d51866
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208293"
---
# <a name="about-command-syntax"></a><span data-ttu-id="aa090-104">À propos de la syntaxe de commande</span><span class="sxs-lookup"><span data-stu-id="aa090-104">About Command Syntax</span></span>

## <a name="short-description"></a><span data-ttu-id="aa090-105">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="aa090-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="aa090-106">Décrit les diagrammes de syntaxe utilisés dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aa090-106">Describes the syntax diagrams that are used in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="aa090-107">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="aa090-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="aa090-108">Les applets de commande [obtenir-Help](xref:Microsoft.PowerShell.Core.Get-Help) et [obtenir-Command](xref:Microsoft.PowerShell.Core.Get-Command) affichent des diagrammes de syntaxe pour vous aider à construire correctement des commandes.</span><span class="sxs-lookup"><span data-stu-id="aa090-108">The [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) and [Get-Command](xref:Microsoft.PowerShell.Core.Get-Command) cmdlets display syntax diagrams to help you construct commands correctly.</span></span> <span data-ttu-id="aa090-109">Cette rubrique explique comment interpréter les diagrammes de syntaxe.</span><span class="sxs-lookup"><span data-stu-id="aa090-109">This topic explains how to interpret the syntax diagrams.</span></span>

## <a name="syntax-diagrams"></a><span data-ttu-id="aa090-110">DIAGRAMMES DE SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="aa090-110">SYNTAX DIAGRAMS</span></span>

<span data-ttu-id="aa090-111">Chaque paragraphe dans un diagramme de syntaxe de commande représente un formulaire valide de la commande.</span><span class="sxs-lookup"><span data-stu-id="aa090-111">Each paragraph in a command syntax diagram represents a valid form of the command.</span></span>

<span data-ttu-id="aa090-112">Pour construire une commande, suivez le diagramme de la syntaxe de gauche à droite.</span><span class="sxs-lookup"><span data-stu-id="aa090-112">To construct a command, follow the syntax diagram from left to right.</span></span> <span data-ttu-id="aa090-113">Sélectionnez parmi les paramètres facultatifs et fournissez des valeurs pour les espaces réservés.</span><span class="sxs-lookup"><span data-stu-id="aa090-113">Select from among the optional parameters and provide values for the placeholders.</span></span>

<span data-ttu-id="aa090-114">PowerShell utilise la notation suivante pour les diagrammes de syntaxe.</span><span class="sxs-lookup"><span data-stu-id="aa090-114">PowerShell uses the following notation for syntax diagrams.</span></span>

```powershell
<command-name> -<Required Parameter Name> <Required Parameter Value>
[-<Optional Parameter Name> <Optional Parameter Value>]
[-<Optional Switch Parameters>]
[-<Optional Parameter Name>] <Required Parameter Value>
```

<span data-ttu-id="aa090-115">Voici la syntaxe de l’applet de commande [New-alias](xref:Microsoft.PowerShell.Utility.New-Alias) .</span><span class="sxs-lookup"><span data-stu-id="aa090-115">The following is the syntax for the [New-Alias](xref:Microsoft.PowerShell.Utility.New-Alias) cmdlet.</span></span>

```powershell
New-Alias [-Name] <string> [-Value] <string> [-Description <string>]
[-Force] [-Option {None | ReadOnly | Constant | Private | AllScope}]
[-PassThru] [-Scope <string>] [-Confirm] [-WhatIf] [<CommonParameters>]
```

<span data-ttu-id="aa090-116">La syntaxe est capitalisée pour des raisons de lisibilité, mais PowerShell ne respecte pas la casse.</span><span class="sxs-lookup"><span data-stu-id="aa090-116">The syntax is capitalized for readability, but PowerShell is case-insensitive.</span></span>

<span data-ttu-id="aa090-117">Le diagramme de syntaxe contient les éléments suivants.</span><span class="sxs-lookup"><span data-stu-id="aa090-117">The syntax diagram has the following elements.</span></span>

## <a name="command-name"></a><span data-ttu-id="aa090-118">Nom de commande</span><span class="sxs-lookup"><span data-stu-id="aa090-118">Command name</span></span>

<span data-ttu-id="aa090-119">Les commandes commencent toujours par un nom de commande, par exemple `New-Alias` .</span><span class="sxs-lookup"><span data-stu-id="aa090-119">Commands always begin with a command name, such as `New-Alias`.</span></span> <span data-ttu-id="aa090-120">Tapez le nom de la commande ou son alias, par exemple « GCM » pour `Get-Command` .</span><span class="sxs-lookup"><span data-stu-id="aa090-120">Type the command name or its alias, such a "gcm" for `Get-Command`.</span></span>

## <a name="parameters"></a><span data-ttu-id="aa090-121">Paramètres</span><span class="sxs-lookup"><span data-stu-id="aa090-121">Parameters</span></span>

<span data-ttu-id="aa090-122">Les paramètres d’une commande sont des options qui déterminent ce que fait la commande.</span><span class="sxs-lookup"><span data-stu-id="aa090-122">The parameters of a command are options that determine what the command does.</span></span>
<span data-ttu-id="aa090-123">Certains paramètres acceptent une « valeur » qui est l’entrée utilisateur de la commande.</span><span class="sxs-lookup"><span data-stu-id="aa090-123">Some parameters take a "value" which is user input to the command.</span></span>

<span data-ttu-id="aa090-124">Par exemple, la `Get-Help` commande a un paramètre **Name** qui vous permet de spécifier le nom de la rubrique pour laquelle l’aide est affichée.</span><span class="sxs-lookup"><span data-stu-id="aa090-124">For example, the `Get-Help` command has a **Name** parameter that lets you specify the name of the topic for which help is displayed.</span></span> <span data-ttu-id="aa090-125">Le nom de la rubrique est la valeur du paramètre **Name** .</span><span class="sxs-lookup"><span data-stu-id="aa090-125">The topic name is the value of the **Name** parameter.</span></span>

<span data-ttu-id="aa090-126">Dans une commande PowerShell, les noms de paramètres commencent toujours par un trait d’Union.</span><span class="sxs-lookup"><span data-stu-id="aa090-126">In a PowerShell command, parameter names always begin with a hyphen.</span></span>
<span data-ttu-id="aa090-127">Le trait d’Union indique à PowerShell que l’élément dans la commande est un nom de paramètre.</span><span class="sxs-lookup"><span data-stu-id="aa090-127">The hyphen tells PowerShell that the item in the command is a parameter name.</span></span>

<span data-ttu-id="aa090-128">Par exemple, pour utiliser le paramètre Name de `New-Alias` , vous tapez ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="aa090-128">For example, to use the Name parameter of `New-Alias`, you type the following:</span></span>

```powershell
-Name
```

<span data-ttu-id="aa090-129">Les paramètres peuvent être obligatoires ou facultatifs.</span><span class="sxs-lookup"><span data-stu-id="aa090-129">Parameters can be mandatory or optional.</span></span> <span data-ttu-id="aa090-130">Dans un diagramme de syntaxe, les éléments facultatifs sont placés entre crochets `[ ]` .</span><span class="sxs-lookup"><span data-stu-id="aa090-130">In a syntax diagram, optional items are enclosed in brackets `[ ]`.</span></span>

<span data-ttu-id="aa090-131">Pour plus d’informations sur les paramètres, consultez [about_Parameters](about_Parameters.md).</span><span class="sxs-lookup"><span data-stu-id="aa090-131">For more information about parameters, see [about_Parameters](about_Parameters.md).</span></span>

## <a name="parameter-values"></a><span data-ttu-id="aa090-132">Valeurs des paramètres</span><span class="sxs-lookup"><span data-stu-id="aa090-132">Parameter Values</span></span>

<span data-ttu-id="aa090-133">Une valeur de paramètre est l’entrée que le paramètre prend.</span><span class="sxs-lookup"><span data-stu-id="aa090-133">A parameter value is the input that the parameter takes.</span></span> <span data-ttu-id="aa090-134">Étant donné que Windows PowerShell est basé sur le Framework Microsoft .NET, les valeurs des paramètres sont représentées dans le diagramme de syntaxe par leur type .NET.</span><span class="sxs-lookup"><span data-stu-id="aa090-134">Because Windows PowerShell is based on the Microsoft .NET Framework, parameter values are represented in the syntax diagram by their .NET type.</span></span>

<span data-ttu-id="aa090-135">Par exemple, le paramètre Name de `Get-Help` prend une valeur « String », qui est une chaîne de texte, telle qu’un mot unique ou plusieurs mots placés entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="aa090-135">For example, the Name parameter of `Get-Help` takes a "String" value, which is a text string, such as a single word or multiple words enclosed in quotation marks.</span></span>

```powershell
[-Name] <string>
```

<span data-ttu-id="aa090-136">Le type .NET d’une valeur de paramètre est placé entre crochets pointus `< >` pour indiquer qu’il s’agit d’un espace réservé pour une valeur et non d’un littéral que vous tapez dans une commande.</span><span class="sxs-lookup"><span data-stu-id="aa090-136">The .NET type of a parameter value is enclosed in angle brackets `< >` to indicate that it is placeholder for a value and not a literal that you type in a command.</span></span>

<span data-ttu-id="aa090-137">Pour utiliser le paramètre, remplacez l’espace réservé de type .NET par un objet qui a le type .NET spécifié.</span><span class="sxs-lookup"><span data-stu-id="aa090-137">To use the parameter, replace the .NET type placeholder with an object that has the specified .NET type.</span></span>

<span data-ttu-id="aa090-138">Par exemple, pour utiliser le paramètre **Name** , tapez « -Name » suivi d’une chaîne, telle que la suivante :</span><span class="sxs-lookup"><span data-stu-id="aa090-138">For example, to use the **Name** parameter, type "-Name" followed by a string, such as the following:</span></span>

```powershell
-Name MyAlias
```

## <a name="parameters-with-no-values"></a><span data-ttu-id="aa090-139">Paramètres sans valeurs</span><span class="sxs-lookup"><span data-stu-id="aa090-139">Parameters with no values</span></span>

<span data-ttu-id="aa090-140">Certains paramètres n’acceptent pas d’entrée, donc ils n’ont pas de valeur de paramètre.</span><span class="sxs-lookup"><span data-stu-id="aa090-140">Some parameters do not accept input, so they do not have a parameter value.</span></span>
<span data-ttu-id="aa090-141">Les paramètres sans valeurs sont appelés « paramètres de commutateur », car ils fonctionnent comme des commutateurs activés/désactivés.</span><span class="sxs-lookup"><span data-stu-id="aa090-141">Parameters without values are called "switch parameters" because they work like on/off switches.</span></span> <span data-ttu-id="aa090-142">Vous les incluez (sur) ou vous les omettez (OFF) à partir d’une commande.</span><span class="sxs-lookup"><span data-stu-id="aa090-142">You include them (on) or you omit them (off) from a command.</span></span>

<span data-ttu-id="aa090-143">Pour utiliser un paramètre de commutateur, tapez simplement le nom du paramètre, précédé d’un trait d’Union.</span><span class="sxs-lookup"><span data-stu-id="aa090-143">To use a switch parameter, just type the parameter name, preceded by a hyphen.</span></span>

<span data-ttu-id="aa090-144">Par exemple, pour utiliser le paramètre **WhatIf** de l' `New-Alias` applet de commande, tapez ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="aa090-144">For example, to use the **WhatIf** parameter of the `New-Alias` cmdlet, type the following:</span></span>

```powershell
-WhatIf
```

## <a name="parameter-sets"></a><span data-ttu-id="aa090-145">Jeux de paramètres</span><span class="sxs-lookup"><span data-stu-id="aa090-145">Parameter Sets</span></span>

<span data-ttu-id="aa090-146">Les paramètres d’une commande sont répertoriés dans Jeux de paramètres.</span><span class="sxs-lookup"><span data-stu-id="aa090-146">The parameters of a command are listed in parameter sets.</span></span> <span data-ttu-id="aa090-147">Les jeux de paramètres ressemblent aux paragraphes d’un diagramme de syntaxe.</span><span class="sxs-lookup"><span data-stu-id="aa090-147">Parameter sets look like the paragraphs of a syntax diagram.</span></span>

<span data-ttu-id="aa090-148">L' `New-Alias` applet de commande a un jeu de paramètres, mais de nombreuses cmdlets ont plusieurs jeux de paramètres.</span><span class="sxs-lookup"><span data-stu-id="aa090-148">The `New-Alias` cmdlet has one parameter set, but many cmdlets have multiple parameter sets.</span></span> <span data-ttu-id="aa090-149">Certains paramètres d’applet de commande sont uniques à un jeu de paramètres, tandis que d’autres apparaissent dans plusieurs jeux de paramètres.</span><span class="sxs-lookup"><span data-stu-id="aa090-149">Some of the cmdlet parameters are unique to a parameter set, and others appear in multiple parameter sets.</span></span> <span data-ttu-id="aa090-150">Chaque jeu de paramètres représente le format d’une commande valide.</span><span class="sxs-lookup"><span data-stu-id="aa090-150">Each parameter set represents the format of a valid command.</span></span> <span data-ttu-id="aa090-151">Un jeu de paramètres comprend uniquement des paramètres qui peuvent être utilisés ensemble dans une commande.</span><span class="sxs-lookup"><span data-stu-id="aa090-151">A parameter set includes only parameters that can be used together in a command.</span></span> <span data-ttu-id="aa090-152">Si les paramètres ne peuvent pas être utilisés dans la même commande, ils apparaissent dans des jeux de paramètres distincts.</span><span class="sxs-lookup"><span data-stu-id="aa090-152">If parameters cannot be used in the same command, they appear in separate parameter sets.</span></span>

<span data-ttu-id="aa090-153">Par exemple, l’applet de commande [obtenir-Random](xref:Microsoft.PowerShell.Utility.Get-Random) possède les jeux de paramètres suivants :</span><span class="sxs-lookup"><span data-stu-id="aa090-153">For example, the [Get-Random](xref:Microsoft.PowerShell.Utility.Get-Random) cmdlet has the following parameter sets:</span></span>

```powershell
Get-Random [[-Maximum] <Object>] [-Minimum <Object>] [-SetSeed <int>]
[<CommonParameters>]

Get-Random [-InputObject] <Object[]> [-Count <int>] [-SetSeed <int>]
[<CommonParameters>]
```

<span data-ttu-id="aa090-154">Le premier jeu de paramètres, qui retourne un nombre aléatoire, possède les paramètres **minimum** et **maximum** .</span><span class="sxs-lookup"><span data-stu-id="aa090-154">The first parameter set, which returns a random number, has the **Minimum** and **Maximum** parameters.</span></span> <span data-ttu-id="aa090-155">Le deuxième jeu de paramètres, qui retourne un objet sélectionné de manière aléatoire à partir d’un ensemble d’objets, comprend les paramètres **InputObject** et **Count** .</span><span class="sxs-lookup"><span data-stu-id="aa090-155">The second parameter set, which returns a randomly selected object from a set of objects, includes the **InputObject** and **Count** parameters.</span></span> <span data-ttu-id="aa090-156">Les deux jeux de paramètres ont le paramètre **setseed** et les paramètres communs.</span><span class="sxs-lookup"><span data-stu-id="aa090-156">Both parameter sets have the **SetSeed** parameter and the common parameters.</span></span>

<span data-ttu-id="aa090-157">Ces jeux de paramètres indiquent que vous pouvez utiliser les paramètres **InputObject** et **Count** dans la même commande, mais vous ne pouvez pas utiliser les paramètres **maximum** et **Count** dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="aa090-157">These parameter sets indicate that you can use the **InputObject** and **Count** parameters in the same command, but you cannot use the **Maximum** and **Count** parameters in the same command.</span></span>

<span data-ttu-id="aa090-158">Vous indiquez le jeu de paramètres que vous souhaitez utiliser à l’aide des paramètres de ce jeu de paramètres.</span><span class="sxs-lookup"><span data-stu-id="aa090-158">You indicate which parameter set you want to use by using the parameters in that parameter set.</span></span>

<span data-ttu-id="aa090-159">Toutefois, chaque applet de commande possède également un jeu de paramètres par défaut.</span><span class="sxs-lookup"><span data-stu-id="aa090-159">However, every cmdlet also has a default parameter set.</span></span> <span data-ttu-id="aa090-160">Le jeu de paramètres par défaut est utilisé lorsque vous ne spécifiez pas de paramètres propres à un jeu de paramètres.</span><span class="sxs-lookup"><span data-stu-id="aa090-160">The default parameter set is used when you do not specify parameters that are unique to a parameter set.</span></span> <span data-ttu-id="aa090-161">Par exemple, si vous utilisez `Get-Random` sans paramètres, Windows PowerShell part du principe que vous utilisez le jeu de paramètres **Number** et qu’il retourne un nombre aléatoire.</span><span class="sxs-lookup"><span data-stu-id="aa090-161">For example, if you use `Get-Random` without parameters, Windows PowerShell assumes that you are using the **Number** parameter set and it returns a random number.</span></span>

<span data-ttu-id="aa090-162">Dans chaque jeu de paramètres, les paramètres apparaissent dans l’ordre de position.</span><span class="sxs-lookup"><span data-stu-id="aa090-162">In each parameter set, the parameters appear in position order.</span></span> <span data-ttu-id="aa090-163">L’ordre des paramètres dans une commande est important uniquement lorsque vous omettez les noms de paramètres facultatifs.</span><span class="sxs-lookup"><span data-stu-id="aa090-163">The order of parameters in a command matters only when you omit the optional parameter names.</span></span> <span data-ttu-id="aa090-164">Lorsque les noms de paramètres sont omis, PowerShell assigne des valeurs aux paramètres par position et type.</span><span class="sxs-lookup"><span data-stu-id="aa090-164">When parameter names are omitted, PowerShell assigns values to parameters by position and type.</span></span> <span data-ttu-id="aa090-165">Pour plus d’informations sur la position des paramètres, consultez `about_Parameters` .</span><span class="sxs-lookup"><span data-stu-id="aa090-165">For more information about parameter position, see `about_Parameters`.</span></span>

## <a name="symbols-in-syntax-diagrams"></a><span data-ttu-id="aa090-166">Symboles dans les diagrammes de syntaxe</span><span class="sxs-lookup"><span data-stu-id="aa090-166">Symbols in Syntax Diagrams</span></span>

<span data-ttu-id="aa090-167">Le diagramme de syntaxe répertorie le nom de la commande, les paramètres de commande et les valeurs de paramètre.</span><span class="sxs-lookup"><span data-stu-id="aa090-167">The syntax diagram lists the command name, the command parameters, and the parameter values.</span></span> <span data-ttu-id="aa090-168">Il utilise également des symboles pour montrer comment construire une commande valide.</span><span class="sxs-lookup"><span data-stu-id="aa090-168">It also uses symbols to show how to construct a valid command.</span></span>

<span data-ttu-id="aa090-169">Les diagrammes de syntaxe utilisent les symboles suivants :</span><span class="sxs-lookup"><span data-stu-id="aa090-169">The syntax diagrams use the following symbols:</span></span>

- <span data-ttu-id="aa090-170">Un trait d’Union `-` indique un nom de paramètre.</span><span class="sxs-lookup"><span data-stu-id="aa090-170">A hyphen `-` indicates a parameter name.</span></span> <span data-ttu-id="aa090-171">Dans une commande, tapez le trait d’Union juste avant le nom du paramètre sans espaces intermédiaires, comme indiqué dans le diagramme de syntaxe.</span><span class="sxs-lookup"><span data-stu-id="aa090-171">In a command, type the hyphen immediately before the parameter name with no intervening spaces, as shown in the syntax diagram.</span></span>

  <span data-ttu-id="aa090-172">Par exemple, pour utiliser le paramètre **Name** de `New-Alias` , tapez :</span><span class="sxs-lookup"><span data-stu-id="aa090-172">For example, to use the **Name** parameter of `New-Alias`, type:</span></span>

  ```powershell
  -Name
  ```

- <span data-ttu-id="aa090-173">Les chevrons indiquent le texte de l' `<>` espace réservé.</span><span class="sxs-lookup"><span data-stu-id="aa090-173">Angle brackets `<>` indicate placeholder text.</span></span> <span data-ttu-id="aa090-174">Vous ne tapez pas les crochets pointus ni le texte de l’espace réservé dans une commande.</span><span class="sxs-lookup"><span data-stu-id="aa090-174">You do not type the angle brackets or the placeholder text in a command.</span></span> <span data-ttu-id="aa090-175">Au lieu de cela, remplacez-le par l’élément qu’il décrit.</span><span class="sxs-lookup"><span data-stu-id="aa090-175">Instead, you replace it with the item that it describes.</span></span>

  <span data-ttu-id="aa090-176">Les chevrons sont utilisés pour identifier le type .NET de la valeur prise par un paramètre.</span><span class="sxs-lookup"><span data-stu-id="aa090-176">Angle brackets are used to identify the .NET type of the value that a parameter takes.</span></span> <span data-ttu-id="aa090-177">Par exemple, pour utiliser le paramètre **Name** de l' `New-Alias` applet de commande, remplacez `<string>` par une chaîne, qui est un mot unique ou un groupe de mots entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="aa090-177">For example, to use the **Name** parameter of the `New-Alias` cmdlet, you replace the `<string>` with a string, which is a single word or a group of words that are enclosed in quotation marks.</span></span>

- <span data-ttu-id="aa090-178">Les crochets `[ ]` indiquent des éléments facultatifs.</span><span class="sxs-lookup"><span data-stu-id="aa090-178">Brackets `[ ]` indicate optional items.</span></span> <span data-ttu-id="aa090-179">Un paramètre et sa valeur peuvent être facultatifs, ou le nom d’un paramètre requis peut être facultatif.</span><span class="sxs-lookup"><span data-stu-id="aa090-179">A parameter and its value can be optional, or the name of a required parameter can be optional.</span></span>

  <span data-ttu-id="aa090-180">Par exemple, le paramètre **Description** de `New-Alias` et sa valeur sont placés entre crochets, car ils sont tous deux facultatifs.</span><span class="sxs-lookup"><span data-stu-id="aa090-180">For example, the **Description** parameter of `New-Alias` and its value are enclosed in brackets because they are both optional.</span></span>

  ```powershell
  [-Description <string>]
  ```

  <span data-ttu-id="aa090-181">Les crochets indiquent également que la valeur du paramètre name `<string>` est obligatoire, mais le nom du paramètre, « Name », est facultatif.</span><span class="sxs-lookup"><span data-stu-id="aa090-181">The brackets also indicate that the Name parameter value `<string>` is required, but the parameter name, "Name", is optional.</span></span>

  ```powershell
  [-Name] <string>
  ```

- <span data-ttu-id="aa090-182">Un crochet droit et un crochet gauche `[]` ajoutés à un type .net indiquent que le paramètre peut accepter une ou plusieurs valeurs de ce type.</span><span class="sxs-lookup"><span data-stu-id="aa090-182">A right and left bracket `[]` appended to a .NET type indicates that the parameter can accept one or multiple values of that type.</span></span> <span data-ttu-id="aa090-183">Entrez les valeurs dans une liste séparée par des virgules.</span><span class="sxs-lookup"><span data-stu-id="aa090-183">Enter the values in a comma-separated list.</span></span>

  <span data-ttu-id="aa090-184">Par exemple, le paramètre **Name** de l' `New-Alias` applet de commande ne prend qu’une seule chaîne, mais le paramètre **Name** de l’applet de commande [obtient-process](xref:Microsoft.PowerShell.Management.Get-Process) peut prendre une ou plusieurs chaînes.</span><span class="sxs-lookup"><span data-stu-id="aa090-184">For example, the **Name** parameter of the `New-Alias` cmdlet takes only one string, but the **Name** parameter of [Get-Process](xref:Microsoft.PowerShell.Management.Get-Process) can take one or many strings.</span></span>

  ```powershell
  New-Alias [-Name] <string>

  New-Alias -Name MyAlias
  ```

  ```powershell
  Get-Process [-Name] <string[]>

  Get-Process -Name Explorer, Winlogon, Services
  ```

- <span data-ttu-id="aa090-185">Les accolades `{}` indiquent une « énumération », qui est un ensemble de valeurs valides pour un paramètre.</span><span class="sxs-lookup"><span data-stu-id="aa090-185">Braces `{}` indicate an "enumeration," which is a set of valid values for a parameter.</span></span>

  <span data-ttu-id="aa090-186">Les valeurs entre les accolades sont séparées par des barres verticales `|` .</span><span class="sxs-lookup"><span data-stu-id="aa090-186">The values in the braces are separated by vertical bars `|`.</span></span> <span data-ttu-id="aa090-187">Ces barres indiquent un choix « exclusif ou », ce qui signifie que vous ne pouvez choisir qu’une seule valeur de l’ensemble de valeurs qui sont répertoriées à l’intérieur des accolades.</span><span class="sxs-lookup"><span data-stu-id="aa090-187">These bars indicate an "exclusive OR" choice, meaning that you can choose only one value from the set of values that are listed inside the braces.</span></span>

  <span data-ttu-id="aa090-188">Par exemple, la syntaxe de l' `New-Alias` applet de **commande** comprend l’énumération value suivante pour le paramètre option :</span><span class="sxs-lookup"><span data-stu-id="aa090-188">For example, the syntax for the `New-Alias` cmdlet includes the following value enumeration for the **Option** parameter:</span></span>

  ```powershell
  -Option {None | ReadOnly | Constant | Private | AllScope}
  ```

  <span data-ttu-id="aa090-189">Les accolades et les barres verticales indiquent que vous pouvez choisir l’une des valeurs listées pour le paramètre **option** , par exemple « ReadOnly » ou « options AllScope ».</span><span class="sxs-lookup"><span data-stu-id="aa090-189">The braces and vertical bars indicate that you can choose any one of the listed values for the **Option** parameter, such as "ReadOnly" or "AllScope".</span></span>

  ```powershell
  -Option ReadOnly
  ```

## <a name="optional-items"></a><span data-ttu-id="aa090-190">Éléments facultatifs</span><span class="sxs-lookup"><span data-stu-id="aa090-190">Optional Items</span></span>

<span data-ttu-id="aa090-191">Les crochets `[]` entourent les éléments facultatifs.</span><span class="sxs-lookup"><span data-stu-id="aa090-191">Brackets `[]` surround optional items.</span></span> <span data-ttu-id="aa090-192">Par exemple, dans la description de la syntaxe de l’applet de commande `New-Alias` , le paramètre **scope** est facultatif.</span><span class="sxs-lookup"><span data-stu-id="aa090-192">For example, in the `New-Alias` cmdlet syntax description, the **Scope** parameter is optional.</span></span> <span data-ttu-id="aa090-193">Cela est indiqué dans la syntaxe par des crochets autour du nom et du type de paramètre :</span><span class="sxs-lookup"><span data-stu-id="aa090-193">This is indicated in the syntax by the brackets around the parameter name and type:</span></span>

```powershell
[-Scope <string>]
```

<span data-ttu-id="aa090-194">Les deux exemples suivants sont des utilisations correctes de l’applet de commande `New-Alias` :</span><span class="sxs-lookup"><span data-stu-id="aa090-194">Both the following examples are correct uses of the `New-Alias` cmdlet:</span></span>

```powershell
New-Alias -Name utd -Value Update-TypeData
New-Alias -Name utd -Value Update-TypeData -Scope Global
```

<span data-ttu-id="aa090-195">Un nom de paramètre peut être facultatif même si la valeur de ce paramètre est requise.</span><span class="sxs-lookup"><span data-stu-id="aa090-195">A parameter name can be optional even if the value for that parameter is required.</span></span> <span data-ttu-id="aa090-196">Cela est indiqué dans la syntaxe par des crochets autour du nom du paramètre, mais pas du type de paramètre, comme dans cet exemple de l’applet de commande `New-Alias` :</span><span class="sxs-lookup"><span data-stu-id="aa090-196">This is indicated in the syntax by the brackets around the parameter name but not the parameter type, as in this example from the `New-Alias` cmdlet:</span></span>

```powershell
[-Name] <string> [-Value] <string>
```

<span data-ttu-id="aa090-197">Les commandes suivantes utilisent correctement l' `New-Alias` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="aa090-197">The following commands correctly use the `New-Alias` cmdlet.</span></span> <span data-ttu-id="aa090-198">Les commandes produisent le même résultat.</span><span class="sxs-lookup"><span data-stu-id="aa090-198">The commands produce the same result.</span></span>

```powershell
New-Alias -Name utd -Value Update-TypeData
New-Alias -Name utd Update-TypeData
New-Alias utd -Value Update-TypeData
New-Alias utd Update-TypeData
```

<span data-ttu-id="aa090-199">Si le nom du paramètre n’est pas inclus dans l’instruction comme étant typé, Windows PowerShell essaie d’utiliser la position des arguments pour assigner les valeurs aux paramètres.</span><span class="sxs-lookup"><span data-stu-id="aa090-199">If the parameter name is not included in the statement as typed, Windows PowerShell tries to use the position of the arguments to assign the values to parameters.</span></span>

<span data-ttu-id="aa090-200">L’exemple suivant n’est pas complet :</span><span class="sxs-lookup"><span data-stu-id="aa090-200">The following example is not complete:</span></span>

```powershell
New-Alias utd
```

<span data-ttu-id="aa090-201">Cette applet de commande requiert des valeurs pour les paramètres **Name** et **value** .</span><span class="sxs-lookup"><span data-stu-id="aa090-201">This cmdlet requires values for both the **Name** and **Value** parameters.</span></span>

<span data-ttu-id="aa090-202">Dans les exemples de syntaxe, les crochets sont également utilisés pour nommer et effectuer un cast en types .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="aa090-202">In syntax examples, brackets are also used in naming and casting to .NET Framework types.</span></span> <span data-ttu-id="aa090-203">Dans ce contexte, les crochets n’indiquent pas qu’un élément est facultatif.</span><span class="sxs-lookup"><span data-stu-id="aa090-203">In this context, brackets do not indicate an element is optional.</span></span>

## <a name="see-also"></a><span data-ttu-id="aa090-204">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="aa090-204">SEE ALSO</span></span>

- [<span data-ttu-id="aa090-205">about_Parameters</span><span class="sxs-lookup"><span data-stu-id="aa090-205">about_Parameters</span></span>](about_Parameters.md)
- [<span data-ttu-id="aa090-206">Get-Command</span><span class="sxs-lookup"><span data-stu-id="aa090-206">Get-Command</span></span>](xref:Microsoft.PowerShell.Core.Get-Command)
- [<span data-ttu-id="aa090-207">Get-Help</span><span class="sxs-lookup"><span data-stu-id="aa090-207">Get-Help</span></span>](xref:Microsoft.PowerShell.Core.Get-Help)

