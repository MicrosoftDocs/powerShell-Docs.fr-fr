---
ms.date: 08/27/2018
keywords: powershell,applet de commande
title: Obtention d’informations d’aide détaillées
ms.openlocfilehash: 3f52de8c9963618c154b119d5f4859a92d61fbda
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030402"
---
# <a name="getting-detailed-help-information"></a><span data-ttu-id="3dfe1-103">Obtention d’informations d’aide détaillées</span><span class="sxs-lookup"><span data-stu-id="3dfe1-103">Getting detailed help information</span></span>

<span data-ttu-id="3dfe1-104">PowerShell inclut des articles d’aide détaillés qui expliquent les concepts de PowerShell et le langage PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3dfe1-104">PowerShell includes detailed Help articles that explain PowerShell concepts and the PowerShell language.</span></span> <span data-ttu-id="3dfe1-105">Il existe également des articles d’aide pour chaque cmdlet et fournisseur, et pour un grand nombre de fonctions et de scripts.</span><span class="sxs-lookup"><span data-stu-id="3dfe1-105">There are also Help articles for each cmdlet and provider and for many functions and scripts.</span></span>

<span data-ttu-id="3dfe1-106">Vous pouvez afficher ces articles d’aide à l’invite de commandes, ou afficher les versions les plus récemment mises à jour de ces articles dans la documentation [PowerShell](/powershell/scripting/overview) en ligne.</span><span class="sxs-lookup"><span data-stu-id="3dfe1-106">You can display these Help articles at the command prompt or view the most recently updated versions of these articles in the [PowerShell](/powershell/scripting/overview) documentation online.</span></span>

## <a name="getting-help-for-cmdlets"></a><span data-ttu-id="3dfe1-107">Obtention d’aide sur les cmdlets</span><span class="sxs-lookup"><span data-stu-id="3dfe1-107">Getting help for cmdlets</span></span>

<span data-ttu-id="3dfe1-108">Pour obtenir de l’aide sur les cmdlets PowerShell, utilisez la cmdlet [Get-Help](/powershell/module/microsoft.powershell.core/Get-Help).</span><span class="sxs-lookup"><span data-stu-id="3dfe1-108">To get Help about PowerShell cmdlets, use the [Get-Help](/powershell/module/microsoft.powershell.core/Get-Help) cmdlet.</span></span> <span data-ttu-id="3dfe1-109">Par exemple, pour obtenir de l’aide sur la cmdlet `Get-ChildItem` :</span><span class="sxs-lookup"><span data-stu-id="3dfe1-109">For example, to get Help for the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem
```

<span data-ttu-id="3dfe1-110">ou</span><span class="sxs-lookup"><span data-stu-id="3dfe1-110">or</span></span>

```powershell
Get-ChildItem -?
```

<span data-ttu-id="3dfe1-111">Vous pouvez même obtenir de l’aide sur l’applet de commande Get-Help.</span><span class="sxs-lookup"><span data-stu-id="3dfe1-111">You can even get Help about the Get-Help cmdlet.</span></span> <span data-ttu-id="3dfe1-112">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="3dfe1-112">For example:</span></span>

```powershell
Get-Help Get-Help
```

<span data-ttu-id="3dfe1-113">Pour obtenir la liste de tous les articles d’aide sur la cmdlet dans votre session, tapez :</span><span class="sxs-lookup"><span data-stu-id="3dfe1-113">To get a list of all the cmdlet Help articles in your session, type:</span></span>

```powershell
Get-Help -Category Cmdlet
```

<span data-ttu-id="3dfe1-114">Pour afficher une page de chaque article d’aide à la fois, utilisez la fonction `help` ou son alias `man`.</span><span class="sxs-lookup"><span data-stu-id="3dfe1-114">To display one page of each Help article at a time, use the `help` function or its alias `man`.</span></span>
<span data-ttu-id="3dfe1-115">Par exemple, pour afficher l’aide concernant la cmdlet `Get-ChildItem`, tapez</span><span class="sxs-lookup"><span data-stu-id="3dfe1-115">For example, to display Help for the `Get-ChildItem` cmdlet, type</span></span>

```powershell
man Get-ChildItem
```

<span data-ttu-id="3dfe1-116">ou</span><span class="sxs-lookup"><span data-stu-id="3dfe1-116">or</span></span>

```powershell
help Get-ChildItem
```

<span data-ttu-id="3dfe1-117">Pour afficher des informations détaillées, utilisez le paramètre **Detailed** de la cmdlet `Get-Help`.</span><span class="sxs-lookup"><span data-stu-id="3dfe1-117">To display detailed information, use the **Detailed** parameter of the `Get-Help` cmdlet.</span></span> <span data-ttu-id="3dfe1-118">Par exemple, pour obtenir des informations détaillées sur la cmdlet `Get-ChildItem`, tapez :</span><span class="sxs-lookup"><span data-stu-id="3dfe1-118">For example, to get detailed information about the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Detailed
```

