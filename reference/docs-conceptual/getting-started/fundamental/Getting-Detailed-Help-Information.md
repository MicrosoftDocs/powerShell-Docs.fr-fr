---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Obtention d’informations d’aide détaillées
ms.assetid: 6fb4daf7-8607-4a3e-b692-f77631adc1b9
ms.openlocfilehash: 29c24af3f688f9388893044952442910e793842d
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2018
ms.locfileid: "34483030"
---
# <a name="getting-detailed-help-information"></a><span data-ttu-id="de4c5-103">Obtention d’informations d’aide détaillées</span><span class="sxs-lookup"><span data-stu-id="de4c5-103">Getting Detailed Help Information</span></span>
<span data-ttu-id="de4c5-104">Windows PowerShell inclut des rubriques d’aide détaillées qui expliquent les concepts de Windows PowerShell et le langage Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="de4c5-104">Windows PowerShell includes detailed Help topics that explain Windows PowerShell concepts and the Windows PowerShell language.</span></span> <span data-ttu-id="de4c5-105">Il existe également des rubriques d’aide pour chaque applet de commande et fournisseur, et des rubriques d’aide pour un grand nombre de fonctions et de scripts.</span><span class="sxs-lookup"><span data-stu-id="de4c5-105">There are also Help topics for each cmdlet and provider and Help topics for many functions and scripts.</span></span>

<span data-ttu-id="de4c5-106">Vous pouvez afficher ces rubriques d’aide à l’invite de commandes, ou afficher les versions les plus récemment mises à jour de ces rubriques dans la Bibliothèque Microsoft TechNet.</span><span class="sxs-lookup"><span data-stu-id="de4c5-106">You can display these Help topics at the command prompt or view the most recently updated versions of these topics in the Microsoft TechNet Library.</span></span> <span data-ttu-id="de4c5-107">De nombreux programmes hébergeant Windows PowerShell, comme l’environnement d’écriture de scripts intégré de Windows PowerShell, fournissent des fonctionnalités d’aide supplémentaires, telles qu’une aide contextuelle et un fichier d’aide compilé (.chm).</span><span class="sxs-lookup"><span data-stu-id="de4c5-107">Many programs that host Windows PowerShell, such as Windows PowerShell Integrated Scripting Environment, provide additional Help features, such as context-sensitive Help and compiled Help file (.chm).</span></span>

