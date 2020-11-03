---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 09/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-help?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Help
ms.openlocfilehash: 1a4a3f7050c3da2a73ae0d5319938117284076b7
ms.sourcegitcommit: 05f578d3fca0d9663bb1e4f76e2f14604f5303ae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2020
ms.locfileid: "93206210"
---
# <span data-ttu-id="29b69-103">Get-Help</span><span class="sxs-lookup"><span data-stu-id="29b69-103">Get-Help</span></span>

## <span data-ttu-id="29b69-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="29b69-104">SYNOPSIS</span></span>
<span data-ttu-id="29b69-105">Affiche des informations sur les commandes et les concepts PowerShell.</span><span class="sxs-lookup"><span data-stu-id="29b69-105">Displays information about PowerShell commands and concepts.</span></span>

## <span data-ttu-id="29b69-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="29b69-106">SYNTAX</span></span>

### <span data-ttu-id="29b69-107">AllUsersView (par défaut)</span><span class="sxs-lookup"><span data-stu-id="29b69-107">AllUsersView (Default)</span></span>

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Full] [-Component <String[]>]
 [-Functionality <String[]>] [-Role <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="29b69-108">DetailedView</span><span class="sxs-lookup"><span data-stu-id="29b69-108">DetailedView</span></span>

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] -Detailed
 [-Component <String[]>] [-Functionality <String[]>] [-Role <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="29b69-109">Exemples</span><span class="sxs-lookup"><span data-stu-id="29b69-109">Examples</span></span>

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] -Examples
 [-Component <String[]>] [-Functionality <String[]>] [-Role <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="29b69-110">Paramètres</span><span class="sxs-lookup"><span data-stu-id="29b69-110">Parameters</span></span>

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] -Parameter <String[]>
 [-Component <String[]>] [-Functionality <String[]>] [-Role <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="29b69-111">En ligne</span><span class="sxs-lookup"><span data-stu-id="29b69-111">Online</span></span>

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>]
 [-Functionality <String[]>] [-Role <String[]>] -Online [<CommonParameters>]
```

### <span data-ttu-id="29b69-112">ShowWindow</span><span class="sxs-lookup"><span data-stu-id="29b69-112">ShowWindow</span></span>

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>]
 [-Functionality <String[]>] [-Role <String[]>] -ShowWindow [<CommonParameters>]
```

## <span data-ttu-id="29b69-113">Description</span><span class="sxs-lookup"><span data-stu-id="29b69-113">DESCRIPTION</span></span>

<span data-ttu-id="29b69-114">L' `Get-Help` applet de commande affiche des informations sur les concepts et les commandes PowerShell, y compris les applets de commande, les fonctions, les commandes Common Information Model (CIM), les flux de travail, les fournisseurs, les alias et les scripts.</span><span class="sxs-lookup"><span data-stu-id="29b69-114">The `Get-Help` cmdlet displays information about PowerShell concepts and commands, including cmdlets, functions, Common Information Model (CIM) commands, workflows, providers, aliases, and scripts.</span></span>

<span data-ttu-id="29b69-115">Pour obtenir de l’aide pour une applet de commande PowerShell, tapez `Get-Help` suivi du nom de l’applet de commande, par exemple : `Get-Help Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="29b69-115">To get help for a PowerShell cmdlet, type `Get-Help` followed by the cmdlet name, such as: `Get-Help Get-Process`.</span></span>

<span data-ttu-id="29b69-116">Les articles d’aide conceptuelle dans PowerShell commencent par **about_** , comme **about_Comparison_Operators** .</span><span class="sxs-lookup"><span data-stu-id="29b69-116">Conceptual help articles in PowerShell begin with **about_** , such as **about_Comparison_Operators** .</span></span> <span data-ttu-id="29b69-117">Pour afficher tous les articles **about_** , tapez `Get-Help about_*` .</span><span class="sxs-lookup"><span data-stu-id="29b69-117">To see all **about_** articles, type `Get-Help about_*`.</span></span> <span data-ttu-id="29b69-118">Pour afficher un article particulier, tapez `Get-Help about_<article-name>` , par exemple `Get-Help about_Comparison_Operators` .</span><span class="sxs-lookup"><span data-stu-id="29b69-118">To see a particular article, type `Get-Help about_<article-name>`, such as `Get-Help about_Comparison_Operators`.</span></span>

<span data-ttu-id="29b69-119">Pour obtenir de l’aide pour un fournisseur PowerShell, tapez `Get-Help` suivi du nom du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="29b69-119">To get help for a PowerShell provider, type `Get-Help` followed by the provider name.</span></span> <span data-ttu-id="29b69-120">Par exemple, pour obtenir de l’aide pour le fournisseur de certificats, tapez `Get-Help Certificate` .</span><span class="sxs-lookup"><span data-stu-id="29b69-120">For example, to get help for the Certificate provider, type `Get-Help Certificate`.</span></span>

<span data-ttu-id="29b69-121">Vous pouvez également taper `help` ou `man` , qui affiche un écran de texte à la fois.</span><span class="sxs-lookup"><span data-stu-id="29b69-121">You can also type `help` or `man`, which displays one screen of text at a time.</span></span> <span data-ttu-id="29b69-122">Ou, `<cmdlet-name> -?` , qui est identique à `Get-Help` , mais fonctionne uniquement pour les applets de commande.</span><span class="sxs-lookup"><span data-stu-id="29b69-122">Or, `<cmdlet-name> -?`, that is identical to `Get-Help`, but only works for cmdlets.</span></span>

<span data-ttu-id="29b69-123">`Get-Help` Obtient le contenu de l’aide qu’il affiche à partir des fichiers d’aide sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="29b69-123">`Get-Help` gets the help content that it displays from help files on your computer.</span></span> <span data-ttu-id="29b69-124">Sans les fichiers d’aide, `Get-Help` affiche uniquement les informations de base sur les applets de commande.</span><span class="sxs-lookup"><span data-stu-id="29b69-124">Without the help files, `Get-Help` displays only basic information about cmdlets.</span></span> <span data-ttu-id="29b69-125">Certains modules PowerShell incluent des fichiers d’aide.</span><span class="sxs-lookup"><span data-stu-id="29b69-125">Some PowerShell modules include help files.</span></span> <span data-ttu-id="29b69-126">À compter de PowerShell 3,0, les modules fournis avec le système d’exploitation Windows n’incluent pas les fichiers d’aide.</span><span class="sxs-lookup"><span data-stu-id="29b69-126">Beginning in PowerShell 3.0, the modules that come with the Windows operating system don't include help files.</span></span> <span data-ttu-id="29b69-127">Pour télécharger ou mettre à jour les fichiers d’aide d’un module dans PowerShell 3,0, utilisez l’applet de commande `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="29b69-127">To download or update the help files for a module in PowerShell 3.0, use the `Update-Help` cmdlet.</span></span>

<span data-ttu-id="29b69-128">Vous pouvez également consulter les documents d’aide PowerShell en ligne dans le Microsoft Docs. Pour obtenir la version en ligne d’un fichier d’aide, utilisez le paramètre **Online** , tel que : `Get-Help Get-Process -Online` .</span><span class="sxs-lookup"><span data-stu-id="29b69-128">You can also view the PowerShell help documents online in the Microsoft Docs. To get the online version of a help file, use the **Online** parameter, such as: `Get-Help Get-Process -Online`.</span></span> <span data-ttu-id="29b69-129">Pour lire toute la documentation PowerShell, consultez la [documentation Microsoft docs PowerShell](/powershell).</span><span class="sxs-lookup"><span data-stu-id="29b69-129">To read all the PowerShell documentation, see the Microsoft Docs [PowerShell Documentation](/powershell).</span></span>