<span data-ttu-id="3dfe1-119">Pour afficher tout le contenu de l’article d’aide, utilisez le paramètre **Full** de la cmdlet `Get-Help`.</span><span class="sxs-lookup"><span data-stu-id="3dfe1-119">To display all content in the Help article, use the **Full** parameter of the `Get-Help` cmdlet.</span></span> <span data-ttu-id="3dfe1-120">Par exemple, pour afficher tout le contenu de l’article d’aide pour la cmdlet `Get-ChildItem`, tapez :</span><span class="sxs-lookup"><span data-stu-id="3dfe1-120">For example, to display all content in the Help article for the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Full
```

<span data-ttu-id="3dfe1-121">Pour obtenir une aide détaillée sur les paramètres d’une cmdlet, utilisez le paramètre **Parameter** de la cmdlet `Get-Help`.</span><span class="sxs-lookup"><span data-stu-id="3dfe1-121">To get detailed Help about the parameters of a cmdlet, use the **Parameter** parameter of the `Get-Help` cmdlet.</span></span> <span data-ttu-id="3dfe1-122">Par exemple, pour obtenir une aide détaillée sur tous les paramètres de la cmdlet `Get-ChildItem`, tapez :</span><span class="sxs-lookup"><span data-stu-id="3dfe1-122">For example, to get detailed Help for all of the parameters of the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Parameter *
```