## <a name="getting-help-for-cmdlets"></a><span data-ttu-id="de4c5-108">Obtention d’aide sur les applets de commande</span><span class="sxs-lookup"><span data-stu-id="de4c5-108">Getting Help for Cmdlets</span></span>
<span data-ttu-id="de4c5-109">Pour obtenir de l’aide sur les applets de commande Windows PowerShell, utilisez l’applet de commande [Get-Help [m2]](https://technet.microsoft.com/library/2d7fe1b4-0025-4580-a911-d81922dd6cd2).</span><span class="sxs-lookup"><span data-stu-id="de4c5-109">To get Help about Windows PowerShell cmdlets, use the [Get-Help [m2]](https://technet.microsoft.com/library/2d7fe1b4-0025-4580-a911-d81922dd6cd2) cmdlet.</span></span> <span data-ttu-id="de4c5-110">Par exemple, pour obtenir de l’aide sur l’applet de commande [Get-ChildItem [m2]](https://technet.microsoft.com/library/4b270d63-c995-45b8-b5b4-3f8887efbfcc), tapez :</span><span class="sxs-lookup"><span data-stu-id="de4c5-110">For example, to get Help for the [Get-ChildItem [m2]](https://technet.microsoft.com/library/4b270d63-c995-45b8-b5b4-3f8887efbfcc) cmdlet, type:</span></span>

```
get-help get-childitem
```

<span data-ttu-id="de4c5-111">ou</span><span class="sxs-lookup"><span data-stu-id="de4c5-111">or</span></span>

```
get-childitem -?
```

<span data-ttu-id="de4c5-112">Vous pouvez même obtenir de l’aide sur l’applet de commande Get-Help.</span><span class="sxs-lookup"><span data-stu-id="de4c5-112">You can even get Help about the Get-Help cmdlet.</span></span> <span data-ttu-id="de4c5-113">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="de4c5-113">For example:</span></span>

```
get-help get-help
```

<span data-ttu-id="de4c5-114">Pour obtenir la liste de toutes les rubriques d’aide sur l’applet de commande dans votre session, tapez :</span><span class="sxs-lookup"><span data-stu-id="de4c5-114">To get a list of all the cmdlet Help topics in your session, type:</span></span>

```
get-help -category cmdlet
```

<span data-ttu-id="de4c5-115">Pour afficher une page de chaque rubrique d’aide à la fois, utilisez la fonction **help** ou son alias **man**.</span><span class="sxs-lookup"><span data-stu-id="de4c5-115">To display one page of each Help topic at a time, use the **help** function or its alias **man**.</span></span> <span data-ttu-id="de4c5-116">Par exemple, pour afficher l’aide sur l’applet de commande Get-ChildItem, tapez :</span><span class="sxs-lookup"><span data-stu-id="de4c5-116">For example, to display Help for the Get-ChildItem cmdlet, type</span></span>

```
man get-childitem
```

<span data-ttu-id="de4c5-117">ou</span><span class="sxs-lookup"><span data-stu-id="de4c5-117">or</span></span>

```
help get-childitem
```

<span data-ttu-id="de4c5-118">Pour afficher des informations détaillées sur une applet de commande, une fonction ou un script, notamment des descriptions de ses paramètres et des exemples de son utilisation, utilisez le paramètre *Detailed* de l’applet de commande Get-Help.</span><span class="sxs-lookup"><span data-stu-id="de4c5-118">To display detailed information about a cmdlet, function, or script, including descriptions of its parameters and examples of its use, use the *Detailed* parameter of the Get-Help cmdlet.</span></span> <span data-ttu-id="de4c5-119">Par exemple, pour obtenir des informations détaillées sur l’applet de commande Get-ChildItem, tapez :</span><span class="sxs-lookup"><span data-stu-id="de4c5-119">For example, to get detailed information about the Get-ChildItem cmdlet, type:</span></span>

```
get-help get-childitem -detailed
```

<span data-ttu-id="de4c5-120">Pour afficher tout le contenu de la rubrique d’aide, utilisez le paramètre *Full* de l’applet de commande Get-Help.</span><span class="sxs-lookup"><span data-stu-id="de4c5-120">To display all content in the Help topic, use the *Full* parameter of the Get-Help cmdlet.</span></span> <span data-ttu-id="de4c5-121">Par exemple, pour afficher tout le contenu de la rubrique d’aide pour l’applet de commande Get-ChildItem, tapez :</span><span class="sxs-lookup"><span data-stu-id="de4c5-121">For example, to display all content in the Help topic for the Get-ChildItem cmdlet, type:</span></span>

```
get-help get-childitem -full
```

<span data-ttu-id="de4c5-122">Pour obtenir une aide détaillée sur les paramètres d’une applet de commande, utilisez le paramètre *Parameter* de l’applet de commande Get-Help.</span><span class="sxs-lookup"><span data-stu-id="de4c5-122">To get detailed Help about the parameters of a cmdlet, use the *Parameter* parameter of the Get-Help cmdlet.</span></span> <span data-ttu-id="de4c5-123">Par exemple, pour obtenir une aide détaillée sur tous les paramètres de l’applet de commande Get-ChildItem, tapez :</span><span class="sxs-lookup"><span data-stu-id="de4c5-123">For example, to get detailed Help for all of the parameters of the Get-ChildItem cmdlet, type:</span></span>

```
get-help get-childitem -parameter *
```

<span data-ttu-id="de4c5-124">Pour afficher uniquement les exemples d’une rubrique d’aide, utilisez le paramètre *Example* de l’applet de commande Get-Help.</span><span class="sxs-lookup"><span data-stu-id="de4c5-124">To display only the examples in a Help topic, use the *Example* parameter of the Get-Help.</span></span> <span data-ttu-id="de4c5-125">Par exemple, pour afficher uniquement les exemples de la rubrique d’aide sur l’applet de commande Get-ChildItem, tapez :</span><span class="sxs-lookup"><span data-stu-id="de4c5-125">For example, to display only the examples in the Help topic for the Get-ChildItem cmdlet, type:</span></span>

```
get-help get-childitem -examples
```

<span data-ttu-id="de4c5-126">Pour plus d’informations sur la manière de rédiger des rubriques d’aide sur les applets de commande que vous écrivez, consultez [How to Write Cmdlet Help](https://go.microsoft.com/fwlink/?LinkID=123415) dans MSDN Library.</span><span class="sxs-lookup"><span data-stu-id="de4c5-126">For information about how to write Help topics for the cmdlets that you write, see [How to Write Cmdlet Help](https://go.microsoft.com/fwlink/?LinkID=123415) in the MSDN library.</span></span>

## <a name="getting-conceptual-help"></a><span data-ttu-id="de4c5-127">Obtention d’aide conceptuelle</span><span class="sxs-lookup"><span data-stu-id="de4c5-127">Getting Conceptual Help</span></span>
<span data-ttu-id="de4c5-128">L’applet de commande Get-Help affiche également des informations sur des rubriques conceptuelles de Windows PowerShell, dont des rubriques sur le langage Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="de4c5-128">The Get-Help cmdlet also displays information about conceptual topics in Windows PowerShell, including topics about the Windows PowerShell language.</span></span> <span data-ttu-id="de4c5-129">Les rubriques d’aide conceptuelle commencent par le préfixe « about_ », par exemple, « about_line_editing ».</span><span class="sxs-lookup"><span data-stu-id="de4c5-129">Conceptual Help topics begin with the "about_" prefix, such as about_line_editing.</span></span> <span data-ttu-id="de4c5-130">(Le nom de la rubrique conceptuelle doit être saisi en anglais, même dans les versions non anglaises de Windows PowerShell.)</span><span class="sxs-lookup"><span data-stu-id="de4c5-130">(The name of the conceptual topic must be entered in English even on non-English versions of Windows PowerShell.)</span></span>

<span data-ttu-id="de4c5-131">Pour afficher la liste des rubriques conceptuelles, tapez :</span><span class="sxs-lookup"><span data-stu-id="de4c5-131">To display a list of conceptual topics, type:</span></span>

```
get-help about_*
```

<span data-ttu-id="de4c5-132">Pour afficher une rubrique d’aide spécifique, tapez son nom, par exemple :</span><span class="sxs-lookup"><span data-stu-id="de4c5-132">To display a particular Help topic, type the topic name, for example:</span></span>

```
get-help about_command_syntax
```

<span data-ttu-id="de4c5-133">Les paramètres de l’applet de commande Get-Help, tels que *Detailed*, *Parameter* et *Examples*, n’ont aucune incidence sur l’affichage des rubriques d’aide conceptuelle.</span><span class="sxs-lookup"><span data-stu-id="de4c5-133">The parameters of Get-Help, such as *Detailed*, *Parameter*, and *Examples*, have no effect on the display of conceptual Help topics.</span></span>

## <a name="getting-help-about-providers"></a><span data-ttu-id="de4c5-134">Obtention d’aide sur les fournisseurs</span><span class="sxs-lookup"><span data-stu-id="de4c5-134">Getting Help About Providers</span></span>
<span data-ttu-id="de4c5-135">L’applet de commande Get-Help affiche des informations sur les fournisseurs Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="de4c5-135">The Get-Help cmdlet displays information about Windows PowerShell providers.</span></span> <span data-ttu-id="de4c5-136">Pour obtenir de l’aide sur un fournisseur, tapez « Get-Help », suivi du nom du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="de4c5-136">To get Help for a provider, type "Get-Help" followed by the provider name.</span></span> <span data-ttu-id="de4c5-137">Par exemple, pour obtenir de l’aide sur le fournisseur de Registre, tapez :</span><span class="sxs-lookup"><span data-stu-id="de4c5-137">For example, to get Help for the Registry provider, type:</span></span>

```
get-help registry
```

<span data-ttu-id="de4c5-138">Pour obtenir la liste de toutes les rubriques d’aide sur le fournisseur dans votre session, tapez :</span><span class="sxs-lookup"><span data-stu-id="de4c5-138">To get a list of all the provider Help topics in your session, type</span></span>

```
get-help -category provider
```

<span data-ttu-id="de4c5-139">Les paramètres de l’applet de commande Get-Help, tels que *Detailed*, *Parameter* et *Examples*, n’ont aucune incidence sur l’affichage des rubriques d’aide sur le fournisseur.</span><span class="sxs-lookup"><span data-stu-id="de4c5-139">The parameters of Get-Help, such as *Detailed*, *Parameter*, and *Examples*, have no effect on the display of provider Help topics.</span></span>

## <a name="getting-help-about-scripts-and-functions"></a><span data-ttu-id="de4c5-140">Obtention d’aide sur les fonctions et les scripts</span><span class="sxs-lookup"><span data-stu-id="de4c5-140">Getting Help About Scripts and Functions</span></span>
<span data-ttu-id="de4c5-141">De nombreux scripts et fonctions dans Windows PowerShell ont des rubriques d’aide associées.</span><span class="sxs-lookup"><span data-stu-id="de4c5-141">Many scripts and functions in Windows PowerShell have Help topics.</span></span> <span data-ttu-id="de4c5-142">Utilisez l’applet de commande Get-Help pour afficher les rubriques d’aide sur les scripts et fonctions.</span><span class="sxs-lookup"><span data-stu-id="de4c5-142">Use the Get-Help cmdlet to display the Help topics for scripts and functions.</span></span>

<span data-ttu-id="de4c5-143">Pour afficher l’aide sur une fonction, tapez « get-help », suivi du nom de la fonction.</span><span class="sxs-lookup"><span data-stu-id="de4c5-143">To display the Help for a function, type "get-help" followed by the function name.</span></span> <span data-ttu-id="de4c5-144">Par exemple, pour obtenir de l’aide sur la fonction Disable-PSRemoting, tapez :</span><span class="sxs-lookup"><span data-stu-id="de4c5-144">For example, to get Help for the Disable-PSRemoting function, type:</span></span>

```
get-help disable-psremoting
```

<span data-ttu-id="de4c5-145">Pour afficher l’aide sur un script, tapez le chemin d’accès complet au fichier de script.</span><span class="sxs-lookup"><span data-stu-id="de4c5-145">To display the Help for a script, type the fully qualified path to the script file.</span></span> <span data-ttu-id="de4c5-146">Si le script figure dans un chemin d’accès répertorié dans la variable d’environnement Path, vous pouvez omettre le chemin d’accès de la commande.</span><span class="sxs-lookup"><span data-stu-id="de4c5-146">If the script is in a path that is listed in the Path environment variable, you can omit the path from the command.</span></span>

<span data-ttu-id="de4c5-147">Par exemple, si vous avez un script nommé « TestScript.ps1 » dans le répertoire C:\\PS-Test, pour afficher la rubrique d’aide sur le script, tapez :</span><span class="sxs-lookup"><span data-stu-id="de4c5-147">For example, if you have a script called "TestScript.ps1" in your C:\\PS-Test directory, to display the Help topic for the script, type:</span></span>

```
get-help c:\ps-test\TestScript.ps1
```

<span data-ttu-id="de4c5-148">Les paramètres conçus pour afficher de l’aide sur l’applet de commande, tels que *Detailed*, *Full*, *Examples*et *Parameter*, opèrent également pour l’aide sur le script et l’aide sur la fonction.</span><span class="sxs-lookup"><span data-stu-id="de4c5-148">The parameters that were designed for displaying cmdlet Help, such as *Detailed*, *Full*, *Examples*, and *Parameter*, work for script Help and function Help, too.</span></span> <span data-ttu-id="de4c5-149">Toutefois, lorsque vous affichez toute l’aide en tapant « get-help \* », l’aide sur les fonctions et les scripts ne s’affiche pas.</span><span class="sxs-lookup"><span data-stu-id="de4c5-149">However, when you display all Help, by typing "get-help \*", Help for functions and scripts does not appear.</span></span>

<span data-ttu-id="de4c5-150">Pour plus d’informations sur l’écriture de rubriques d’aide pour vos fonctions et les scripts, voir [about_Functions [m2]](https://technet.microsoft.com/library/61d40692-5300-4de9-a9b5-bae31815e105), [about_Scripts](https://technet.microsoft.com/library/7dc08334-dcfe-450b-b949-0554855623af) et [about_Comment_Based_Help](https://technet.microsoft.com/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf).</span><span class="sxs-lookup"><span data-stu-id="de4c5-150">For information about writing Help topics for your functions and scripts, see [about_Functions [m2]](https://technet.microsoft.com/library/61d40692-5300-4de9-a9b5-bae31815e105), [about_Scripts](https://technet.microsoft.com/library/7dc08334-dcfe-450b-b949-0554855623af), and [about_Comment_Based_Help](https://technet.microsoft.com/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf).</span></span>

## <a name="getting-help-online"></a><span data-ttu-id="de4c5-151">Obtention d’aide en ligne</span><span class="sxs-lookup"><span data-stu-id="de4c5-151">Getting Help Online</span></span>
<span data-ttu-id="de4c5-152">Si vous êtes connecté à Internet, l’un des meilleurs moyens d’obtenir de l’aide consiste à afficher les rubriques d’aide en ligne.</span><span class="sxs-lookup"><span data-stu-id="de4c5-152">If you are connected to the Internet, one of the best ways to get Help is to view the Help topics online.</span></span> <span data-ttu-id="de4c5-153">Étant donné que les rubriques en ligne sont faciles à mettre à jour, il est probable qu’elles fournissent le contenu à jour.</span><span class="sxs-lookup"><span data-stu-id="de4c5-153">Because online topics are easy to update, they are likely to provide the most current content.</span></span>

<span data-ttu-id="de4c5-154">Pour obtenir l’aide en ligne, essayez le paramètre *Online* de l’applet de commande Get-Help.</span><span class="sxs-lookup"><span data-stu-id="de4c5-154">To get Help online, try the *Online* parameter of the Get-Help cmdlet.</span></span> <span data-ttu-id="de4c5-155">La paramètre *Online* de l’applet de commande Get-Help opère uniquement pour l’applet de commande Help, la fonction Help et le script Help.</span><span class="sxs-lookup"><span data-stu-id="de4c5-155">The *Online* parameter of the Get-Help cmdlet works only for cmdlet Help, function Help, and script Help.</span></span> <span data-ttu-id="de4c5-156">Vous ne pouvez pas utiliser le paramètre *Online* avec des rubriques conceptuelles (About) ou des rubriques d’aide sur le fournisseur.</span><span class="sxs-lookup"><span data-stu-id="de4c5-156">You cannot use the *Online* parameter with conceptual (About) topics or provider Help topics.</span></span> <span data-ttu-id="de4c5-157">En outre, étant donné que cette fonctionnalité est facultative, elle n’opère pas pour chaque applet de commande, fonction ou une rubrique d’aide sur un script.</span><span class="sxs-lookup"><span data-stu-id="de4c5-157">Also, because this feature is optional, it does not work for every cmdlet, function, or script Help topic.</span></span>

<span data-ttu-id="de4c5-158">Toutefois, toutes les rubriques d’aide fournies avec Windows PowerShell, y compris l’aide sur le fournisseur et les rubriques d’aide conceptuelle (About) sont disponibles en ligne dans la section [Windows PowerShell](http://go.microsoft.com/fwlink/?LinkID=107116) de la Bibliothèque Microsoft TechNet.</span><span class="sxs-lookup"><span data-stu-id="de4c5-158">However, all the Help topics that come with Windows PowerShell, including provider Help and conceptual (About) Help topics, are available online in the [Windows PowerShell](http://go.microsoft.com/fwlink/?LinkID=107116) section of the Microsoft TechNet Library.</span></span>

<span data-ttu-id="de4c5-159">Pour utiliser le paramètre *Online* de l’applet de commande Get-Help, utilisez le format de commande suivant.</span><span class="sxs-lookup"><span data-stu-id="de4c5-159">To use the *Online* parameter of the Get-Help cmdlet, use the following command format.</span></span>

```
get-help <command-name> -online
```

<span data-ttu-id="de4c5-160">Par exemple, pour obtenir la version en ligne de la rubrique d’aide sur l’applet de commande Get-ChildItem, tapez :</span><span class="sxs-lookup"><span data-stu-id="de4c5-160">For example, to get the online version of the Help topic about the Get-ChildItem cmdlet, type:</span></span>

```
get-help get-childitem -online
```

<span data-ttu-id="de4c5-161">Si une version en ligne de la rubrique d’aide est disponible, elle s’ouvre dans votre navigateur par défaut.</span><span class="sxs-lookup"><span data-stu-id="de4c5-161">If an online version of the Help topic is available, it will open in your default browser.</span></span>

<span data-ttu-id="de4c5-162">Si l’aide en ligne est prise en charge pour une rubrique d’aide, vous pouvez également afficher l’adresse Internet (URL) de la rubrique d’aide.</span><span class="sxs-lookup"><span data-stu-id="de4c5-162">If online Help is supported for a Help topic, you can also view the Internet address (URL) of the Help topic.</span></span> <span data-ttu-id="de4c5-163">L’adresse Internet apparaît dans la section Liens connexes d’une rubrique d’aide.</span><span class="sxs-lookup"><span data-stu-id="de4c5-163">The Internet address appears in the Related Links section of a Help topic.</span></span>

<span data-ttu-id="de4c5-164">Par exemple, pour afficher l’URL de la version en ligne de l’applet de commande Add-Computer, tapez :</span><span class="sxs-lookup"><span data-stu-id="de4c5-164">For example, to see the URL for the online version of the Add-Computer cmdlet, type:</span></span>

```
get-help add-computer
```

<span data-ttu-id="de4c5-165">La première ligne de la section Liens connexes de la rubrique est présentée ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="de4c5-165">The first line in the Related Links section of the topic is shown below.</span></span>

```
Online version: http://go.microsoft.com/fwlink/?LinkID=135194
```

<span data-ttu-id="de4c5-166">Pour plus d’informations sur la manière de fournir un support en ligne pour vos rubriques d’aide, consultez [about_Comment_Based_Help](https://technet.microsoft.com/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf) et [How to Write Cmdlet Help](https://go.microsoft.com/fwlink/?LinkID=123415) dans MSDN Library.</span><span class="sxs-lookup"><span data-stu-id="de4c5-166">For information about how to provide online support for your Help topics, see [about_Comment_Based_Help](https://technet.microsoft.com/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf), and see [How to Write Cmdlet Help](https://go.microsoft.com/fwlink/?LinkID=123415) in the MSDN library.</span></span>

## <a name="see-also"></a><span data-ttu-id="de4c5-167">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="de4c5-167">See Also</span></span>
- <span data-ttu-id="de4c5-168">[about_Functions [m2]](https://technet.microsoft.com/library/61d40692-5300-4de9-a9b5-bae31815e105)</span><span class="sxs-lookup"><span data-stu-id="de4c5-168">[about_Functions [m2]](https://technet.microsoft.com/library/61d40692-5300-4de9-a9b5-bae31815e105)</span></span>
- [<span data-ttu-id="de4c5-169">about_Scripts</span><span class="sxs-lookup"><span data-stu-id="de4c5-169">about_Scripts</span></span>](https://technet.microsoft.com/library/7dc08334-dcfe-450b-b949-0554855623af)
- [<span data-ttu-id="de4c5-170">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="de4c5-170">about_Comment_Based_Help</span></span>](https://technet.microsoft.com/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf)
- <span data-ttu-id="de4c5-171">[Get-Help [m2]](https://technet.microsoft.com/library/2d7fe1b4-0025-4580-a911-d81922dd6cd2)</span><span class="sxs-lookup"><span data-stu-id="de4c5-171">[Get-Help [m2]](https://technet.microsoft.com/library/2d7fe1b4-0025-4580-a911-d81922dd6cd2)</span></span>