<span data-ttu-id="29b69-130">Si vous tapez `Get-Help` suivi du nom exact d’un article d’aide, ou d’un mot unique à un article d’aide, `Get-Help` affiche le contenu de l’article.</span><span class="sxs-lookup"><span data-stu-id="29b69-130">If you type `Get-Help` followed by the exact name of a help article, or by a word unique to a help article, `Get-Help` displays the article's content.</span></span> <span data-ttu-id="29b69-131">Si vous spécifiez le nom exact d’un alias de commande, `Get-Help` affiche l’aide de la commande d’origine.</span><span class="sxs-lookup"><span data-stu-id="29b69-131">If you specify the exact name of a command alias, `Get-Help` displays the help for the original command.</span></span> <span data-ttu-id="29b69-132">Si vous entrez un mot ou un modèle de mot qui apparaît dans plusieurs titres d’articles d’aide, `Get-Help` affiche une liste des titres correspondants.</span><span class="sxs-lookup"><span data-stu-id="29b69-132">If you enter a word or word pattern that appears in several help article titles, `Get-Help` displays a list of the matching titles.</span></span> <span data-ttu-id="29b69-133">Si vous entrez du texte qui n’apparaît pas dans les titres des articles d’aide, `Get-Help` affiche une liste d’articles qui contiennent ce texte dans leur contenu.</span><span class="sxs-lookup"><span data-stu-id="29b69-133">If you enter any text that doesn't appear in any help article titles, `Get-Help` displays a list of articles that include that text in their contents.</span></span>

<span data-ttu-id="29b69-134">`Get-Help` peut obtenir des articles d’aide pour toutes les langues et paramètres régionaux pris en charge.</span><span class="sxs-lookup"><span data-stu-id="29b69-134">`Get-Help` can get help articles for all supported languages and locales.</span></span> <span data-ttu-id="29b69-135">`Get-Help` recherche d’abord les fichiers d’aide dans les paramètres régionaux définis pour Windows, puis dans les paramètres régionaux parents, par exemple **PT** pour **pt-br** , puis dans des paramètres régionaux de secours.</span><span class="sxs-lookup"><span data-stu-id="29b69-135">`Get-Help` first looks for help files in the locale set for Windows, then in the parent locale, such as **pt** for **pt-BR** , and then in a fallback locale.</span></span> <span data-ttu-id="29b69-136">À compter de PowerShell 3,0, si `Get-Help` ne trouve pas l’aide dans les paramètres régionaux de secours, il recherche des articles d’aide en anglais, en **-US** , avant de renvoyer un message d’erreur ou d’afficher l’aide générée automatiquement.</span><span class="sxs-lookup"><span data-stu-id="29b69-136">Beginning in PowerShell 3.0, if `Get-Help` doesn't find help in the fallback locale, it looks for help articles in English, **en-US** , before it returns an error message or displaying autogenerated help.</span></span>

<span data-ttu-id="29b69-137">Pour plus d’informations sur les symboles qui `Get-Help` s’affichent dans le diagramme de syntaxe de commande, consultez [about_Command_Syntax](./About/about_Command_Syntax.md).</span><span class="sxs-lookup"><span data-stu-id="29b69-137">For information about the symbols that `Get-Help` displays in the command syntax diagram, see [about_Command_Syntax](./About/about_Command_Syntax.md).</span></span>
<span data-ttu-id="29b69-138">Pour plus d’informations sur les attributs de paramètres, tels que **Required** et **Position** , consultez [about_Parameters](./About/about_Parameters.md).</span><span class="sxs-lookup"><span data-stu-id="29b69-138">For information about parameter attributes, such as **Required** and **Position** , see [about_Parameters](./About/about_Parameters.md).</span></span>

>[!NOTE]
> <span data-ttu-id="29b69-139">Dans PowerShell 3,0 et PowerShell 4,0, `Get-Help` les articles **About** ne peuvent pas être détectés dans les modules, sauf si le module est importé dans la session active.</span><span class="sxs-lookup"><span data-stu-id="29b69-139">In PowerShell 3.0 and PowerShell 4.0, `Get-Help` can't find **About** articles in modules unless the module is imported into the current session.</span></span> <span data-ttu-id="29b69-140">Il s'agit d'un problème connu.</span><span class="sxs-lookup"><span data-stu-id="29b69-140">This is a known issue.</span></span> <span data-ttu-id="29b69-141">Pour obtenir des **informations sur** les articles d’un module, importez le module à l’aide de l’applet de commande `Import-Module` ou en exécutant une applet de commande incluse dans le module.</span><span class="sxs-lookup"><span data-stu-id="29b69-141">To get **About** articles in a module, import the module, either by using the `Import-Module` cmdlet or by running a cmdlet that's included in the module.</span></span>

## <span data-ttu-id="29b69-142">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="29b69-142">EXAMPLES</span></span>

### <span data-ttu-id="29b69-143">Exemple 1 : afficher les informations d’aide de base sur une applet de commande</span><span class="sxs-lookup"><span data-stu-id="29b69-143">Example 1: Display basic help information about a cmdlet</span></span>

<span data-ttu-id="29b69-144">Ces exemples affichent des informations d’aide de base sur l’applet de commande `Format-Table` .</span><span class="sxs-lookup"><span data-stu-id="29b69-144">These examples display basic help information about the `Format-Table` cmdlet.</span></span>

```powershell
Get-Help Format-Table
Get-Help -Name Format-Table
Format-Table -?
```