<span data-ttu-id="3dfe1-123">Pour afficher uniquement les exemples d’un article d’aide, utilisez le paramètre **Example** de la cmdlet `Get-Help`.</span><span class="sxs-lookup"><span data-stu-id="3dfe1-123">To display only the examples in a Help article, use the **Examples** parameter of the `Get-Help`.</span></span>
<span data-ttu-id="3dfe1-124">Par exemple, pour afficher uniquement les exemples de l’article d’aide pour l’applet de commande `Get-ChildItem`, tapez :</span><span class="sxs-lookup"><span data-stu-id="3dfe1-124">For example, to display only the examples in the Help article for the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Examples
```

<span data-ttu-id="3dfe1-125">Pour plus d’informations sur la manière de rédiger des articles d’aide sur les cmdlets que vous écrivez, consultez [How to Write Cmdlet Help](/powershell/developer/help/writing-help-for-windows-powershell-cmdlets).</span><span class="sxs-lookup"><span data-stu-id="3dfe1-125">For information about how to write Help articles for the cmdlets that you write, see [How to Write Cmdlet Help](/powershell/developer/help/writing-help-for-windows-powershell-cmdlets).</span></span>

## <a name="getting-conceptual-help"></a><span data-ttu-id="3dfe1-126">Obtention d’aide conceptuelle</span><span class="sxs-lookup"><span data-stu-id="3dfe1-126">Getting conceptual help</span></span>

<span data-ttu-id="3dfe1-127">La cmdlet `Get-Help` affiche également des informations sur des articles conceptuels dans PowerShell, dont des articles sur le langage PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3dfe1-127">The `Get-Help` cmdlet also displays information about conceptual articles in PowerShell, including articles about the PowerShell language.</span></span> <span data-ttu-id="3dfe1-128">Les articles d’aide conceptuelle commencent par le préfixe « about_ », par exemple, « about_line_editing ».</span><span class="sxs-lookup"><span data-stu-id="3dfe1-128">Conceptual Help articles begin with the "about_" prefix, such as about_line_editing.</span></span> <span data-ttu-id="3dfe1-129">(Le nom de l’article conceptuel doit être saisi en anglais, même dans les versions non anglaises de PowerShell.)</span><span class="sxs-lookup"><span data-stu-id="3dfe1-129">(The name of the conceptual article must be entered in English even on non-English versions of PowerShell.)</span></span>

<span data-ttu-id="3dfe1-130">Pour afficher la liste des articles conceptuels, tapez :</span><span class="sxs-lookup"><span data-stu-id="3dfe1-130">To display a list of conceptual articles, type:</span></span>

```powershell
Get-Help about_*
```

<span data-ttu-id="3dfe1-131">Pour afficher un article d’aide spécifique, tapez son nom, par exemple :</span><span class="sxs-lookup"><span data-stu-id="3dfe1-131">To display a particular Help article, type the article name, for example:</span></span>

```powershell
Get-Help about_command_syntax
```

<span data-ttu-id="3dfe1-132">Les paramètres de la cmdlet `Get-Help`, tels que **Detailed**, **Parameter** et **Examples**, n’ont aucune incidence sur l’affichage des articles d’aide conceptuelle.</span><span class="sxs-lookup"><span data-stu-id="3dfe1-132">The parameters of `Get-Help`, such as **Detailed**, **Parameter**, and **Examples**, have no effect on the display of conceptual Help articles.</span></span>

## <a name="getting-help-about-providers"></a><span data-ttu-id="3dfe1-133">Obtention d’aide sur les fournisseurs</span><span class="sxs-lookup"><span data-stu-id="3dfe1-133">Getting help about providers</span></span>

<span data-ttu-id="3dfe1-134">La cmdlet `Get-Help` affiche des informations sur les fournisseurs PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3dfe1-134">The `Get-Help` cmdlet displays information about PowerShell providers.</span></span> <span data-ttu-id="3dfe1-135">Pour obtenir de l’aide sur un fournisseur, tapez `Get-Help`, suivi du nom du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="3dfe1-135">To get Help for a provider, type `Get-Help` followed by the provider name.</span></span> <span data-ttu-id="3dfe1-136">Par exemple, pour obtenir de l’aide sur le fournisseur de Registre, tapez :</span><span class="sxs-lookup"><span data-stu-id="3dfe1-136">For example, to get Help for the Registry provider, type:</span></span>

```powershell
Get-Help registry
```

<span data-ttu-id="3dfe1-137">Pour obtenir la liste de tous les articles d’aide sur le fournisseur dans votre session, tapez</span><span class="sxs-lookup"><span data-stu-id="3dfe1-137">To get a list of all the provider Help articles in your session, type</span></span>

```powershell
Get-Help -Category provider
```

<span data-ttu-id="3dfe1-138">Les paramètres de la cmdlet `Get-Help`, tels que **Detailed**, **Parameter** et **Examples**, n’ont aucune incidence sur l’affichage des articles d’aide sur le fournisseur.</span><span class="sxs-lookup"><span data-stu-id="3dfe1-138">The parameters of `Get-Help`, such as **Detailed**, **Parameter**, and **Examples**, have no effect on the display of provider Help articles.</span></span>

## <a name="getting-help-about-scripts-and-functions"></a><span data-ttu-id="3dfe1-139">Obtention d’aide sur les fonctions et les scripts</span><span class="sxs-lookup"><span data-stu-id="3dfe1-139">Getting help about scripts and functions</span></span>

<span data-ttu-id="3dfe1-140">De nombreux scripts et fonctions dans PowerShell ont des articles d’aide associés.</span><span class="sxs-lookup"><span data-stu-id="3dfe1-140">Many scripts and functions in PowerShell have Help articles.</span></span> <span data-ttu-id="3dfe1-141">Utilisez la cmdlet `Get-Help` pour afficher les articles d’aide sur les scripts et fonctions.</span><span class="sxs-lookup"><span data-stu-id="3dfe1-141">Use the `Get-Help` cmdlet to display the Help articles for scripts and functions.</span></span>

<span data-ttu-id="3dfe1-142">Pour afficher l’aide sur une fonction, tapez `Get-Help`, suivi du nom de la fonction.</span><span class="sxs-lookup"><span data-stu-id="3dfe1-142">To display the Help for a function, type `Get-Help` followed by the function name.</span></span> <span data-ttu-id="3dfe1-143">Par exemple, pour obtenir de l’aide sur la fonction `Disable-PSRemoting`, tapez :</span><span class="sxs-lookup"><span data-stu-id="3dfe1-143">For example, to get Help for the `Disable-PSRemoting` function, type:</span></span>

```powershell
Get-Help Disable-PSRemoting
```

<span data-ttu-id="3dfe1-144">Pour afficher l’aide sur un script, tapez le chemin d’accès au fichier de script.</span><span class="sxs-lookup"><span data-stu-id="3dfe1-144">To display the Help for a script, type the path to the script file.</span></span> <span data-ttu-id="3dfe1-145">Si le script n’est pas dans un chemin d’accès répertorié dans la variable d’environnement Path, vous devez utiliser le chemin d’accès qualifié complet.</span><span class="sxs-lookup"><span data-stu-id="3dfe1-145">If the script is not in a path listed in the Path environment variable, you must use the fully qualified path.</span></span>

<span data-ttu-id="3dfe1-146">Par exemple, si vous avez un script nommé « TestScript.ps1 » dans le répertoire C:\\PS-Test, pour afficher l’article d’aide sur le script, tapez :</span><span class="sxs-lookup"><span data-stu-id="3dfe1-146">For example, if you have a script called "TestScript.ps1" in your C:\\PS-Test directory, to display the Help article for the script, type:</span></span>

```powershell
Get-Help c:\ps-test\TestScript.ps1
```

<span data-ttu-id="3dfe1-147">Les paramètres qui sont conçus pour afficher l’aide sur la cmdlet fonctionnent aussi pour l’aide sur le script et la fonction.</span><span class="sxs-lookup"><span data-stu-id="3dfe1-147">The parameters that are designed for displaying cmdlet Help work for script and function Help, too.</span></span> <span data-ttu-id="3dfe1-148">Toutefois, l’aide sur les fonctions et les scripts ne s’affiche pas lorsque vous exécutez `Get-Help *`.</span><span class="sxs-lookup"><span data-stu-id="3dfe1-148">However, help for functions and scripts is not shown when you run `Get-Help *`.</span></span>

<span data-ttu-id="3dfe1-149">Pour plus d’informations sur l’écriture d’articles d’aide pour vos fonctions et vos scripts, consultez les articles suivants :</span><span class="sxs-lookup"><span data-stu-id="3dfe1-149">For information about writing Help articles for your functions and scripts, see the following articles:</span></span>

- [<span data-ttu-id="3dfe1-150">about_Functions</span><span class="sxs-lookup"><span data-stu-id="3dfe1-150">about_Functions</span></span>](/powershell/module/microsoft.powershell.core/about/about_functions)
- [<span data-ttu-id="3dfe1-151">about_Scripts</span><span class="sxs-lookup"><span data-stu-id="3dfe1-151">about_Scripts</span></span>](/powershell/module/microsoft.powershell.core/about/about_scripts)
- [<span data-ttu-id="3dfe1-152">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="3dfe1-152">about_Comment_Based_Help</span></span>](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)

## <a name="getting-help-online"></a><span data-ttu-id="3dfe1-153">Obtention d’aide en ligne</span><span class="sxs-lookup"><span data-stu-id="3dfe1-153">Getting help online</span></span>

<span data-ttu-id="3dfe1-154">Afficher les articles d’aide en ligne est l’une des meilleures façons d’obtenir de l’aide.</span><span class="sxs-lookup"><span data-stu-id="3dfe1-154">Viewing the Help articles online is one of the best ways to get help.</span></span> <span data-ttu-id="3dfe1-155">Les articles en ligne sont plus faciles à mettre à jour et fournissent le contenu le plus récent.</span><span class="sxs-lookup"><span data-stu-id="3dfe1-155">Online articles are easier to update and provide the most current content.</span></span>

<span data-ttu-id="3dfe1-156">Pour obtenir l’aide en ligne, utilisez le paramètre **Online** de la cmdlet `Get-Help`.</span><span class="sxs-lookup"><span data-stu-id="3dfe1-156">To get Help online, use the **Online** parameter of the `Get-Help` cmdlet.</span></span> <span data-ttu-id="3dfe1-157">Tous les articles d’aide fournis avec PowerShell, y compris les articles d’aide sur le fournisseur et les articles d’aide conceptuelle (À propos), sont disponibles en ligne dans la documentation [PowerShell](/powershell/scripting/powershell-scripting).</span><span class="sxs-lookup"><span data-stu-id="3dfe1-157">All the Help articles that come with PowerShell, including provider Help and conceptual (About) Help articles, are available online in the [PowerShell](/powershell/scripting/powershell-scripting) documentation.</span></span>

> [!NOTE]
> <span data-ttu-id="3dfe1-158">Vous ne pouvez pas utiliser le paramètre **Online** avec des articles d’aide conceptuelle (about_\*) ou des articles d’aide du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="3dfe1-158">You can't use the **Online** parameter with conceptual (about_\*) or provider Help articles.</span></span>
> <span data-ttu-id="3dfe1-159">L’aide en ligne est facultative, donc elle ne fonctionne pas pour chaque cmdlet, fonction ou script.</span><span class="sxs-lookup"><span data-stu-id="3dfe1-159">Online help is optional, so it does not work for every cmdlet, function, or script.</span></span>

<span data-ttu-id="3dfe1-160">Par exemple, pour obtenir la version en ligne de l’article d’aide sur la cmdlet `Get-ChildItem`, tapez :</span><span class="sxs-lookup"><span data-stu-id="3dfe1-160">For example, to get the online version of the Help article about the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Online
```

