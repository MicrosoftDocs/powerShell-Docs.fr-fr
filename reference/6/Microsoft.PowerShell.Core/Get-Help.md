---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 08/23/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-help?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Help
ms.openlocfilehash: 691709fe3f5e4908ab3203df73f636981adf560c
ms.sourcegitcommit: b7ff031a12afd04910aeb98345ebee92f5845b0c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "93205798"
---
# <span data-ttu-id="aec92-103">Get-Help</span><span class="sxs-lookup"><span data-stu-id="aec92-103">Get-Help</span></span>

## <span data-ttu-id="aec92-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="aec92-104">SYNOPSIS</span></span>
<span data-ttu-id="aec92-105">Affiche des informations sur les commandes et les concepts PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aec92-105">Displays information about PowerShell commands and concepts.</span></span>

## <span data-ttu-id="aec92-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="aec92-106">SYNTAX</span></span>

### <span data-ttu-id="aec92-107">AllUsersView (par défaut)</span><span class="sxs-lookup"><span data-stu-id="aec92-107">AllUsersView (Default)</span></span>

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Full] [-Component <String[]>]
 [-Functionality <String[]>] [-Role <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="aec92-108">DetailedView</span><span class="sxs-lookup"><span data-stu-id="aec92-108">DetailedView</span></span>

```
Get-Help [[-Name] <String>] -Detailed [-Path <String>] [-Category <String[]>]
 [-Component <String[]>] [-Functionality <String[]>] [-Role <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="aec92-109">Exemples</span><span class="sxs-lookup"><span data-stu-id="aec92-109">Examples</span></span>

```
Get-Help [[-Name] <String>] -Examples [-Path <String>] [-Category <String[]>]
 [-Component <String[]>] [-Functionality <String[]>] [-Role <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="aec92-110">Paramètres</span><span class="sxs-lookup"><span data-stu-id="aec92-110">Parameters</span></span>

```
Get-Help [[-Name] <String>] -Parameter <String[]> [-Path <String>] [-Category <String[]>]
 [-Component <String[]>] [-Functionality <String[]>] [-Role <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="aec92-111">En ligne</span><span class="sxs-lookup"><span data-stu-id="aec92-111">Online</span></span>

```
Get-Help [[-Name] <String>] -Online [-Path <String>] [-Category <String[]>] [-Component <String[]>]
 [-Functionality <String[]>] [-Role <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="aec92-112">Description</span><span class="sxs-lookup"><span data-stu-id="aec92-112">DESCRIPTION</span></span>

<span data-ttu-id="aec92-113">L' `Get-Help` applet de commande affiche des informations sur les concepts et les commandes PowerShell, y compris les applets de commande, les fonctions, les commandes Common Information Model (CIM), les flux de travail, les fournisseurs, les alias et les scripts.</span><span class="sxs-lookup"><span data-stu-id="aec92-113">The `Get-Help` cmdlet displays information about PowerShell concepts and commands, including cmdlets, functions, Common Information Model (CIM) commands, workflows, providers, aliases, and scripts.</span></span>

<span data-ttu-id="aec92-114">Pour obtenir de l’aide pour une applet de commande PowerShell, tapez `Get-Help` suivi du nom de l’applet de commande, par exemple : `Get-Help Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="aec92-114">To get help for a PowerShell cmdlet, type `Get-Help` followed by the cmdlet name, such as: `Get-Help Get-Process`.</span></span>

<span data-ttu-id="aec92-115">Les articles d’aide conceptuelle dans PowerShell commencent par **about_** , comme **about_Comparison_Operators** .</span><span class="sxs-lookup"><span data-stu-id="aec92-115">Conceptual help articles in PowerShell begin with **about_** , such as **about_Comparison_Operators** .</span></span> <span data-ttu-id="aec92-116">Pour afficher tous les articles **about_** , tapez `Get-Help about_*` .</span><span class="sxs-lookup"><span data-stu-id="aec92-116">To see all **about_** articles, type `Get-Help about_*`.</span></span> <span data-ttu-id="aec92-117">Pour afficher un article particulier, tapez `Get-Help about_<article-name>` , par exemple `Get-Help about_Comparison_Operators` .</span><span class="sxs-lookup"><span data-stu-id="aec92-117">To see a particular article, type `Get-Help about_<article-name>`, such as `Get-Help about_Comparison_Operators`.</span></span>

<span data-ttu-id="aec92-118">Pour obtenir de l’aide pour un fournisseur PowerShell, tapez `Get-Help` suivi du nom du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="aec92-118">To get help for a PowerShell provider, type `Get-Help` followed by the provider name.</span></span> <span data-ttu-id="aec92-119">Par exemple, pour obtenir de l’aide pour le fournisseur de certificats, tapez `Get-Help Certificate` .</span><span class="sxs-lookup"><span data-stu-id="aec92-119">For example, to get help for the Certificate provider, type `Get-Help Certificate`.</span></span>

<span data-ttu-id="aec92-120">Vous pouvez également taper `help` ou `man` , qui affiche un écran de texte à la fois.</span><span class="sxs-lookup"><span data-stu-id="aec92-120">You can also type `help` or `man`, which displays one screen of text at a time.</span></span> <span data-ttu-id="aec92-121">Ou, `<cmdlet-name> -?` , qui est identique à `Get-Help` , mais fonctionne uniquement pour les applets de commande.</span><span class="sxs-lookup"><span data-stu-id="aec92-121">Or, `<cmdlet-name> -?`, that is identical to `Get-Help`, but only works for cmdlets.</span></span>

<span data-ttu-id="aec92-122">`Get-Help` Obtient le contenu de l’aide qu’il affiche à partir des fichiers d’aide sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="aec92-122">`Get-Help` gets the help content that it displays from help files on your computer.</span></span> <span data-ttu-id="aec92-123">Sans les fichiers d’aide, `Get-Help` affiche uniquement les informations de base sur les applets de commande.</span><span class="sxs-lookup"><span data-stu-id="aec92-123">Without the help files, `Get-Help` displays only basic information about cmdlets.</span></span> <span data-ttu-id="aec92-124">Certains modules PowerShell incluent des fichiers d’aide.</span><span class="sxs-lookup"><span data-stu-id="aec92-124">Some PowerShell modules include help files.</span></span> <span data-ttu-id="aec92-125">À compter de PowerShell 3,0, les modules fournis avec le système d’exploitation Windows n’incluent pas les fichiers d’aide.</span><span class="sxs-lookup"><span data-stu-id="aec92-125">Beginning in PowerShell 3.0, the modules that come with the Windows operating system don't include help files.</span></span> <span data-ttu-id="aec92-126">Pour télécharger ou mettre à jour les fichiers d’aide d’un module dans PowerShell 3,0, utilisez l’applet de commande `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="aec92-126">To download or update the help files for a module in PowerShell 3.0, use the `Update-Help` cmdlet.</span></span>

<span data-ttu-id="aec92-127">Vous pouvez également consulter les documents d’aide PowerShell en ligne dans le Microsoft Docs. Pour obtenir la version en ligne d’un fichier d’aide, utilisez le paramètre **Online** , tel que : `Get-Help Get-Process -Online` .</span><span class="sxs-lookup"><span data-stu-id="aec92-127">You can also view the PowerShell help documents online in the Microsoft Docs. To get the online version of a help file, use the **Online** parameter, such as: `Get-Help Get-Process -Online`.</span></span> <span data-ttu-id="aec92-128">Pour lire toute la documentation PowerShell, consultez la [documentation Microsoft docs PowerShell](/powershell).</span><span class="sxs-lookup"><span data-stu-id="aec92-128">To read all the PowerShell documentation, see the Microsoft Docs [PowerShell Documentation](/powershell).</span></span>

<span data-ttu-id="aec92-129">Si vous tapez `Get-Help` suivi du nom exact d’un article d’aide, ou d’un mot unique à un article d’aide, `Get-Help` affiche le contenu de l’article.</span><span class="sxs-lookup"><span data-stu-id="aec92-129">If you type `Get-Help` followed by the exact name of a help article, or by a word unique to a help article, `Get-Help` displays the article's content.</span></span> <span data-ttu-id="aec92-130">Si vous spécifiez le nom exact d’un alias de commande, `Get-Help` affiche l’aide de la commande d’origine.</span><span class="sxs-lookup"><span data-stu-id="aec92-130">If you specify the exact name of a command alias, `Get-Help` displays the help for the original command.</span></span> <span data-ttu-id="aec92-131">Si vous entrez un mot ou un modèle de mot qui apparaît dans plusieurs titres d’articles d’aide, `Get-Help` affiche une liste des titres correspondants.</span><span class="sxs-lookup"><span data-stu-id="aec92-131">If you enter a word or word pattern that appears in several help article titles, `Get-Help` displays a list of the matching titles.</span></span> <span data-ttu-id="aec92-132">Si vous entrez du texte qui n’apparaît pas dans les titres des articles d’aide, `Get-Help` affiche une liste d’articles qui contiennent ce texte dans leur contenu.</span><span class="sxs-lookup"><span data-stu-id="aec92-132">If you enter any text that doesn't appear in any help article titles, `Get-Help` displays a list of articles that include that text in their contents.</span></span>

<span data-ttu-id="aec92-133">`Get-Help` peut obtenir des articles d’aide pour toutes les langues et paramètres régionaux pris en charge.</span><span class="sxs-lookup"><span data-stu-id="aec92-133">`Get-Help` can get help articles for all supported languages and locales.</span></span> <span data-ttu-id="aec92-134">`Get-Help` recherche d’abord les fichiers d’aide dans les paramètres régionaux définis pour Windows, puis dans les paramètres régionaux parents, par exemple **PT** pour **pt-br** , puis dans des paramètres régionaux de secours.</span><span class="sxs-lookup"><span data-stu-id="aec92-134">`Get-Help` first looks for help files in the locale set for Windows, then in the parent locale, such as **pt** for **pt-BR** , and then in a fallback locale.</span></span> <span data-ttu-id="aec92-135">À compter de PowerShell 3,0, si `Get-Help` ne trouve pas l’aide dans les paramètres régionaux de secours, il recherche des articles d’aide en anglais, en **-US** , avant de renvoyer un message d’erreur ou d’afficher l’aide générée automatiquement.</span><span class="sxs-lookup"><span data-stu-id="aec92-135">Beginning in PowerShell 3.0, if `Get-Help` doesn't find help in the fallback locale, it looks for help articles in English, **en-US** , before it returns an error message or displaying autogenerated help.</span></span>

<span data-ttu-id="aec92-136">Pour plus d’informations sur les symboles qui `Get-Help` s’affichent dans le diagramme de syntaxe de commande, consultez [about_Command_Syntax](./About/about_Command_Syntax.md).</span><span class="sxs-lookup"><span data-stu-id="aec92-136">For information about the symbols that `Get-Help` displays in the command syntax diagram, see [about_Command_Syntax](./About/about_Command_Syntax.md).</span></span>
<span data-ttu-id="aec92-137">Pour plus d’informations sur les attributs de paramètres, tels que **Required** et **Position** , consultez [about_Parameters](./About/about_Parameters.md).</span><span class="sxs-lookup"><span data-stu-id="aec92-137">For information about parameter attributes, such as **Required** and **Position** , see [about_Parameters](./About/about_Parameters.md).</span></span>

>[!NOTE]
> <span data-ttu-id="aec92-138">Dans PowerShell 3,0 et PowerShell 4,0, `Get-Help` les articles **About** ne peuvent pas être détectés dans les modules, sauf si le module est importé dans la session active.</span><span class="sxs-lookup"><span data-stu-id="aec92-138">In PowerShell 3.0 and PowerShell 4.0, `Get-Help` can't find **About** articles in modules unless the module is imported into the current session.</span></span> <span data-ttu-id="aec92-139">Il s'agit d'un problème connu.</span><span class="sxs-lookup"><span data-stu-id="aec92-139">This is a known issue.</span></span> <span data-ttu-id="aec92-140">Pour obtenir des **informations sur** les articles d’un module, importez le module à l’aide de l’applet de commande `Import-Module` ou en exécutant une applet de commande incluse dans le module.</span><span class="sxs-lookup"><span data-stu-id="aec92-140">To get **About** articles in a module, import the module, either by using the `Import-Module` cmdlet or by running a cmdlet that's included in the module.</span></span>

## <span data-ttu-id="aec92-141">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="aec92-141">EXAMPLES</span></span>

### <span data-ttu-id="aec92-142">Exemple 1 : afficher les informations d’aide de base sur une applet de commande</span><span class="sxs-lookup"><span data-stu-id="aec92-142">Example 1: Display basic help information about a cmdlet</span></span>

<span data-ttu-id="aec92-143">Ces exemples affichent des informations d’aide de base sur l’applet de commande `Format-Table` .</span><span class="sxs-lookup"><span data-stu-id="aec92-143">These examples display basic help information about the `Format-Table` cmdlet.</span></span>

```powershell
Get-Help Format-Table
Get-Help -Name Format-Table
Format-Table -?
```

<span data-ttu-id="aec92-144">`Get-Help <cmdlet-name>` est la syntaxe la plus simple et la syntaxe par défaut de l’applet de commande `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="aec92-144">`Get-Help <cmdlet-name>` is the simplest and default syntax of `Get-Help` cmdlet.</span></span> <span data-ttu-id="aec92-145">Vous pouvez omettre le paramètre **Name** .</span><span class="sxs-lookup"><span data-stu-id="aec92-145">You can omit the **Name** parameter.</span></span>

<span data-ttu-id="aec92-146">La syntaxe `<cmdlet-name> -?` fonctionne uniquement pour les applets de commande.</span><span class="sxs-lookup"><span data-stu-id="aec92-146">The syntax `<cmdlet-name> -?` works only for cmdlets.</span></span>

### <span data-ttu-id="aec92-147">Exemple 2 : afficher les informations de base une page à la fois</span><span class="sxs-lookup"><span data-stu-id="aec92-147">Example 2: Display basic information one page at a time</span></span>

<span data-ttu-id="aec92-148">Ces exemples affichent des informations d’aide de base sur l’applet de commande `Format-Table` , une page à la fois.</span><span class="sxs-lookup"><span data-stu-id="aec92-148">These examples display basic help information about the `Format-Table` cmdlet one page at a time.</span></span>

```powershell
help Format-Table
man Format-Table
Get-Help Format-Table | Out-Host -Paging
```

<span data-ttu-id="aec92-149">`help` est une fonction qui exécute `Get-Help` l’applet de commande en interne et affiche le résultat une page à la fois.</span><span class="sxs-lookup"><span data-stu-id="aec92-149">`help` is a function that runs `Get-Help` cmdlet internally and displays the result one page at a time.</span></span>

<span data-ttu-id="aec92-150">`man` alias de la `help` fonction.</span><span class="sxs-lookup"><span data-stu-id="aec92-150">`man` is an alias for the `help` function.</span></span>

<span data-ttu-id="aec92-151">`Get-Help Format-Table` envoie l’objet dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="aec92-151">`Get-Help Format-Table` sends the object down the pipeline.</span></span> <span data-ttu-id="aec92-152">`Out-Host -Paging` reçoit la sortie du pipeline et l’affiche une page à la fois.</span><span class="sxs-lookup"><span data-stu-id="aec92-152">`Out-Host -Paging` receives the output from the pipeline and displays it one page at a time.</span></span> <span data-ttu-id="aec92-153">Pour plus d’informations, consultez [Out-Host](Out-Host.md).</span><span class="sxs-lookup"><span data-stu-id="aec92-153">For more information, see [Out-Host](Out-Host.md).</span></span>

### <span data-ttu-id="aec92-154">Exemple 3 : afficher plus d’informations pour une applet de commande</span><span class="sxs-lookup"><span data-stu-id="aec92-154">Example 3: Display more information for a cmdlet</span></span>

<span data-ttu-id="aec92-155">Ces exemples affichent des informations d’aide plus détaillées sur l’applet de commande `Format-Table` .</span><span class="sxs-lookup"><span data-stu-id="aec92-155">These examples display more detailed help information about the `Format-Table` cmdlet.</span></span>

```powershell
Get-Help Format-Table -Detailed
Get-Help Format-Table -Full
```

<span data-ttu-id="aec92-156">Le paramètre **detailed** affiche la vue détaillée de l’article d’aide qui comprend des descriptions de paramètres et des exemples.</span><span class="sxs-lookup"><span data-stu-id="aec92-156">The **Detailed** parameter displays the help article's detailed view that includes parameter descriptions and examples.</span></span>

<span data-ttu-id="aec92-157">Le paramètre **Full** affiche la vue complète de l’article d’aide qui comprend des descriptions de paramètres, des exemples, des types d’objet d’entrée et de sortie, ainsi que des remarques supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="aec92-157">The **Full** parameter displays the help article's full view that includes parameter descriptions, examples, input and output object types, and additional notes.</span></span>

<span data-ttu-id="aec92-158">Les paramètres **détaillés** et **complets** sont effectifs uniquement pour les commandes qui ont des fichiers d’aide installés sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="aec92-158">The **Detailed** and **Full** parameters are effective only for the commands that have help files installed on the computer.</span></span> <span data-ttu-id="aec92-159">Les paramètres ne sont pas efficaces pour les articles d’aide conceptuel ( **about_** ).</span><span class="sxs-lookup"><span data-stu-id="aec92-159">The parameters aren't effective for the conceptual ( **about_** ) help articles.</span></span>

### <span data-ttu-id="aec92-160">Exemple 4 : afficher les parties sélectionnées d’une applet de commande à l’aide de paramètres</span><span class="sxs-lookup"><span data-stu-id="aec92-160">Example 4: Display selected parts of a cmdlet by using parameters</span></span>

<span data-ttu-id="aec92-161">Ces exemples affichent les parties sélectionnées de l’aide de l’applet de commande `Format-Table` .</span><span class="sxs-lookup"><span data-stu-id="aec92-161">These examples display selected portions of the `Format-Table` cmdlet help.</span></span>

```powershell
Get-Help Format-Table -Examples
Get-Help Format-Table -Parameter *
Get-Help Format-Table -Parameter GroupBy
```

<span data-ttu-id="aec92-162">Le paramètre **exemples** affiche le **nom** et les sections **Synopsis** du fichier d’aide, ainsi que tous les exemples.</span><span class="sxs-lookup"><span data-stu-id="aec92-162">The **Examples** parameter displays the help file's **NAME** and **SYNOPSIS** sections, and all the Examples.</span></span> <span data-ttu-id="aec92-163">Vous ne pouvez pas spécifier un exemple de nombre, car le paramètre d' **exemples** est un paramètre de commutateur.</span><span class="sxs-lookup"><span data-stu-id="aec92-163">You can't specify an Example number because the **Examples** parameter is a switch parameter.</span></span>

<span data-ttu-id="aec92-164">Le **paramètre parameter affiche** uniquement les descriptions des paramètres spécifiés.</span><span class="sxs-lookup"><span data-stu-id="aec92-164">The **Parameter** parameter displays only the descriptions of the specified parameters.</span></span> <span data-ttu-id="aec92-165">Si vous spécifiez uniquement le `*` caractère générique astérisque (), il affiche les descriptions de tous les paramètres.</span><span class="sxs-lookup"><span data-stu-id="aec92-165">If you specify only the asterisk (`*`) wildcard character, it displays the descriptions of all parameters.</span></span>
<span data-ttu-id="aec92-166">Quand le **paramètre** spécifie un nom de paramètre tel que **GroupBy** , les informations sur ce paramètre sont affichées.</span><span class="sxs-lookup"><span data-stu-id="aec92-166">When **Parameter** specifies a parameter name such as **GroupBy** , information about that parameter is shown.</span></span>

<span data-ttu-id="aec92-167">Ces paramètres ne sont pas efficaces pour les articles d’aide conceptuel ( **about_** ).</span><span class="sxs-lookup"><span data-stu-id="aec92-167">These parameters aren't effective for the conceptual ( **about_** ) help articles.</span></span>

### <span data-ttu-id="aec92-168">Exemple 5 : afficher la version en ligne de l’aide</span><span class="sxs-lookup"><span data-stu-id="aec92-168">Example 5: Display online version of help</span></span>

<span data-ttu-id="aec92-169">Cet exemple affiche la version en ligne de l’article d’aide pour l’applet de commande `Format-Table` dans votre navigateur Web par défaut.</span><span class="sxs-lookup"><span data-stu-id="aec92-169">This example displays the online version of the help article for the `Format-Table` cmdlet in your default web browser.</span></span>

```powershell
Get-Help Format-Table -Online
```

### <span data-ttu-id="aec92-170">Exemple 6 : afficher de l’aide sur le système d’aide</span><span class="sxs-lookup"><span data-stu-id="aec92-170">Example 6: Display help about the help system</span></span>

<span data-ttu-id="aec92-171">L' `Get-Help` applet de commande sans paramètres affiche des informations sur le système d’aide PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aec92-171">The `Get-Help` cmdlet without parameters displays information about the PowerShell help system.</span></span>

```powershell
Get-Help
```

### <span data-ttu-id="aec92-172">Exemple 7 : afficher les articles d’aide disponibles</span><span class="sxs-lookup"><span data-stu-id="aec92-172">Example 7: Display available help articles</span></span>

<span data-ttu-id="aec92-173">Cet exemple affiche une liste de tous les articles d’aide disponibles sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="aec92-173">This example displays a list of all help articles available on your computer.</span></span>

```powershell
Get-Help *
```

### <span data-ttu-id="aec92-174">Exemple 8 : afficher une liste d’articles conceptuels</span><span class="sxs-lookup"><span data-stu-id="aec92-174">Example 8: Display a list of conceptual articles</span></span>

<span data-ttu-id="aec92-175">Cet exemple affiche une liste des articles conceptuels inclus dans l’aide de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aec92-175">This example displays a list of the conceptual articles included in PowerShell help.</span></span> <span data-ttu-id="aec92-176">Tous ces articles commencent par les caractères **about_** .</span><span class="sxs-lookup"><span data-stu-id="aec92-176">All these articles begin with the characters **about_** .</span></span> <span data-ttu-id="aec92-177">Pour afficher un fichier d’aide particulier, tapez `Get-Help \<about_article-name\>` , par exemple, `Get-Help about_Signing` .</span><span class="sxs-lookup"><span data-stu-id="aec92-177">To display a particular help file, type `Get-Help \<about_article-name\>`, for example, `Get-Help about_Signing`.</span></span>

<span data-ttu-id="aec92-178">Seuls les articles conceptuels sur lesquels sont installés des fichiers d’aide sur votre ordinateur sont affichés.</span><span class="sxs-lookup"><span data-stu-id="aec92-178">Only the conceptual articles that have help files installed on your computer are displayed.</span></span> <span data-ttu-id="aec92-179">Pour plus d’informations sur le téléchargement et l’installation des fichiers d’aide dans PowerShell 3,0, consultez [Update-Help](Update-Help.md).</span><span class="sxs-lookup"><span data-stu-id="aec92-179">For information about downloading and installing help files in PowerShell 3.0, see [Update-Help](Update-Help.md).</span></span>

```powershell
Get-Help about_*
```

### <span data-ttu-id="aec92-180">Exemple 9 : Rechercher un mot dans l’aide sur les applets de commande</span><span class="sxs-lookup"><span data-stu-id="aec92-180">Example 9: Search for a word in cmdlet help</span></span>

<span data-ttu-id="aec92-181">Cet exemple montre comment rechercher un mot dans l’article d’aide d’une applet de commande.</span><span class="sxs-lookup"><span data-stu-id="aec92-181">This example shows how to search for a word in a cmdlet help article.</span></span>

```powershell
Get-Help Add-Member -Full | Out-String -Stream | Select-String -Pattern Clixml
```

```Output
the Export-Clixml cmdlet to save the instance of the object, including the additional members...
can use the Import-Clixml cmdlet to re-create the instance of the object from the information...
Export-Clixml
Import-Clixml
```

<span data-ttu-id="aec92-182">`Get-Help` utilise le paramètre **Full** pour obtenir des informations d’aide pour `Add-Member` .</span><span class="sxs-lookup"><span data-stu-id="aec92-182">`Get-Help` uses the **Full** parameter to get help information for `Add-Member`.</span></span> <span data-ttu-id="aec92-183">L’objet **MamlCommandHelpInfo** est envoyé vers le pipeline.</span><span class="sxs-lookup"><span data-stu-id="aec92-183">The **MamlCommandHelpInfo** object is sent down the pipeline.</span></span> <span data-ttu-id="aec92-184">`Out-String` utilise le paramètre **Stream** pour convertir l’objet en une chaîne.</span><span class="sxs-lookup"><span data-stu-id="aec92-184">`Out-String` uses the **Stream** parameter to convert the object into a string.</span></span> <span data-ttu-id="aec92-185">`Select-String` utilise le paramètre **pattern** pour rechercher **Clixml** dans la chaîne.</span><span class="sxs-lookup"><span data-stu-id="aec92-185">`Select-String` uses the **Pattern** parameter to search the string for **Clixml** .</span></span>

### <span data-ttu-id="aec92-186">Exemple 10 : afficher une liste d’articles incluant un mot</span><span class="sxs-lookup"><span data-stu-id="aec92-186">Example 10: Display a list of articles that include a word</span></span>

<span data-ttu-id="aec92-187">Cet exemple affiche une liste d’articles qui incluent le mot **Remoting** .</span><span class="sxs-lookup"><span data-stu-id="aec92-187">This example displays a list of articles that include the word **remoting** .</span></span>

<span data-ttu-id="aec92-188">Lorsque vous entrez un mot qui n’apparaît pas dans un titre d’article, `Get-Help` affiche la liste des articles qui contiennent ce mot.</span><span class="sxs-lookup"><span data-stu-id="aec92-188">When you enter a word that doesn't appear in any article title, `Get-Help` displays a list of articles that include that word.</span></span>

```powershell
Get-Help -Name remoting
```

```Output
Name                              Category  Module                    Synopsis
----                              --------  ------                    --------
Install-PowerShellRemoting.ps1    External                            Install-PowerShellRemoting.ps1
Disable-PSRemoting                Cmdlet    Microsoft.PowerShell.Core Prevents remote users...
Enable-PSRemoting                 Cmdlet    Microsoft.PowerShell.Core Configures the computer...
```

### <span data-ttu-id="aec92-189">Exemple 11 : afficher l’aide spécifique au fournisseur</span><span class="sxs-lookup"><span data-stu-id="aec92-189">Example 11: Display provider-specific help</span></span>

<span data-ttu-id="aec92-190">Cet exemple montre deux façons d’obtenir l’aide spécifique au fournisseur pour `Get-Item` .</span><span class="sxs-lookup"><span data-stu-id="aec92-190">This example shows two ways of getting the provider-specific help for `Get-Item`.</span></span> <span data-ttu-id="aec92-191">Ces commandes obtiennent de l’aide qui explique comment utiliser l' `Get-Item` applet de commande dans le nœud **DataCollection** du fournisseur de SQL Server PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aec92-191">These commands get help that explains how to use the `Get-Item` cmdlet in the PowerShell SQL Server provider's **DataCollection** node.</span></span>

<span data-ttu-id="aec92-192">Le premier exemple utilise le `Get-Help` paramètre **path** pour spécifier le chemin d’accès du fournisseur SQL Server.</span><span class="sxs-lookup"><span data-stu-id="aec92-192">The first example uses the `Get-Help` **Path** parameter to specify the SQL Server provider's path.</span></span>
<span data-ttu-id="aec92-193">Étant donné que le chemin d’accès du fournisseur est spécifié, vous pouvez exécuter la commande à partir de n’importe quel emplacement de chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="aec92-193">Because the provider's path is specified, you can run the command from any path location.</span></span>

<span data-ttu-id="aec92-194">Le deuxième exemple utilise `Set-Location` pour naviguer jusqu’au chemin d’accès du fournisseur SQL Server.</span><span class="sxs-lookup"><span data-stu-id="aec92-194">The second example uses `Set-Location` to navigate to the SQL Server provider's path.</span></span> <span data-ttu-id="aec92-195">À partir de cet emplacement, le paramètre **path** n’est pas nécessaire pour `Get-Help` pour obtenir l’aide spécifique au fournisseur.</span><span class="sxs-lookup"><span data-stu-id="aec92-195">From that location, the **Path** parameter isn't needed for `Get-Help` to get the provider-specific help.</span></span>

```powershell
Get-Help Get-Item -Path SQLSERVER:\DataCollection
```

```Output
NAME

    Get-Item

SYNOPSIS

    Gets a collection of Server objects for the local computer and any computers

    to which you have made a SQL Server PowerShell connection.
    ...
```

```powershell
Set-Location SQLSERVER:\DataCollection
SQLSERVER:\DataCollection> Get-Help Get-Item
```

```Output
NAME

    Get-Item

SYNOPSIS

    Gets a collection of Server objects for the local computer and any computers

    to which you have made a SQL Server PowerShell connection.
    ...
```

### <span data-ttu-id="aec92-196">Exemple 12 : afficher l’aide d’un script</span><span class="sxs-lookup"><span data-stu-id="aec92-196">Example 12: Display help for a script</span></span>

<span data-ttu-id="aec92-197">Cet exemple obtient l’aide pour le `MyScript.ps1 script` .</span><span class="sxs-lookup"><span data-stu-id="aec92-197">This example gets help for the `MyScript.ps1 script`.</span></span> <span data-ttu-id="aec92-198">Pour plus d’informations sur la façon d’écrire de l’aide pour vos fonctions et scripts, consultez [about_Comment_Based_Help](./About/about_Comment_Based_Help.md).</span><span class="sxs-lookup"><span data-stu-id="aec92-198">For information about how to write help for your functions and scripts, see [about_Comment_Based_Help](./About/about_Comment_Based_Help.md).</span></span>

```powershell
Get-Help -Name C:\PS-Test\MyScript.ps1
```

## <span data-ttu-id="aec92-199">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="aec92-199">PARAMETERS</span></span>

### <span data-ttu-id="aec92-200">-Catégorie</span><span class="sxs-lookup"><span data-stu-id="aec92-200">-Category</span></span>

<span data-ttu-id="aec92-201">Affiche l'aide uniquement des éléments de la catégorie spécifiée et de leurs alias.</span><span class="sxs-lookup"><span data-stu-id="aec92-201">Displays help only for items in the specified category and their aliases.</span></span> <span data-ttu-id="aec92-202">Les articles conceptuels se trouvent dans la catégorie **HelpFile** .</span><span class="sxs-lookup"><span data-stu-id="aec92-202">Conceptual articles are in the **HelpFile** category.</span></span>

<span data-ttu-id="aec92-203">Les valeurs acceptables pour ce paramètre sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="aec92-203">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="aec92-204">Alias</span><span class="sxs-lookup"><span data-stu-id="aec92-204">Alias</span></span>
- <span data-ttu-id="aec92-205">Applet de commande</span><span class="sxs-lookup"><span data-stu-id="aec92-205">Cmdlet</span></span>
- <span data-ttu-id="aec92-206">Fournisseur</span><span class="sxs-lookup"><span data-stu-id="aec92-206">Provider</span></span>
- <span data-ttu-id="aec92-207">Général</span><span class="sxs-lookup"><span data-stu-id="aec92-207">General</span></span>
- <span data-ttu-id="aec92-208">Questions fréquentes (FAQ)</span><span class="sxs-lookup"><span data-stu-id="aec92-208">FAQ</span></span>
- <span data-ttu-id="aec92-209">Glossaire</span><span class="sxs-lookup"><span data-stu-id="aec92-209">Glossary</span></span>
- <span data-ttu-id="aec92-210">HelpFile</span><span class="sxs-lookup"><span data-stu-id="aec92-210">HelpFile</span></span>
- <span data-ttu-id="aec92-211">ScriptCommand</span><span class="sxs-lookup"><span data-stu-id="aec92-211">ScriptCommand</span></span>
- <span data-ttu-id="aec92-212">Fonction</span><span class="sxs-lookup"><span data-stu-id="aec92-212">Function</span></span>
- <span data-ttu-id="aec92-213">Filtrer</span><span class="sxs-lookup"><span data-stu-id="aec92-213">Filter</span></span>
- <span data-ttu-id="aec92-214">ExternalScript</span><span class="sxs-lookup"><span data-stu-id="aec92-214">ExternalScript</span></span>
- <span data-ttu-id="aec92-215">Tous</span><span class="sxs-lookup"><span data-stu-id="aec92-215">All</span></span>
- <span data-ttu-id="aec92-216">DefaultHelp</span><span class="sxs-lookup"><span data-stu-id="aec92-216">DefaultHelp</span></span>
- <span data-ttu-id="aec92-217">Workflow</span><span class="sxs-lookup"><span data-stu-id="aec92-217">Workflow</span></span>
- <span data-ttu-id="aec92-218">DscResource</span><span class="sxs-lookup"><span data-stu-id="aec92-218">DscResource</span></span>
- <span data-ttu-id="aec92-219">Classe</span><span class="sxs-lookup"><span data-stu-id="aec92-219">Class</span></span>
- <span data-ttu-id="aec92-220">Configuration</span><span class="sxs-lookup"><span data-stu-id="aec92-220">Configuration</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:
Accepted values: Alias, Cmdlet, Provider, General, FAQ, Glossary, HelpFile, ScriptCommand, Function, Filter, ExternalScript, All, DefaultHelp, Workflow, DscResource, Class, Configuration

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="aec92-221">-Composant</span><span class="sxs-lookup"><span data-stu-id="aec92-221">-Component</span></span>

<span data-ttu-id="aec92-222">Affiche les commandes avec la valeur de composant spécifiée, par exemple **Exchange** .</span><span class="sxs-lookup"><span data-stu-id="aec92-222">Displays commands with the specified component value, such as **Exchange** .</span></span> <span data-ttu-id="aec92-223">Entrez un nom de composant.</span><span class="sxs-lookup"><span data-stu-id="aec92-223">Enter a component name.</span></span>
<span data-ttu-id="aec92-224">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="aec92-224">Wildcard characters are permitted.</span></span> <span data-ttu-id="aec92-225">Ce paramètre n’a aucun effet sur les affichages de l’aide conceptuelle ( **about_** ).</span><span class="sxs-lookup"><span data-stu-id="aec92-225">This parameter has no effect on displays of conceptual ( **About_** ) help.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="aec92-226">-Detailed</span><span class="sxs-lookup"><span data-stu-id="aec92-226">-Detailed</span></span>

<span data-ttu-id="aec92-227">Ajoute la description des paramètre et les exemples à l'affichage de l'aide de base.</span><span class="sxs-lookup"><span data-stu-id="aec92-227">Adds parameter descriptions and examples to the basic help display.</span></span> <span data-ttu-id="aec92-228">Ce paramètre est effectif uniquement lorsque les fichiers d’aide sont installés sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="aec92-228">This parameter is effective only when the help files are installed on the computer.</span></span> <span data-ttu-id="aec92-229">Elle n’a aucun effet sur les affichages de l’aide conceptuelle ( **about_** ).</span><span class="sxs-lookup"><span data-stu-id="aec92-229">It has no effect on displays of conceptual ( **About_** ) help.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DetailedView
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="aec92-230">-Examples</span><span class="sxs-lookup"><span data-stu-id="aec92-230">-Examples</span></span>

<span data-ttu-id="aec92-231">Affiche uniquement le nom, le résumé et les exemples.</span><span class="sxs-lookup"><span data-stu-id="aec92-231">Displays only the name, synopsis, and examples.</span></span> <span data-ttu-id="aec92-232">Pour afficher uniquement les exemples, tapez `(Get-Help \<cmdlet-name\>).Examples` .</span><span class="sxs-lookup"><span data-stu-id="aec92-232">To display only the examples, type `(Get-Help \<cmdlet-name\>).Examples`.</span></span>

<span data-ttu-id="aec92-233">Ce paramètre est effectif uniquement lorsque les fichiers d’aide sont installés sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="aec92-233">This parameter is effective only when the help files are installed on the computer.</span></span> <span data-ttu-id="aec92-234">Elle n’a aucun effet sur les affichages de l’aide conceptuelle ( **about_** ).</span><span class="sxs-lookup"><span data-stu-id="aec92-234">It has no effect on displays of conceptual ( **About_** ) help.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Examples
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="aec92-235">-Full</span><span class="sxs-lookup"><span data-stu-id="aec92-235">-Full</span></span>

<span data-ttu-id="aec92-236">Affiche la totalité de l’article d’aide pour une applet de commande.</span><span class="sxs-lookup"><span data-stu-id="aec92-236">Displays the entire help article for a cmdlet.</span></span> <span data-ttu-id="aec92-237">**Full** comprend des descriptions de paramètres et des attributs, des exemples, des types d’objet d’entrée et de sortie, ainsi que des remarques supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="aec92-237">**Full** includes parameter descriptions and attributes, examples, input and output object types, and additional notes.</span></span>

<span data-ttu-id="aec92-238">Ce paramètre est effectif uniquement lorsque les fichiers d’aide sont installés sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="aec92-238">This parameter is effective only when the help files are installed on the computer.</span></span> <span data-ttu-id="aec92-239">Elle n’a aucun effet sur les affichages de l’aide conceptuelle ( **about_** ).</span><span class="sxs-lookup"><span data-stu-id="aec92-239">It has no effect on displays of conceptual ( **About_** ) help.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AllUsersView
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="aec92-240">-Fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="aec92-240">-Functionality</span></span>

<span data-ttu-id="aec92-241">Affiche l'aide pour des éléments ayant la fonctionnalité spécifiée.</span><span class="sxs-lookup"><span data-stu-id="aec92-241">Displays help for items with the specified functionality.</span></span> <span data-ttu-id="aec92-242">Entrez la fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="aec92-242">Enter the functionality.</span></span> <span data-ttu-id="aec92-243">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="aec92-243">Wildcard characters are permitted.</span></span> <span data-ttu-id="aec92-244">Ce paramètre n’a aucun effet sur les affichages de l’aide conceptuelle ( **about_** ).</span><span class="sxs-lookup"><span data-stu-id="aec92-244">This parameter has no effect on displays of conceptual ( **About_** ) help.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="aec92-245">-Name</span><span class="sxs-lookup"><span data-stu-id="aec92-245">-Name</span></span>

<span data-ttu-id="aec92-246">Obtient de l'aide sur la commande ou le concept spécifié.</span><span class="sxs-lookup"><span data-stu-id="aec92-246">Gets help about the specified command or concept.</span></span> <span data-ttu-id="aec92-247">Entrez le nom d’une applet de commande, d’une fonction, d’un fournisseur, d’un script ou d’un flux de travail, tel que `Get-Member` , un nom d’article conceptuel, tel que `about_Objects` , ou un alias, tel que `ls` .</span><span class="sxs-lookup"><span data-stu-id="aec92-247">Enter the name of a cmdlet, function, provider, script, or workflow, such as `Get-Member`, a conceptual article name, such as `about_Objects`, or an alias, such as `ls`.</span></span> <span data-ttu-id="aec92-248">Les caractères génériques sont autorisés dans les noms d’applet de commande et de fournisseur, mais vous ne pouvez pas utiliser de caractères génériques pour rechercher les noms des articles d’aide de fonction et de script.</span><span class="sxs-lookup"><span data-stu-id="aec92-248">Wildcard characters are permitted in cmdlet and provider names, but you can't use wildcard characters to find the names of function help and script help articles.</span></span>

<span data-ttu-id="aec92-249">Pour obtenir de l’aide sur un script qui ne se trouve pas dans un chemin d’accès qui est listé dans la `$env:Path` variable d’environnement, tapez le chemin d’accès et le nom de fichier du script.</span><span class="sxs-lookup"><span data-stu-id="aec92-249">To get help for a script that isn't located in a path that's listed in the `$env:Path` environment variable, type the script's path and file name.</span></span>

<span data-ttu-id="aec92-250">Si vous entrez le nom exact d’un article d’aide, `Get-Help` affiche le contenu de l’article.</span><span class="sxs-lookup"><span data-stu-id="aec92-250">If you enter the exact name of a help article, `Get-Help` displays the article contents.</span></span>

<span data-ttu-id="aec92-251">Si vous entrez un mot ou un modèle de mot qui apparaît dans plusieurs titres d’articles d’aide, `Get-Help` affiche une liste des titres correspondants.</span><span class="sxs-lookup"><span data-stu-id="aec92-251">If you enter a word or word pattern that appears in several help article titles, `Get-Help` displays a list of the matching titles.</span></span>

<span data-ttu-id="aec92-252">Si vous entrez du texte qui ne correspond à aucun titre d’article d’aide, `Get-Help` affiche une liste d’articles incluant ce texte dans leur contenu.</span><span class="sxs-lookup"><span data-stu-id="aec92-252">If you enter any text that doesn't match any help article titles, `Get-Help` displays a list of articles that include that text in their contents.</span></span>

<span data-ttu-id="aec92-253">Les noms des articles conceptuels, tels que `about_Objects` , doivent être entrés en anglais, même dans les versions non anglaises de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aec92-253">The names of conceptual articles, such as `about_Objects`, must be entered in English, even in non-English versions of PowerShell.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="aec92-254">-En ligne</span><span class="sxs-lookup"><span data-stu-id="aec92-254">-Online</span></span>

<span data-ttu-id="aec92-255">Affiche la version en ligne d’un article d’aide dans le navigateur par défaut.</span><span class="sxs-lookup"><span data-stu-id="aec92-255">Displays the online version of a help article in the default browser.</span></span> <span data-ttu-id="aec92-256">Ce paramètre est valide uniquement pour les articles d’aide sur les applets de commande, les fonctions, les workflows et les scripts.</span><span class="sxs-lookup"><span data-stu-id="aec92-256">This parameter is valid only for cmdlet, function, workflow, and script help articles.</span></span> <span data-ttu-id="aec92-257">Vous ne pouvez pas utiliser le paramètre **Online** avec `Get-Help` dans une session à distance.</span><span class="sxs-lookup"><span data-stu-id="aec92-257">You can't use the **Online** parameter with `Get-Help` in a remote session.</span></span>

<span data-ttu-id="aec92-258">Pour plus d’informations sur la prise en charge de cette fonctionnalité dans les articles d’aide que vous écrivez, consultez [about_Comment_Based_Help](./About/about_Comment_Based_Help.md)et [prise en charge de l’aide en ligne](/powershell/scripting/developer/module/supporting-online-help)et [écriture d’aide pour les applets de commande PowerShell](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets).</span><span class="sxs-lookup"><span data-stu-id="aec92-258">For information about supporting this feature in help articles that you write, see [about_Comment_Based_Help](./About/about_Comment_Based_Help.md), and [Supporting Online Help](/powershell/scripting/developer/module/supporting-online-help), and [Writing Help for PowerShell Cmdlets](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Online
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="aec92-259">Paramètres </span><span class="sxs-lookup"><span data-stu-id="aec92-259">-Parameter</span></span>

<span data-ttu-id="aec92-260">Affiche uniquement les descriptions détaillées des paramètres spécifiés.</span><span class="sxs-lookup"><span data-stu-id="aec92-260">Displays only the detailed descriptions of the specified parameters.</span></span> <span data-ttu-id="aec92-261">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="aec92-261">Wildcards are permitted.</span></span> <span data-ttu-id="aec92-262">Ce paramètre n’a aucun effet sur les affichages de l’aide conceptuelle ( **about_** ).</span><span class="sxs-lookup"><span data-stu-id="aec92-262">This parameter has no effect on displays of conceptual ( **About_** ) help.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Parameters
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="aec92-263">-Path</span><span class="sxs-lookup"><span data-stu-id="aec92-263">-Path</span></span>

<span data-ttu-id="aec92-264">Obtient l'aide qui explique le fonctionnement de l'applet de commande dans le chemin d'accès du fournisseur spécifié.</span><span class="sxs-lookup"><span data-stu-id="aec92-264">Gets help that explains how the cmdlet works in the specified provider path.</span></span> <span data-ttu-id="aec92-265">Entrez un chemin d’accès au fournisseur PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aec92-265">Enter a PowerShell provider path.</span></span>

<span data-ttu-id="aec92-266">Ce paramètre obtient une version personnalisée d’un article d’aide sur les applets de commande qui explique le fonctionnement de l’applet de commande dans le chemin d’accès du fournisseur PowerShell spécifié.</span><span class="sxs-lookup"><span data-stu-id="aec92-266">This parameter gets a customized version of a cmdlet help article that explains how the cmdlet works in the specified PowerShell provider path.</span></span> <span data-ttu-id="aec92-267">Ce paramètre est effectif uniquement pour l’aide relative à une applet de commande de fournisseur et uniquement lorsque le fournisseur comprend une version personnalisée de l’article d’aide sur l’applet de commande du fournisseur dans son fichier d’aide.</span><span class="sxs-lookup"><span data-stu-id="aec92-267">This parameter is effective only for help about a provider cmdlet and only when the provider includes a custom version of the provider cmdlet help article in its help file.</span></span> <span data-ttu-id="aec92-268">Pour utiliser ce paramètre, installez le fichier d'aide du module qui inclut le fournisseur.</span><span class="sxs-lookup"><span data-stu-id="aec92-268">To use this parameter, install the help file for the module that includes the provider.</span></span>

<span data-ttu-id="aec92-269">Pour afficher l’aide de l’applet de commande personnalisée pour un chemin d’accès de fournisseur, accédez à l’emplacement du chemin d’accès du fournisseur et entrez une `Get-Help` commande ou, à partir d’un emplacement de chemin d’accès, utilisez le paramètre **path** de `Get-Help` pour spécifier le chemin d’accès du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="aec92-269">To see the custom cmdlet help for a provider path, go to the provider path location and enter a `Get-Help` command or, from any path location, use the **Path** parameter of `Get-Help` to specify the provider path.</span></span> <span data-ttu-id="aec92-270">Vous pouvez également trouver l’aide en ligne de l’applet de commande personnalisée dans la section d’aide du fournisseur des articles d’aide.</span><span class="sxs-lookup"><span data-stu-id="aec92-270">You can also find custom cmdlet help online in the provider help section of the help articles.</span></span>

<span data-ttu-id="aec92-271">Pour plus d’informations sur les fournisseurs PowerShell, consultez [about_Providers](./About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="aec92-271">For more information about PowerShell providers, see [about_Providers](./About/about_Providers.md).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="aec92-272">-Rôle</span><span class="sxs-lookup"><span data-stu-id="aec92-272">-Role</span></span>

<span data-ttu-id="aec92-273">Affiche l'aide personnalisée du rôle d'utilisateur spécifié.</span><span class="sxs-lookup"><span data-stu-id="aec92-273">Displays help customized for the specified user role.</span></span> <span data-ttu-id="aec92-274">Entrez un rôle.</span><span class="sxs-lookup"><span data-stu-id="aec92-274">Enter a role.</span></span> <span data-ttu-id="aec92-275">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="aec92-275">Wildcard characters are permitted.</span></span>

<span data-ttu-id="aec92-276">Entrez le rôle joué par l'utilisateur dans une organisation.</span><span class="sxs-lookup"><span data-stu-id="aec92-276">Enter the role that the user plays in an organization.</span></span> <span data-ttu-id="aec92-277">Certaines applets de commande affichent du texte différent dans leurs fichiers d'aide en fonction de la valeur de ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="aec92-277">Some cmdlets display different text in their help files based on the value of this parameter.</span></span> <span data-ttu-id="aec92-278">Ce paramètre n'a aucun effet sur l'aide des applets de commande de base.</span><span class="sxs-lookup"><span data-stu-id="aec92-278">This parameter has no effect on help for the core cmdlets.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="aec92-279">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="aec92-279">CommonParameters</span></span>

<span data-ttu-id="aec92-280">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="aec92-280">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="aec92-281">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="aec92-281">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="aec92-282">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="aec92-282">INPUTS</span></span>

### <span data-ttu-id="aec92-283">Aucun</span><span class="sxs-lookup"><span data-stu-id="aec92-283">None</span></span>

<span data-ttu-id="aec92-284">Vous ne pouvez pas envoyer d’objets dans le pipeline vers `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="aec92-284">You can't send objects down the pipeline to `Get-Help`.</span></span>

## <span data-ttu-id="aec92-285">SORTIES</span><span class="sxs-lookup"><span data-stu-id="aec92-285">OUTPUTS</span></span>

### <span data-ttu-id="aec92-286">ExtendedCmdletHelpInfo</span><span class="sxs-lookup"><span data-stu-id="aec92-286">ExtendedCmdletHelpInfo</span></span>

<span data-ttu-id="aec92-287">Si vous exécutez `Get-Help` sur une commande qui n’a pas de fichier d’aide, `Get-Help` retourne un objet **ExtendedCmdletHelpInfo** qui représente l’aide générée automatiquement.</span><span class="sxs-lookup"><span data-stu-id="aec92-287">If you run `Get-Help` on a command that doesn't have a help file, `Get-Help` returns an **ExtendedCmdletHelpInfo** object that represents autogenerated help.</span></span>

### <span data-ttu-id="aec92-288">System.String</span><span class="sxs-lookup"><span data-stu-id="aec92-288">System.String</span></span>

<span data-ttu-id="aec92-289">Si vous recevez un article d’aide conceptuelle, `Get-Help` le retourne sous forme de chaîne.</span><span class="sxs-lookup"><span data-stu-id="aec92-289">If you get a conceptual help article, `Get-Help` returns it as a string.</span></span>

### <span data-ttu-id="aec92-290">MamlCommandHelpInfo</span><span class="sxs-lookup"><span data-stu-id="aec92-290">MamlCommandHelpInfo</span></span>

<span data-ttu-id="aec92-291">Si vous recevez une commande qui contient un fichier d’aide, `Get-Help` retourne un objet **MamlCommandHelpInfo** .</span><span class="sxs-lookup"><span data-stu-id="aec92-291">If you get a command that has a help file, `Get-Help` returns a **MamlCommandHelpInfo** object.</span></span>

## <span data-ttu-id="aec92-292">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="aec92-292">NOTES</span></span>

<span data-ttu-id="aec92-293">PowerShell 3,0 n’inclut pas les fichiers d’aide.</span><span class="sxs-lookup"><span data-stu-id="aec92-293">PowerShell 3.0 doesn't include help files.</span></span> <span data-ttu-id="aec92-294">Pour télécharger et installer les fichiers d’aide que `Get-Help` lit, utilisez l’applet de commande `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="aec92-294">To download and install the help files that `Get-Help` reads, use the `Update-Help` cmdlet.</span></span> <span data-ttu-id="aec92-295">Vous pouvez utiliser l' `Update-Help` applet de commande pour télécharger et installer les fichiers d’aide pour les commandes de base fournies avec PowerShell et pour tous les modules que vous installez.</span><span class="sxs-lookup"><span data-stu-id="aec92-295">You can use the `Update-Help` cmdlet to download and install help files for the core commands that come with PowerShell and for any modules that you install.</span></span> <span data-ttu-id="aec92-296">Vous pouvez également l'utiliser pour mettre à jour les fichiers d'aide afin que l'aide sur votre ordinateur ne soit jamais obsolète.</span><span class="sxs-lookup"><span data-stu-id="aec92-296">You can also use it to update the help files so that the help on your computer is never outdated.</span></span>

<span data-ttu-id="aec92-297">Vous pouvez également lire les articles d’aide sur les commandes fournies avec PowerShell Online à partir de [prise en main avec Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="aec92-297">You can also read the help articles about the commands that come with PowerShell online starting at [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

<span data-ttu-id="aec92-298">`Get-Help` affiche l’aide dans l’ensemble de paramètres régionaux pour le système d’exploitation Windows ou dans la langue de secours pour ces paramètres régionaux.</span><span class="sxs-lookup"><span data-stu-id="aec92-298">`Get-Help` displays help in the locale set for the Windows operating system or in the fallback language for that locale.</span></span> <span data-ttu-id="aec92-299">Si vous n’avez pas de fichiers d’aide pour les paramètres régionaux principaux ou de secours, `Get-Help` se comporte comme s’il n’y avait pas de fichiers d’aide sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="aec92-299">If you don't have help files for the primary or fallback locale, `Get-Help` behaves as if there are no help files on the computer.</span></span> <span data-ttu-id="aec92-300">Pour obtenir de l’aide pour des paramètres régionaux différents, utilisez **région** et **langue** dans le panneau de configuration pour modifier les paramètres.</span><span class="sxs-lookup"><span data-stu-id="aec92-300">To get help for a different locale, use **Region** and **Language** in Control Panel to change the settings.</span></span> <span data-ttu-id="aec92-301">Sur Windows 10, **paramètres** , **heure & langue** .</span><span class="sxs-lookup"><span data-stu-id="aec92-301">On Windows 10, **Settings** , **Time & Language** .</span></span>

<span data-ttu-id="aec92-302">La vue complète de l’aide comprend une table d’informations sur les paramètres.</span><span class="sxs-lookup"><span data-stu-id="aec92-302">The full view of help includes a table of information about the parameters.</span></span> <span data-ttu-id="aec92-303">La table inclut les champs suivants :</span><span class="sxs-lookup"><span data-stu-id="aec92-303">The table includes the following fields:</span></span>

- <span data-ttu-id="aec92-304">**Requis** .</span><span class="sxs-lookup"><span data-stu-id="aec92-304">**Required** .</span></span> <span data-ttu-id="aec92-305">indique si le paramètre est obligatoire (true) ou facultatif (false).</span><span class="sxs-lookup"><span data-stu-id="aec92-305">Indicates whether the parameter is required (true) or optional (false).</span></span>

- <span data-ttu-id="aec92-306">**Position** .</span><span class="sxs-lookup"><span data-stu-id="aec92-306">**Position** .</span></span> <span data-ttu-id="aec92-307">Indique si le paramètre est nommé ou positionnel (numérique).</span><span class="sxs-lookup"><span data-stu-id="aec92-307">Indicates whether the parameter is named or positional (numeric).</span></span> <span data-ttu-id="aec92-308">les paramètres positionnels doivent apparaître à un emplacement spécifié de la commande.</span><span class="sxs-lookup"><span data-stu-id="aec92-308">Positional parameters must appear in a specified place in the command.</span></span>

- <span data-ttu-id="aec92-309">**Nommé** indique que le nom du paramètre est obligatoire, mais que le paramètre peut apparaître n’importe où dans la commande.</span><span class="sxs-lookup"><span data-stu-id="aec92-309">**Named** indicates that the parameter name is required, but that the parameter can appear anywhere in the command.</span></span>

- <span data-ttu-id="aec92-310">**Numeric** indique que le nom du paramètre est facultatif, mais lorsque le nom est omis, le paramètre doit se trouver à l’emplacement spécifié par le nombre.</span><span class="sxs-lookup"><span data-stu-id="aec92-310">**Numeric** indicates that the parameter name is optional, but when the name is omitted, the parameter must be in the place specified by the number.</span></span> <span data-ttu-id="aec92-311">Par exemple, `2` indique que lorsque le nom du paramètre est omis, le paramètre doit être le deuxième ou le seul paramètre sans nom dans la commande.</span><span class="sxs-lookup"><span data-stu-id="aec92-311">For example, `2` indicates that when the parameter name is omitted, the parameter must be the second or only unnamed parameter in the command.</span></span> <span data-ttu-id="aec92-312">Quand le nom du paramètre est utilisé, le paramètre peut apparaître n'importe où dans la commande.</span><span class="sxs-lookup"><span data-stu-id="aec92-312">When the parameter name is used, the parameter can appear anywhere in the command.</span></span>

- <span data-ttu-id="aec92-313">**Valeur par défaut** .</span><span class="sxs-lookup"><span data-stu-id="aec92-313">**Default value** .</span></span> <span data-ttu-id="aec92-314">La valeur du paramètre ou le comportement par défaut que PowerShell utilise si vous n’incluez pas le paramètre dans la commande.</span><span class="sxs-lookup"><span data-stu-id="aec92-314">The parameter value or default behavior that PowerShell uses if you don't include the parameter in the command.</span></span>

- <span data-ttu-id="aec92-315">Accepte l’entrée de pipeline.</span><span class="sxs-lookup"><span data-stu-id="aec92-315">Accepts pipeline input.</span></span> <span data-ttu-id="aec92-316">Indique si vous pouvez (true) ou ne pouvez pas (false) envoyer des objets au paramètre via un pipeline.</span><span class="sxs-lookup"><span data-stu-id="aec92-316">Indicates whether you can (true) or can't (false) send objects to the parameter through a pipeline.</span></span> <span data-ttu-id="aec92-317">**Par nom de propriété** signifie que l’objet en pipeline doit avoir une propriété qui porte le même nom que le nom du paramètre.</span><span class="sxs-lookup"><span data-stu-id="aec92-317">**By Property Name** means that the pipelined object must have a property that has the same name as the parameter name.</span></span>

- <span data-ttu-id="aec92-318">**Accepte les caractères génériques** .</span><span class="sxs-lookup"><span data-stu-id="aec92-318">**Accepts wildcard characters** .</span></span> <span data-ttu-id="aec92-319">Indique si la valeur d’un paramètre peut inclure des caractères génériques, tels qu’un astérisque () ou un point d' `*` interrogation ( `?` ).</span><span class="sxs-lookup"><span data-stu-id="aec92-319">Indicates whether the value of a parameter can include wildcard characters, such as an asterisk (`*`) or question mark (`?`).</span></span>

## <span data-ttu-id="aec92-320">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="aec92-320">RELATED LINKS</span></span>

[<span data-ttu-id="aec92-321">about_Command_Syntax</span><span class="sxs-lookup"><span data-stu-id="aec92-321">about_Command_Syntax</span></span>](About/about_Command_Syntax.md)

[<span data-ttu-id="aec92-322">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="aec92-322">about_Comment_Based_Help</span></span>](./About/about_Comment_Based_Help.md)

[<span data-ttu-id="aec92-323">Get-Command</span><span class="sxs-lookup"><span data-stu-id="aec92-323">Get-Command</span></span>](Get-Command.md)

[<span data-ttu-id="aec92-324">Prise en charge de l’aide actualisable</span><span class="sxs-lookup"><span data-stu-id="aec92-324">Supporting Updatable Help</span></span>](/powershell/scripting/developer/module/supporting-updatable-help)

[<span data-ttu-id="aec92-325">Update-Help</span><span class="sxs-lookup"><span data-stu-id="aec92-325">Update-Help</span></span>](Update-Help.md)

[<span data-ttu-id="aec92-326">Écriture de rubriques d’aide basée sur les commentaires</span><span class="sxs-lookup"><span data-stu-id="aec92-326">Writing Comment-Based Help Topics</span></span>](/powershell/scripting/developer/help/writing-comment-based-help-topics)

[<span data-ttu-id="aec92-327">Écriture d’une aide pour les applets de commande PowerShell</span><span class="sxs-lookup"><span data-stu-id="aec92-327">Writing Help for PowerShell Cmdlets</span></span>](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets)