<span data-ttu-id="29b69-145">`Get-Help <cmdlet-name>` est la syntaxe la plus simple et la syntaxe par défaut de l’applet de commande `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="29b69-145">`Get-Help <cmdlet-name>` is the simplest and default syntax of `Get-Help` cmdlet.</span></span> <span data-ttu-id="29b69-146">Vous pouvez omettre le paramètre **Name** .</span><span class="sxs-lookup"><span data-stu-id="29b69-146">You can omit the **Name** parameter.</span></span>

<span data-ttu-id="29b69-147">La syntaxe `<cmdlet-name> -?` fonctionne uniquement pour les applets de commande.</span><span class="sxs-lookup"><span data-stu-id="29b69-147">The syntax `<cmdlet-name> -?` works only for cmdlets.</span></span>

### <span data-ttu-id="29b69-148">Exemple 2 : afficher les informations de base une page à la fois</span><span class="sxs-lookup"><span data-stu-id="29b69-148">Example 2: Display basic information one page at a time</span></span>

<span data-ttu-id="29b69-149">Ces exemples affichent des informations d’aide de base sur l’applet de commande `Format-Table` , une page à la fois.</span><span class="sxs-lookup"><span data-stu-id="29b69-149">These examples display basic help information about the `Format-Table` cmdlet one page at a time.</span></span>

```powershell
help Format-Table
man Format-Table
Get-Help Format-Table | Out-Host -Paging
```

<span data-ttu-id="29b69-150">`help` est une fonction qui exécute `Get-Help` l’applet de commande en interne et affiche le résultat une page à la fois.</span><span class="sxs-lookup"><span data-stu-id="29b69-150">`help` is a function that runs `Get-Help` cmdlet internally and displays the result one page at a time.</span></span>

<span data-ttu-id="29b69-151">`man` alias de la `help` fonction.</span><span class="sxs-lookup"><span data-stu-id="29b69-151">`man` is an alias for the `help` function.</span></span>

<span data-ttu-id="29b69-152">`Get-Help Format-Table` envoie l’objet dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="29b69-152">`Get-Help Format-Table` sends the object down the pipeline.</span></span> <span data-ttu-id="29b69-153">`Out-Host -Paging` reçoit la sortie du pipeline et l’affiche une page à la fois.</span><span class="sxs-lookup"><span data-stu-id="29b69-153">`Out-Host -Paging` receives the output from the pipeline and displays it one page at a time.</span></span> <span data-ttu-id="29b69-154">Pour plus d’informations, consultez [Out-Host](Out-Host.md).</span><span class="sxs-lookup"><span data-stu-id="29b69-154">For more information, see [Out-Host](Out-Host.md).</span></span>

### <span data-ttu-id="29b69-155">Exemple 3 : afficher plus d’informations pour une applet de commande</span><span class="sxs-lookup"><span data-stu-id="29b69-155">Example 3: Display more information for a cmdlet</span></span>

<span data-ttu-id="29b69-156">Ces exemples affichent des informations d’aide plus détaillées sur l’applet de commande `Format-Table` .</span><span class="sxs-lookup"><span data-stu-id="29b69-156">These examples display more detailed help information about the `Format-Table` cmdlet.</span></span>

```powershell
Get-Help Format-Table -Detailed
Get-Help Format-Table -Full
```

<span data-ttu-id="29b69-157">Le paramètre **detailed** affiche la vue détaillée de l’article d’aide qui comprend des descriptions de paramètres et des exemples.</span><span class="sxs-lookup"><span data-stu-id="29b69-157">The **Detailed** parameter displays the help article's detailed view that includes parameter descriptions and examples.</span></span>

<span data-ttu-id="29b69-158">Le paramètre **Full** affiche la vue complète de l’article d’aide qui comprend des descriptions de paramètres, des exemples, des types d’objet d’entrée et de sortie, ainsi que des remarques supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="29b69-158">The **Full** parameter displays the help article's full view that includes parameter descriptions, examples, input and output object types, and additional notes.</span></span>

<span data-ttu-id="29b69-159">Les paramètres **détaillés** et **complets** sont effectifs uniquement pour les commandes qui ont des fichiers d’aide installés sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="29b69-159">The **Detailed** and **Full** parameters are effective only for the commands that have help files installed on the computer.</span></span> <span data-ttu-id="29b69-160">Les paramètres ne sont pas efficaces pour les articles d’aide conceptuel ( **about_** ).</span><span class="sxs-lookup"><span data-stu-id="29b69-160">The parameters aren't effective for the conceptual ( **about_** ) help articles.</span></span>

### <span data-ttu-id="29b69-161">Exemple 4 : afficher les parties sélectionnées d’une applet de commande à l’aide de paramètres</span><span class="sxs-lookup"><span data-stu-id="29b69-161">Example 4: Display selected parts of a cmdlet by using parameters</span></span>

<span data-ttu-id="29b69-162">Ces exemples affichent les parties sélectionnées de l’aide de l’applet de commande `Format-Table` .</span><span class="sxs-lookup"><span data-stu-id="29b69-162">These examples display selected portions of the `Format-Table` cmdlet help.</span></span>

```powershell
Get-Help Format-Table -Examples
Get-Help Format-Table -Parameter *
Get-Help Format-Table -Parameter GroupBy
```

<span data-ttu-id="29b69-163">Le paramètre **exemples** affiche le **nom** et les sections **Synopsis** du fichier d’aide, ainsi que tous les exemples.</span><span class="sxs-lookup"><span data-stu-id="29b69-163">The **Examples** parameter displays the help file's **NAME** and **SYNOPSIS** sections, and all the Examples.</span></span> <span data-ttu-id="29b69-164">Vous ne pouvez pas spécifier un exemple de nombre, car le paramètre d' **exemples** est un paramètre de commutateur.</span><span class="sxs-lookup"><span data-stu-id="29b69-164">You can't specify an Example number because the **Examples** parameter is a switch parameter.</span></span>

<span data-ttu-id="29b69-165">Le **paramètre parameter affiche** uniquement les descriptions des paramètres spécifiés.</span><span class="sxs-lookup"><span data-stu-id="29b69-165">The **Parameter** parameter displays only the descriptions of the specified parameters.</span></span> <span data-ttu-id="29b69-166">Si vous spécifiez uniquement le `*` caractère générique astérisque (), il affiche les descriptions de tous les paramètres.</span><span class="sxs-lookup"><span data-stu-id="29b69-166">If you specify only the asterisk (`*`) wildcard character, it displays the descriptions of all parameters.</span></span>
<span data-ttu-id="29b69-167">Quand le **paramètre** spécifie un nom de paramètre tel que **GroupBy** , les informations sur ce paramètre sont affichées.</span><span class="sxs-lookup"><span data-stu-id="29b69-167">When **Parameter** specifies a parameter name such as **GroupBy** , information about that parameter is shown.</span></span>

<span data-ttu-id="29b69-168">Ces paramètres ne sont pas efficaces pour les articles d’aide conceptuel ( **about_** ).</span><span class="sxs-lookup"><span data-stu-id="29b69-168">These parameters aren't effective for the conceptual ( **about_** ) help articles.</span></span>

### <span data-ttu-id="29b69-169">Exemple 5 : afficher la version en ligne de l’aide</span><span class="sxs-lookup"><span data-stu-id="29b69-169">Example 5: Display online version of help</span></span>

<span data-ttu-id="29b69-170">Cet exemple affiche la version en ligne de l’article d’aide pour l’applet de commande `Format-Table` dans votre navigateur Web par défaut.</span><span class="sxs-lookup"><span data-stu-id="29b69-170">This example displays the online version of the help article for the `Format-Table` cmdlet in your default web browser.</span></span>

```powershell
Get-Help Format-Table -Online
```

### <span data-ttu-id="29b69-171">Exemple 6 : afficher de l’aide sur le système d’aide</span><span class="sxs-lookup"><span data-stu-id="29b69-171">Example 6: Display help about the help system</span></span>

<span data-ttu-id="29b69-172">L' `Get-Help` applet de commande sans paramètres affiche des informations sur le système d’aide PowerShell.</span><span class="sxs-lookup"><span data-stu-id="29b69-172">The `Get-Help` cmdlet without parameters displays information about the PowerShell help system.</span></span>

```powershell
Get-Help
```

### <span data-ttu-id="29b69-173">Exemple 7 : afficher les articles d’aide disponibles</span><span class="sxs-lookup"><span data-stu-id="29b69-173">Example 7: Display available help articles</span></span>

<span data-ttu-id="29b69-174">Cet exemple affiche une liste de tous les articles d’aide disponibles sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="29b69-174">This example displays a list of all help articles available on your computer.</span></span>

```powershell
Get-Help *
```

### <span data-ttu-id="29b69-175">Exemple 8 : afficher une liste d’articles conceptuels</span><span class="sxs-lookup"><span data-stu-id="29b69-175">Example 8: Display a list of conceptual articles</span></span>

<span data-ttu-id="29b69-176">Cet exemple affiche une liste des articles conceptuels inclus dans l’aide de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="29b69-176">This example displays a list of the conceptual articles included in PowerShell help.</span></span> <span data-ttu-id="29b69-177">Tous ces articles commencent par les caractères **about_** .</span><span class="sxs-lookup"><span data-stu-id="29b69-177">All these articles begin with the characters **about_** .</span></span> <span data-ttu-id="29b69-178">Pour afficher un fichier d’aide particulier, tapez `Get-Help \<about_article-name\>` , par exemple, `Get-Help about_Signing` .</span><span class="sxs-lookup"><span data-stu-id="29b69-178">To display a particular help file, type `Get-Help \<about_article-name\>`, for example, `Get-Help about_Signing`.</span></span>

<span data-ttu-id="29b69-179">Seuls les articles conceptuels sur lesquels sont installés des fichiers d’aide sur votre ordinateur sont affichés.</span><span class="sxs-lookup"><span data-stu-id="29b69-179">Only the conceptual articles that have help files installed on your computer are displayed.</span></span> <span data-ttu-id="29b69-180">Pour plus d’informations sur le téléchargement et l’installation des fichiers d’aide dans PowerShell 3,0, consultez [Update-Help](Update-Help.md).</span><span class="sxs-lookup"><span data-stu-id="29b69-180">For information about downloading and installing help files in PowerShell 3.0, see [Update-Help](Update-Help.md).</span></span>

```powershell
Get-Help about_*
```

### <span data-ttu-id="29b69-181">Exemple 9 : Rechercher un mot dans l’aide sur les applets de commande</span><span class="sxs-lookup"><span data-stu-id="29b69-181">Example 9: Search for a word in cmdlet help</span></span>

<span data-ttu-id="29b69-182">Cet exemple montre comment rechercher un mot dans l’article d’aide d’une applet de commande.</span><span class="sxs-lookup"><span data-stu-id="29b69-182">This example shows how to search for a word in a cmdlet help article.</span></span>

```powershell
Get-Help Add-Member -Full | Out-String -Stream | Select-String -Pattern Clixml
```

```Output
the Export-Clixml cmdlet to save the instance of the object, including the additional members...
can use the Import-Clixml cmdlet to re-create the instance of the object from the information...
Export-Clixml
Import-Clixml
```

<span data-ttu-id="29b69-183">`Get-Help` utilise le paramètre **Full** pour obtenir des informations d’aide pour `Add-Member` .</span><span class="sxs-lookup"><span data-stu-id="29b69-183">`Get-Help` uses the **Full** parameter to get help information for `Add-Member`.</span></span> <span data-ttu-id="29b69-184">L’objet **MamlCommandHelpInfo** est envoyé vers le pipeline.</span><span class="sxs-lookup"><span data-stu-id="29b69-184">The **MamlCommandHelpInfo** object is sent down the pipeline.</span></span> <span data-ttu-id="29b69-185">`Out-String` utilise le paramètre **Stream** pour convertir l’objet en une chaîne.</span><span class="sxs-lookup"><span data-stu-id="29b69-185">`Out-String` uses the **Stream** parameter to convert the object into a string.</span></span> <span data-ttu-id="29b69-186">`Select-String` utilise le paramètre **pattern** pour rechercher **Clixml** dans la chaîne.</span><span class="sxs-lookup"><span data-stu-id="29b69-186">`Select-String` uses the **Pattern** parameter to search the string for **Clixml** .</span></span>

### <span data-ttu-id="29b69-187">Exemple 10 : afficher une liste d’articles incluant un mot</span><span class="sxs-lookup"><span data-stu-id="29b69-187">Example 10: Display a list of articles that include a word</span></span>

<span data-ttu-id="29b69-188">Cet exemple affiche une liste d’articles qui incluent le mot **Remoting** .</span><span class="sxs-lookup"><span data-stu-id="29b69-188">This example displays a list of articles that include the word **remoting** .</span></span>

<span data-ttu-id="29b69-189">Lorsque vous entrez un mot qui n’apparaît pas dans un titre d’article, `Get-Help` affiche la liste des articles qui contiennent ce mot.</span><span class="sxs-lookup"><span data-stu-id="29b69-189">When you enter a word that doesn't appear in any article title, `Get-Help` displays a list of articles that include that word.</span></span>

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

### <span data-ttu-id="29b69-190">Exemple 11 : afficher l’aide spécifique au fournisseur</span><span class="sxs-lookup"><span data-stu-id="29b69-190">Example 11: Display provider-specific help</span></span>

<span data-ttu-id="29b69-191">Cet exemple montre deux façons d’obtenir l’aide spécifique au fournisseur pour `Get-Item` .</span><span class="sxs-lookup"><span data-stu-id="29b69-191">This example shows two ways of getting the provider-specific help for `Get-Item`.</span></span> <span data-ttu-id="29b69-192">Ces commandes obtiennent de l’aide qui explique comment utiliser l' `Get-Item` applet de commande dans le nœud **DataCollection** du fournisseur de SQL Server PowerShell.</span><span class="sxs-lookup"><span data-stu-id="29b69-192">These commands get help that explains how to use the `Get-Item` cmdlet in the PowerShell SQL Server provider's **DataCollection** node.</span></span>

<span data-ttu-id="29b69-193">Le premier exemple utilise le `Get-Help` paramètre **path** pour spécifier le chemin d’accès du fournisseur SQL Server.</span><span class="sxs-lookup"><span data-stu-id="29b69-193">The first example uses the `Get-Help` **Path** parameter to specify the SQL Server provider's path.</span></span>
<span data-ttu-id="29b69-194">Étant donné que le chemin d’accès du fournisseur est spécifié, vous pouvez exécuter la commande à partir de n’importe quel emplacement de chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="29b69-194">Because the provider's path is specified, you can run the command from any path location.</span></span>

<span data-ttu-id="29b69-195">Le deuxième exemple utilise `Set-Location` pour naviguer jusqu’au chemin d’accès du fournisseur SQL Server.</span><span class="sxs-lookup"><span data-stu-id="29b69-195">The second example uses `Set-Location` to navigate to the SQL Server provider's path.</span></span> <span data-ttu-id="29b69-196">À partir de cet emplacement, le paramètre **path** n’est pas nécessaire pour `Get-Help` pour obtenir l’aide spécifique au fournisseur.</span><span class="sxs-lookup"><span data-stu-id="29b69-196">From that location, the **Path** parameter isn't needed for `Get-Help` to get the provider-specific help.</span></span>

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

### <span data-ttu-id="29b69-197">Exemple 12 : afficher l’aide d’un script</span><span class="sxs-lookup"><span data-stu-id="29b69-197">Example 12: Display help for a script</span></span>

<span data-ttu-id="29b69-198">Cet exemple obtient l’aide pour le `MyScript.ps1 script` .</span><span class="sxs-lookup"><span data-stu-id="29b69-198">This example gets help for the `MyScript.ps1 script`.</span></span> <span data-ttu-id="29b69-199">Pour plus d’informations sur la façon d’écrire de l’aide pour vos fonctions et scripts, consultez [about_Comment_Based_Help](./About/about_Comment_Based_Help.md).</span><span class="sxs-lookup"><span data-stu-id="29b69-199">For information about how to write help for your functions and scripts, see [about_Comment_Based_Help](./About/about_Comment_Based_Help.md).</span></span>

```powershell
Get-Help -Name C:\PS-Test\MyScript.ps1
```

## <span data-ttu-id="29b69-200">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="29b69-200">PARAMETERS</span></span>

### <span data-ttu-id="29b69-201">-Catégorie</span><span class="sxs-lookup"><span data-stu-id="29b69-201">-Category</span></span>

<span data-ttu-id="29b69-202">Affiche l'aide uniquement des éléments de la catégorie spécifiée et de leurs alias.</span><span class="sxs-lookup"><span data-stu-id="29b69-202">Displays help only for items in the specified category and their aliases.</span></span> <span data-ttu-id="29b69-203">Les articles conceptuels se trouvent dans la catégorie **HelpFile** .</span><span class="sxs-lookup"><span data-stu-id="29b69-203">Conceptual articles are in the **HelpFile** category.</span></span>

<span data-ttu-id="29b69-204">Les valeurs acceptables pour ce paramètre sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="29b69-204">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="29b69-205">Alias</span><span class="sxs-lookup"><span data-stu-id="29b69-205">Alias</span></span>
- <span data-ttu-id="29b69-206">Applet de commande</span><span class="sxs-lookup"><span data-stu-id="29b69-206">Cmdlet</span></span>
- <span data-ttu-id="29b69-207">Fournisseur</span><span class="sxs-lookup"><span data-stu-id="29b69-207">Provider</span></span>
- <span data-ttu-id="29b69-208">Général</span><span class="sxs-lookup"><span data-stu-id="29b69-208">General</span></span>
- <span data-ttu-id="29b69-209">Questions fréquentes (FAQ)</span><span class="sxs-lookup"><span data-stu-id="29b69-209">FAQ</span></span>
- <span data-ttu-id="29b69-210">Glossaire</span><span class="sxs-lookup"><span data-stu-id="29b69-210">Glossary</span></span>
- <span data-ttu-id="29b69-211">HelpFile</span><span class="sxs-lookup"><span data-stu-id="29b69-211">HelpFile</span></span>
- <span data-ttu-id="29b69-212">ScriptCommand</span><span class="sxs-lookup"><span data-stu-id="29b69-212">ScriptCommand</span></span>
- <span data-ttu-id="29b69-213">Fonction</span><span class="sxs-lookup"><span data-stu-id="29b69-213">Function</span></span>
- <span data-ttu-id="29b69-214">Filtrer</span><span class="sxs-lookup"><span data-stu-id="29b69-214">Filter</span></span>
- <span data-ttu-id="29b69-215">ExternalScript</span><span class="sxs-lookup"><span data-stu-id="29b69-215">ExternalScript</span></span>
- <span data-ttu-id="29b69-216">Tous</span><span class="sxs-lookup"><span data-stu-id="29b69-216">All</span></span>
- <span data-ttu-id="29b69-217">DefaultHelp</span><span class="sxs-lookup"><span data-stu-id="29b69-217">DefaultHelp</span></span>
- <span data-ttu-id="29b69-218">Workflow</span><span class="sxs-lookup"><span data-stu-id="29b69-218">Workflow</span></span>
- <span data-ttu-id="29b69-219">DscResource</span><span class="sxs-lookup"><span data-stu-id="29b69-219">DscResource</span></span>
- <span data-ttu-id="29b69-220">Classe</span><span class="sxs-lookup"><span data-stu-id="29b69-220">Class</span></span>
- <span data-ttu-id="29b69-221">Configuration</span><span class="sxs-lookup"><span data-stu-id="29b69-221">Configuration</span></span>

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

### <span data-ttu-id="29b69-222">-Composant</span><span class="sxs-lookup"><span data-stu-id="29b69-222">-Component</span></span>

<span data-ttu-id="29b69-223">Affiche les commandes avec la valeur de composant spécifiée, par exemple **Exchange** .</span><span class="sxs-lookup"><span data-stu-id="29b69-223">Displays commands with the specified component value, such as **Exchange** .</span></span> <span data-ttu-id="29b69-224">Entrez un nom de composant.</span><span class="sxs-lookup"><span data-stu-id="29b69-224">Enter a component name.</span></span>
<span data-ttu-id="29b69-225">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="29b69-225">Wildcard characters are permitted.</span></span> <span data-ttu-id="29b69-226">Ce paramètre n’a aucun effet sur les affichages de l’aide conceptuelle ( **about_** ).</span><span class="sxs-lookup"><span data-stu-id="29b69-226">This parameter has no effect on displays of conceptual ( **About_** ) help.</span></span>

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

### <span data-ttu-id="29b69-227">-Detailed</span><span class="sxs-lookup"><span data-stu-id="29b69-227">-Detailed</span></span>

<span data-ttu-id="29b69-228">Ajoute la description des paramètre et les exemples à l'affichage de l'aide de base.</span><span class="sxs-lookup"><span data-stu-id="29b69-228">Adds parameter descriptions and examples to the basic help display.</span></span> <span data-ttu-id="29b69-229">Ce paramètre est effectif uniquement lorsque les fichiers d’aide sont installés sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="29b69-229">This parameter is effective only when the help files are installed on the computer.</span></span> <span data-ttu-id="29b69-230">Elle n’a aucun effet sur les affichages de l’aide conceptuelle ( **about_** ).</span><span class="sxs-lookup"><span data-stu-id="29b69-230">It has no effect on displays of conceptual ( **About_** ) help.</span></span>

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

### <span data-ttu-id="29b69-231">-Examples</span><span class="sxs-lookup"><span data-stu-id="29b69-231">-Examples</span></span>

<span data-ttu-id="29b69-232">Affiche uniquement le nom, le résumé et les exemples.</span><span class="sxs-lookup"><span data-stu-id="29b69-232">Displays only the name, synopsis, and examples.</span></span> <span data-ttu-id="29b69-233">Pour afficher uniquement les exemples, tapez `(Get-Help \<cmdlet-name\>).Examples` .</span><span class="sxs-lookup"><span data-stu-id="29b69-233">To display only the examples, type `(Get-Help \<cmdlet-name\>).Examples`.</span></span>

<span data-ttu-id="29b69-234">Ce paramètre est effectif uniquement lorsque les fichiers d’aide sont installés sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="29b69-234">This parameter is effective only when the help files are installed on the computer.</span></span> <span data-ttu-id="29b69-235">Elle n’a aucun effet sur les affichages de l’aide conceptuelle ( **about_** ).</span><span class="sxs-lookup"><span data-stu-id="29b69-235">It has no effect on displays of conceptual ( **About_** ) help.</span></span>

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

### <span data-ttu-id="29b69-236">-Full</span><span class="sxs-lookup"><span data-stu-id="29b69-236">-Full</span></span>

<span data-ttu-id="29b69-237">Affiche la totalité de l’article d’aide pour une applet de commande.</span><span class="sxs-lookup"><span data-stu-id="29b69-237">Displays the entire help article for a cmdlet.</span></span> <span data-ttu-id="29b69-238">**Full** comprend des descriptions de paramètres et des attributs, des exemples, des types d’objet d’entrée et de sortie, ainsi que des remarques supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="29b69-238">**Full** includes parameter descriptions and attributes, examples, input and output object types, and additional notes.</span></span>

<span data-ttu-id="29b69-239">Ce paramètre est effectif uniquement lorsque les fichiers d’aide sont installés sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="29b69-239">This parameter is effective only when the help files are installed on the computer.</span></span> <span data-ttu-id="29b69-240">Elle n’a aucun effet sur les affichages de l’aide conceptuelle ( **about_** ).</span><span class="sxs-lookup"><span data-stu-id="29b69-240">It has no effect on displays of conceptual ( **About_** ) help.</span></span>

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

### <span data-ttu-id="29b69-241">-Fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="29b69-241">-Functionality</span></span>

<span data-ttu-id="29b69-242">Affiche l'aide pour des éléments ayant la fonctionnalité spécifiée.</span><span class="sxs-lookup"><span data-stu-id="29b69-242">Displays help for items with the specified functionality.</span></span> <span data-ttu-id="29b69-243">Entrez la fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="29b69-243">Enter the functionality.</span></span> <span data-ttu-id="29b69-244">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="29b69-244">Wildcard characters are permitted.</span></span> <span data-ttu-id="29b69-245">Ce paramètre n’a aucun effet sur les affichages de l’aide conceptuelle ( **about_** ).</span><span class="sxs-lookup"><span data-stu-id="29b69-245">This parameter has no effect on displays of conceptual ( **About_** ) help.</span></span>

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

### <span data-ttu-id="29b69-246">-Name</span><span class="sxs-lookup"><span data-stu-id="29b69-246">-Name</span></span>

<span data-ttu-id="29b69-247">Obtient de l'aide sur la commande ou le concept spécifié.</span><span class="sxs-lookup"><span data-stu-id="29b69-247">Gets help about the specified command or concept.</span></span> <span data-ttu-id="29b69-248">Entrez le nom d’une applet de commande, d’une fonction, d’un fournisseur, d’un script ou d’un flux de travail, tel que `Get-Member` , un nom d’article conceptuel, tel que `about_Objects` , ou un alias, tel que `ls` .</span><span class="sxs-lookup"><span data-stu-id="29b69-248">Enter the name of a cmdlet, function, provider, script, or workflow, such as `Get-Member`, a conceptual article name, such as `about_Objects`, or an alias, such as `ls`.</span></span> <span data-ttu-id="29b69-249">Les caractères génériques sont autorisés dans les noms d’applet de commande et de fournisseur, mais vous ne pouvez pas utiliser de caractères génériques pour rechercher les noms des articles d’aide de fonction et de script.</span><span class="sxs-lookup"><span data-stu-id="29b69-249">Wildcard characters are permitted in cmdlet and provider names, but you can't use wildcard characters to find the names of function help and script help articles.</span></span>

<span data-ttu-id="29b69-250">Pour obtenir de l’aide sur un script qui ne se trouve pas dans un chemin d’accès qui est listé dans la `$env:Path` variable d’environnement, tapez le chemin d’accès et le nom de fichier du script.</span><span class="sxs-lookup"><span data-stu-id="29b69-250">To get help for a script that isn't located in a path that's listed in the `$env:Path` environment variable, type the script's path and file name.</span></span>

<span data-ttu-id="29b69-251">Si vous entrez le nom exact d’un article d’aide, `Get-Help` affiche le contenu de l’article.</span><span class="sxs-lookup"><span data-stu-id="29b69-251">If you enter the exact name of a help article, `Get-Help` displays the article contents.</span></span>

<span data-ttu-id="29b69-252">Si vous entrez un mot ou un modèle de mot qui apparaît dans plusieurs titres d’articles d’aide, `Get-Help` affiche une liste des titres correspondants.</span><span class="sxs-lookup"><span data-stu-id="29b69-252">If you enter a word or word pattern that appears in several help article titles, `Get-Help` displays a list of the matching titles.</span></span>

<span data-ttu-id="29b69-253">Si vous entrez du texte qui ne correspond à aucun titre d’article d’aide, `Get-Help` affiche une liste d’articles incluant ce texte dans leur contenu.</span><span class="sxs-lookup"><span data-stu-id="29b69-253">If you enter any text that doesn't match any help article titles, `Get-Help` displays a list of articles that include that text in their contents.</span></span>

<span data-ttu-id="29b69-254">Les noms des articles conceptuels, tels que `about_Objects` , doivent être entrés en anglais, même dans les versions non anglaises de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="29b69-254">The names of conceptual articles, such as `about_Objects`, must be entered in English, even in non-English versions of PowerShell.</span></span>

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

### <span data-ttu-id="29b69-255">-En ligne</span><span class="sxs-lookup"><span data-stu-id="29b69-255">-Online</span></span>

<span data-ttu-id="29b69-256">Affiche la version en ligne d’un article d’aide dans le navigateur par défaut.</span><span class="sxs-lookup"><span data-stu-id="29b69-256">Displays the online version of a help article in the default browser.</span></span> <span data-ttu-id="29b69-257">Ce paramètre est valide uniquement pour les articles d’aide sur les applets de commande, les fonctions, les workflows et les scripts.</span><span class="sxs-lookup"><span data-stu-id="29b69-257">This parameter is valid only for cmdlet, function, workflow, and script help articles.</span></span> <span data-ttu-id="29b69-258">Vous ne pouvez pas utiliser le paramètre **Online** avec `Get-Help` dans une session à distance.</span><span class="sxs-lookup"><span data-stu-id="29b69-258">You can't use the **Online** parameter with `Get-Help` in a remote session.</span></span>

<span data-ttu-id="29b69-259">Pour plus d’informations sur la prise en charge de cette fonctionnalité dans les articles d’aide que vous écrivez, consultez [about_Comment_Based_Help](./About/about_Comment_Based_Help.md)et [prise en charge de l’aide en ligne](/powershell/scripting/developer/module/supporting-online-help)et [écriture d’aide pour les applets de commande PowerShell](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets).</span><span class="sxs-lookup"><span data-stu-id="29b69-259">For information about supporting this feature in help articles that you write, see [about_Comment_Based_Help](./About/about_Comment_Based_Help.md), and [Supporting Online Help](/powershell/scripting/developer/module/supporting-online-help), and [Writing Help for PowerShell Cmdlets](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets).</span></span>

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

### <span data-ttu-id="29b69-260">Paramètres </span><span class="sxs-lookup"><span data-stu-id="29b69-260">-Parameter</span></span>

<span data-ttu-id="29b69-261">Affiche uniquement les descriptions détaillées des paramètres spécifiés.</span><span class="sxs-lookup"><span data-stu-id="29b69-261">Displays only the detailed descriptions of the specified parameters.</span></span> <span data-ttu-id="29b69-262">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="29b69-262">Wildcards are permitted.</span></span> <span data-ttu-id="29b69-263">Ce paramètre n’a aucun effet sur les affichages de l’aide conceptuelle ( **about_** ).</span><span class="sxs-lookup"><span data-stu-id="29b69-263">This parameter has no effect on displays of conceptual ( **About_** ) help.</span></span>

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

### <span data-ttu-id="29b69-264">-Path</span><span class="sxs-lookup"><span data-stu-id="29b69-264">-Path</span></span>

<span data-ttu-id="29b69-265">Obtient l'aide qui explique le fonctionnement de l'applet de commande dans le chemin d'accès du fournisseur spécifié.</span><span class="sxs-lookup"><span data-stu-id="29b69-265">Gets help that explains how the cmdlet works in the specified provider path.</span></span> <span data-ttu-id="29b69-266">Entrez un chemin d’accès au fournisseur PowerShell.</span><span class="sxs-lookup"><span data-stu-id="29b69-266">Enter a PowerShell provider path.</span></span>

<span data-ttu-id="29b69-267">Ce paramètre obtient une version personnalisée d’un article d’aide sur les applets de commande qui explique le fonctionnement de l’applet de commande dans le chemin d’accès du fournisseur PowerShell spécifié.</span><span class="sxs-lookup"><span data-stu-id="29b69-267">This parameter gets a customized version of a cmdlet help article that explains how the cmdlet works in the specified PowerShell provider path.</span></span> <span data-ttu-id="29b69-268">Ce paramètre est effectif uniquement pour l’aide relative à une applet de commande de fournisseur et uniquement lorsque le fournisseur comprend une version personnalisée de l’article d’aide sur l’applet de commande du fournisseur dans son fichier d’aide.</span><span class="sxs-lookup"><span data-stu-id="29b69-268">This parameter is effective only for help about a provider cmdlet and only when the provider includes a custom version of the provider cmdlet help article in its help file.</span></span> <span data-ttu-id="29b69-269">Pour utiliser ce paramètre, installez le fichier d'aide du module qui inclut le fournisseur.</span><span class="sxs-lookup"><span data-stu-id="29b69-269">To use this parameter, install the help file for the module that includes the provider.</span></span>

<span data-ttu-id="29b69-270">Pour afficher l’aide de l’applet de commande personnalisée pour un chemin d’accès de fournisseur, accédez à l’emplacement du chemin d’accès du fournisseur et entrez une `Get-Help` commande ou, à partir d’un emplacement de chemin d’accès, utilisez le paramètre **path** de `Get-Help` pour spécifier le chemin d’accès du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="29b69-270">To see the custom cmdlet help for a provider path, go to the provider path location and enter a `Get-Help` command or, from any path location, use the **Path** parameter of `Get-Help` to specify the provider path.</span></span> <span data-ttu-id="29b69-271">Vous pouvez également trouver l’aide en ligne de l’applet de commande personnalisée dans la section d’aide du fournisseur des articles d’aide.</span><span class="sxs-lookup"><span data-stu-id="29b69-271">You can also find custom cmdlet help online in the provider help section of the help articles.</span></span>

<span data-ttu-id="29b69-272">Pour plus d’informations sur les fournisseurs PowerShell, consultez [about_Providers](./About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="29b69-272">For more information about PowerShell providers, see [about_Providers](./About/about_Providers.md).</span></span>

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

### <span data-ttu-id="29b69-273">-Rôle</span><span class="sxs-lookup"><span data-stu-id="29b69-273">-Role</span></span>

<span data-ttu-id="29b69-274">Affiche l'aide personnalisée du rôle d'utilisateur spécifié.</span><span class="sxs-lookup"><span data-stu-id="29b69-274">Displays help customized for the specified user role.</span></span> <span data-ttu-id="29b69-275">Entrez un rôle.</span><span class="sxs-lookup"><span data-stu-id="29b69-275">Enter a role.</span></span> <span data-ttu-id="29b69-276">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="29b69-276">Wildcard characters are permitted.</span></span>

<span data-ttu-id="29b69-277">Entrez le rôle joué par l'utilisateur dans une organisation.</span><span class="sxs-lookup"><span data-stu-id="29b69-277">Enter the role that the user plays in an organization.</span></span> <span data-ttu-id="29b69-278">Certaines applets de commande affichent du texte différent dans leurs fichiers d'aide en fonction de la valeur de ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="29b69-278">Some cmdlets display different text in their help files based on the value of this parameter.</span></span> <span data-ttu-id="29b69-279">Ce paramètre n'a aucun effet sur l'aide des applets de commande de base.</span><span class="sxs-lookup"><span data-stu-id="29b69-279">This parameter has no effect on help for the core cmdlets.</span></span>

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

### <span data-ttu-id="29b69-280">-ShowWindow</span><span class="sxs-lookup"><span data-stu-id="29b69-280">-ShowWindow</span></span>

<span data-ttu-id="29b69-281">Affiche la rubrique d'aide dans une fenêtre pour faciliter la lecture.</span><span class="sxs-lookup"><span data-stu-id="29b69-281">Displays the help topic in a window for easier reading.</span></span> <span data-ttu-id="29b69-282">La fenêtre inclut une fonctionnalité **de recherche de recherche et** une zone de **paramètres** qui vous permettent de définir des options pour l’affichage, y compris des options permettant d’afficher uniquement les sections sélectionnées d’une rubrique d’aide.</span><span class="sxs-lookup"><span data-stu-id="29b69-282">The window includes a **Find** search feature and a **Settings** box that lets you set options for the display, including options to display only selected sections of a help topic.</span></span>

<span data-ttu-id="29b69-283">Le paramètre **ShowWindow** prend en charge les rubriques d’aide pour les commandes (applets de commande, fonctions, commandes CIM, scripts) et **les articles** conceptuels.</span><span class="sxs-lookup"><span data-stu-id="29b69-283">The **ShowWindow** parameter supports help topics for commands (cmdlets, functions, CIM commands, scripts) and conceptual **About** articles.</span></span> <span data-ttu-id="29b69-284">Il ne gère pas l'aide du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="29b69-284">It does not support provider help.</span></span>

<span data-ttu-id="29b69-285">Ce paramètre a été réintroduit dans PowerShell 7,0.</span><span class="sxs-lookup"><span data-stu-id="29b69-285">This parameter was reintroduced in PowerShell 7.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ShowWindow
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="29b69-286">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="29b69-286">CommonParameters</span></span>

<span data-ttu-id="29b69-287">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="29b69-287">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="29b69-288">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="29b69-288">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="29b69-289">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="29b69-289">INPUTS</span></span>

### <span data-ttu-id="29b69-290">Aucun</span><span class="sxs-lookup"><span data-stu-id="29b69-290">None</span></span>

<span data-ttu-id="29b69-291">Vous ne pouvez pas envoyer d’objets dans le pipeline vers `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="29b69-291">You can't send objects down the pipeline to `Get-Help`.</span></span>