<span data-ttu-id="3dfe1-161">PowerShell ouvre l’article dans votre navigateur par défaut.</span><span class="sxs-lookup"><span data-stu-id="3dfe1-161">PowerShell opens the article in your default browser.</span></span> <span data-ttu-id="3dfe1-162">Si l’aide en ligne est prise en charge pour un article d’aide, vous pouvez également afficher l’URL de l’article d’aide.</span><span class="sxs-lookup"><span data-stu-id="3dfe1-162">If online Help is supported for a Help article, you can also view the URL of the Help article.</span></span> <span data-ttu-id="3dfe1-163">L’URL apparaît dans la section Liens connexes d’un article d’aide.</span><span class="sxs-lookup"><span data-stu-id="3dfe1-163">The URL appears in the Related Links section of a Help article.</span></span>

<span data-ttu-id="3dfe1-164">Par exemple, pour afficher l’URL de la version en ligne de l’applet de commande Add-Computer, tapez :</span><span class="sxs-lookup"><span data-stu-id="3dfe1-164">For example, to see the URL for the online version of the Add-Computer cmdlet, type:</span></span>

```powershell
Get-Help Add-Computer
```

<span data-ttu-id="3dfe1-165">La première ligne de la section Liens connexes de l’article est présentée ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="3dfe1-165">The first line in the Related Links section of the article is shown below.</span></span>