## <span data-ttu-id="29b69-292">SORTIES</span><span class="sxs-lookup"><span data-stu-id="29b69-292">OUTPUTS</span></span>

### <span data-ttu-id="29b69-293">ExtendedCmdletHelpInfo</span><span class="sxs-lookup"><span data-stu-id="29b69-293">ExtendedCmdletHelpInfo</span></span>

<span data-ttu-id="29b69-294">Si vous exécutez `Get-Help` sur une commande qui n’a pas de fichier d’aide, `Get-Help` retourne un objet **ExtendedCmdletHelpInfo** qui représente l’aide générée automatiquement.</span><span class="sxs-lookup"><span data-stu-id="29b69-294">If you run `Get-Help` on a command that doesn't have a help file, `Get-Help` returns an **ExtendedCmdletHelpInfo** object that represents autogenerated help.</span></span>

### <span data-ttu-id="29b69-295">System.String</span><span class="sxs-lookup"><span data-stu-id="29b69-295">System.String</span></span>

<span data-ttu-id="29b69-296">Si vous recevez un article d’aide conceptuelle, `Get-Help` le retourne sous forme de chaîne.</span><span class="sxs-lookup"><span data-stu-id="29b69-296">If you get a conceptual help article, `Get-Help` returns it as a string.</span></span>