```Output
Online version: http://go.microsoft.com/fwlink/?LinkId=821564
```

<span data-ttu-id="3dfe1-166">Pour plus d’informations sur la façon de fournir un support en ligne pour vos articles d’aide, consultez [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).</span><span class="sxs-lookup"><span data-stu-id="3dfe1-166">For information about how to provide online support for your Help articles, see [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).</span></span>

## <a name="see-also"></a><span data-ttu-id="3dfe1-167">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3dfe1-167">See also</span></span>

- [<span data-ttu-id="3dfe1-168">about_Functions</span><span class="sxs-lookup"><span data-stu-id="3dfe1-168">about_Functions</span></span>](/powershell/module/microsoft.powershell.core/about/about_functions)
- [<span data-ttu-id="3dfe1-169">about_Scripts</span><span class="sxs-lookup"><span data-stu-id="3dfe1-169">about_Scripts</span></span>](/powershell/module/microsoft.powershell.core/about/about_scripts)
- [<span data-ttu-id="3dfe1-170">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="3dfe1-170">about_Comment_Based_Help</span></span>](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)
- [<span data-ttu-id="3dfe1-171">Get-Help</span><span class="sxs-lookup"><span data-stu-id="3dfe1-171">Get-Help</span></span>](/powershell/module/microsoft.powershell.core/get-help)