### <span data-ttu-id="29b69-297">MamlCommandHelpInfo</span><span class="sxs-lookup"><span data-stu-id="29b69-297">MamlCommandHelpInfo</span></span>

<span data-ttu-id="29b69-298">Si vous recevez une commande qui contient un fichier d’aide, `Get-Help` retourne un objet **MamlCommandHelpInfo** .</span><span class="sxs-lookup"><span data-stu-id="29b69-298">If you get a command that has a help file, `Get-Help` returns a **MamlCommandHelpInfo** object.</span></span>

## <span data-ttu-id="29b69-299">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="29b69-299">NOTES</span></span>

<span data-ttu-id="29b69-300">PowerShell 3,0 n’inclut pas les fichiers d’aide.</span><span class="sxs-lookup"><span data-stu-id="29b69-300">PowerShell 3.0 doesn't include help files.</span></span> <span data-ttu-id="29b69-301">Pour télécharger et installer les fichiers d’aide que `Get-Help` lit, utilisez l’applet de commande `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="29b69-301">To download and install the help files that `Get-Help` reads, use the `Update-Help` cmdlet.</span></span> <span data-ttu-id="29b69-302">Vous pouvez utiliser l' `Update-Help` applet de commande pour télécharger et installer les fichiers d’aide pour les commandes de base fournies avec PowerShell et pour tous les modules que vous installez.</span><span class="sxs-lookup"><span data-stu-id="29b69-302">You can use the `Update-Help` cmdlet to download and install help files for the core commands that come with PowerShell and for any modules that you install.</span></span> <span data-ttu-id="29b69-303">Vous pouvez également l'utiliser pour mettre à jour les fichiers d'aide afin que l'aide sur votre ordinateur ne soit jamais obsolète.</span><span class="sxs-lookup"><span data-stu-id="29b69-303">You can also use it to update the help files so that the help on your computer is never outdated.</span></span>

<span data-ttu-id="29b69-304">Vous pouvez également lire les articles d’aide sur les commandes fournies avec PowerShell Online à partir de [prise en main avec Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="29b69-304">You can also read the help articles about the commands that come with PowerShell online starting at [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

<span data-ttu-id="29b69-305">`Get-Help` affiche l’aide dans l’ensemble de paramètres régionaux pour le système d’exploitation Windows ou dans la langue de secours pour ces paramètres régionaux.</span><span class="sxs-lookup"><span data-stu-id="29b69-305">`Get-Help` displays help in the locale set for the Windows operating system or in the fallback language for that locale.</span></span> <span data-ttu-id="29b69-306">Si vous n’avez pas de fichiers d’aide pour les paramètres régionaux principaux ou de secours, `Get-Help` se comporte comme s’il n’y avait pas de fichiers d’aide sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="29b69-306">If you don't have help files for the primary or fallback locale, `Get-Help` behaves as if there are no help files on the computer.</span></span> <span data-ttu-id="29b69-307">Pour obtenir de l’aide pour des paramètres régionaux différents, utilisez **région** et **langue** dans le panneau de configuration pour modifier les paramètres.</span><span class="sxs-lookup"><span data-stu-id="29b69-307">To get help for a different locale, use **Region** and **Language** in Control Panel to change the settings.</span></span> <span data-ttu-id="29b69-308">Sur Windows 10, **paramètres** , **heure & langue** .</span><span class="sxs-lookup"><span data-stu-id="29b69-308">On Windows 10, **Settings** , **Time & Language** .</span></span>

<span data-ttu-id="29b69-309">La vue complète de l’aide comprend une table d’informations sur les paramètres.</span><span class="sxs-lookup"><span data-stu-id="29b69-309">The full view of help includes a table of information about the parameters.</span></span> <span data-ttu-id="29b69-310">La table inclut les champs suivants :</span><span class="sxs-lookup"><span data-stu-id="29b69-310">The table includes the following fields:</span></span>

- <span data-ttu-id="29b69-311">**Requis** .</span><span class="sxs-lookup"><span data-stu-id="29b69-311">**Required** .</span></span> <span data-ttu-id="29b69-312">indique si le paramètre est obligatoire (true) ou facultatif (false).</span><span class="sxs-lookup"><span data-stu-id="29b69-312">Indicates whether the parameter is required (true) or optional (false).</span></span>

- <span data-ttu-id="29b69-313">**Position** .</span><span class="sxs-lookup"><span data-stu-id="29b69-313">**Position** .</span></span> <span data-ttu-id="29b69-314">Indique si le paramètre est nommé ou positionnel (numérique).</span><span class="sxs-lookup"><span data-stu-id="29b69-314">Indicates whether the parameter is named or positional (numeric).</span></span> <span data-ttu-id="29b69-315">les paramètres positionnels doivent apparaître à un emplacement spécifié de la commande.</span><span class="sxs-lookup"><span data-stu-id="29b69-315">Positional parameters must appear in a specified place in the command.</span></span>

- <span data-ttu-id="29b69-316">**Nommé** indique que le nom du paramètre est obligatoire, mais que le paramètre peut apparaître n’importe où dans la commande.</span><span class="sxs-lookup"><span data-stu-id="29b69-316">**Named** indicates that the parameter name is required, but that the parameter can appear anywhere in the command.</span></span>

- <span data-ttu-id="29b69-317">**Numeric** indique que le nom du paramètre est facultatif, mais lorsque le nom est omis, le paramètre doit se trouver à l’emplacement spécifié par le nombre.</span><span class="sxs-lookup"><span data-stu-id="29b69-317">**Numeric** indicates that the parameter name is optional, but when the name is omitted, the parameter must be in the place specified by the number.</span></span> <span data-ttu-id="29b69-318">Par exemple, `2` indique que lorsque le nom du paramètre est omis, le paramètre doit être le deuxième ou le seul paramètre sans nom dans la commande.</span><span class="sxs-lookup"><span data-stu-id="29b69-318">For example, `2` indicates that when the parameter name is omitted, the parameter must be the second or only unnamed parameter in the command.</span></span> <span data-ttu-id="29b69-319">Quand le nom du paramètre est utilisé, le paramètre peut apparaître n'importe où dans la commande.</span><span class="sxs-lookup"><span data-stu-id="29b69-319">When the parameter name is used, the parameter can appear anywhere in the command.</span></span>

- <span data-ttu-id="29b69-320">**Valeur par défaut** .</span><span class="sxs-lookup"><span data-stu-id="29b69-320">**Default value** .</span></span> <span data-ttu-id="29b69-321">La valeur du paramètre ou le comportement par défaut que PowerShell utilise si vous n’incluez pas le paramètre dans la commande.</span><span class="sxs-lookup"><span data-stu-id="29b69-321">The parameter value or default behavior that PowerShell uses if you don't include the parameter in the command.</span></span>

- <span data-ttu-id="29b69-322">Accepte l’entrée de pipeline.</span><span class="sxs-lookup"><span data-stu-id="29b69-322">Accepts pipeline input.</span></span> <span data-ttu-id="29b69-323">Indique si vous pouvez (true) ou ne pouvez pas (false) envoyer des objets au paramètre via un pipeline.</span><span class="sxs-lookup"><span data-stu-id="29b69-323">Indicates whether you can (true) or can't (false) send objects to the parameter through a pipeline.</span></span> <span data-ttu-id="29b69-324">**Par nom de propriété** signifie que l’objet en pipeline doit avoir une propriété qui porte le même nom que le nom du paramètre.</span><span class="sxs-lookup"><span data-stu-id="29b69-324">**By Property Name** means that the pipelined object must have a property that has the same name as the parameter name.</span></span>

- <span data-ttu-id="29b69-325">**Accepte les caractères génériques** .</span><span class="sxs-lookup"><span data-stu-id="29b69-325">**Accepts wildcard characters** .</span></span> <span data-ttu-id="29b69-326">Indique si la valeur d’un paramètre peut inclure des caractères génériques, tels qu’un astérisque () ou un point d' `*` interrogation ( `?` ).</span><span class="sxs-lookup"><span data-stu-id="29b69-326">Indicates whether the value of a parameter can include wildcard characters, such as an asterisk (`*`) or question mark (`?`).</span></span>

## <span data-ttu-id="29b69-327">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="29b69-327">RELATED LINKS</span></span>

[<span data-ttu-id="29b69-328">about_Command_Syntax</span><span class="sxs-lookup"><span data-stu-id="29b69-328">about_Command_Syntax</span></span>](About/about_Command_Syntax.md)

[<span data-ttu-id="29b69-329">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="29b69-329">about_Comment_Based_Help</span></span>](./About/about_Comment_Based_Help.md)

[<span data-ttu-id="29b69-330">Get-Command</span><span class="sxs-lookup"><span data-stu-id="29b69-330">Get-Command</span></span>](Get-Command.md)

[<span data-ttu-id="29b69-331">Prise en charge de l’aide actualisable</span><span class="sxs-lookup"><span data-stu-id="29b69-331">Supporting Updatable Help</span></span>](/powershell/scripting/developer/module/supporting-updatable-help)

[<span data-ttu-id="29b69-332">Update-Help</span><span class="sxs-lookup"><span data-stu-id="29b69-332">Update-Help</span></span>](Update-Help.md)

[<span data-ttu-id="29b69-333">Écriture de rubriques d’aide basée sur les commentaires</span><span class="sxs-lookup"><span data-stu-id="29b69-333">Writing Comment-Based Help Topics</span></span>](/powershell/scripting/developer/help/writing-comment-based-help-topics)

[<span data-ttu-id="29b69-334">Écriture d’une aide pour les applets de commande PowerShell</span><span class="sxs-lookup"><span data-stu-id="29b69-334">Writing Help for PowerShell Cmdlets</span></span>](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets)

