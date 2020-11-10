---
description: Décrit comment écrire des rubriques d’aide basées sur des commentaires pour des fonctions et des scripts.
keywords: powershell,applet de commande
ms.date: 06/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_comment_based_help?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Comment_Based_Help
ms.openlocfilehash: c3e02edd6ca33f373b1632160e4a18dc4fb744f2
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94386969"
---
# <a name="about-comment-based-help"></a><span data-ttu-id="0ab62-104">À propos de l’aide basée sur les commentaires</span><span class="sxs-lookup"><span data-stu-id="0ab62-104">About Comment-based Help</span></span>

## <a name="short-description"></a><span data-ttu-id="0ab62-105">Description courte</span><span class="sxs-lookup"><span data-stu-id="0ab62-105">Short description</span></span>
<span data-ttu-id="0ab62-106">Décrit comment écrire des rubriques d’aide basées sur des commentaires pour des fonctions et des scripts.</span><span class="sxs-lookup"><span data-stu-id="0ab62-106">Describes how to write comment-based help topics for functions and scripts.</span></span>

## <a name="long-description"></a><span data-ttu-id="0ab62-107">Description longue</span><span class="sxs-lookup"><span data-stu-id="0ab62-107">Long description</span></span>

<span data-ttu-id="0ab62-108">Vous pouvez écrire des rubriques d’aide basées sur des commentaires pour les fonctions et les scripts en utilisant des mots clés de commentaires d’aide spéciaux.</span><span class="sxs-lookup"><span data-stu-id="0ab62-108">You can write comment-based help topics for functions and scripts by using special help comment keywords.</span></span>

<span data-ttu-id="0ab62-109">L’applet de commande [obtenir-Help](xref:Microsoft.PowerShell.Core.Get-Help) affiche une aide basée sur des commentaires dans le même format que celui dans lequel elle affiche les rubriques d’aide sur les applets de commande générées à partir de fichiers XML.</span><span class="sxs-lookup"><span data-stu-id="0ab62-109">The [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) cmdlet displays comment-based help in the same format in which it displays the cmdlet help topics that are generated from XML files.</span></span> <span data-ttu-id="0ab62-110">Les utilisateurs peuvent utiliser tous les paramètres de `Get-Help` , tels que **detailed** , **Full** , **examples** et **Online** , pour afficher le contenu de l’aide basée sur les commentaires.</span><span class="sxs-lookup"><span data-stu-id="0ab62-110">Users can use all of the parameters of `Get-Help`, such as **Detailed** , **Full** , **Examples** , and **Online** , to display the contents of comment-based help.</span></span>

<span data-ttu-id="0ab62-111">Vous pouvez également écrire des fichiers d’aide XML pour des fonctions et des scripts.</span><span class="sxs-lookup"><span data-stu-id="0ab62-111">You can also write XML-based help files for functions and scripts.</span></span> <span data-ttu-id="0ab62-112">Pour permettre `Get-Help` à l’applet de commande de trouver le fichier d’aide XML pour une fonction ou un script, utilisez le `.ExternalHelp` mot clé.</span><span class="sxs-lookup"><span data-stu-id="0ab62-112">To enable the `Get-Help` cmdlet to find the XML-based help file for a function or script, use the `.ExternalHelp` keyword.</span></span> <span data-ttu-id="0ab62-113">Sans ce mot clé, `Get-Help` les rubriques d’aide XML pour les fonctions ou les scripts ne sont pas disponibles.</span><span class="sxs-lookup"><span data-stu-id="0ab62-113">Without this keyword, `Get-Help` cannot find XML-based help topics for functions or scripts.</span></span>

<span data-ttu-id="0ab62-114">Cette rubrique explique comment écrire des rubriques d’aide pour les fonctions et les scripts.</span><span class="sxs-lookup"><span data-stu-id="0ab62-114">This topic explains how to write help topics for functions and scripts.</span></span> <span data-ttu-id="0ab62-115">Pour plus d’informations sur l’affichage des rubriques d’aide relatives aux fonctions et aux scripts, consultez [obtenir-aide](xref:Microsoft.PowerShell.Core.Get-Help).</span><span class="sxs-lookup"><span data-stu-id="0ab62-115">For information about how to display help topics for functions and scripts, see [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help).</span></span>

<span data-ttu-id="0ab62-116">Les applets de commande [Update-Help](xref:Microsoft.PowerShell.Core.Update-Help) et [Save-Help](xref:Microsoft.PowerShell.Core.Save-Help) fonctionnent uniquement sur les fichiers XML.</span><span class="sxs-lookup"><span data-stu-id="0ab62-116">The [Update-Help](xref:Microsoft.PowerShell.Core.Update-Help) and [Save-Help](xref:Microsoft.PowerShell.Core.Save-Help) cmdlets work only on XML files.</span></span> <span data-ttu-id="0ab62-117">L’aide actualisable ne prend pas en charge les rubriques d’aide basées sur les commentaires.</span><span class="sxs-lookup"><span data-stu-id="0ab62-117">Updatable Help does not support comment-based help topics.</span></span>

## <a name="syntax-for-comment-based-help"></a><span data-ttu-id="0ab62-118">Syntaxe pour l’aide basée sur des commentaires</span><span class="sxs-lookup"><span data-stu-id="0ab62-118">Syntax for comment-based help</span></span>

<span data-ttu-id="0ab62-119">La syntaxe de l’aide basée sur les commentaires est la suivante :</span><span class="sxs-lookup"><span data-stu-id="0ab62-119">The syntax for comment-based help is as follows:</span></span>

```
# .<help keyword>
# <help content>
```

<span data-ttu-id="0ab62-120">ou</span><span class="sxs-lookup"><span data-stu-id="0ab62-120">or</span></span>

```
<#
.<help keyword>
<help content>
#>
```

<span data-ttu-id="0ab62-121">L’aide basée sur les commentaires est écrite sous la forme d’une série de commentaires.</span><span class="sxs-lookup"><span data-stu-id="0ab62-121">Comment-based help is written as a series of comments.</span></span> <span data-ttu-id="0ab62-122">Vous pouvez taper un symbole de commentaire `#` avant chaque ligne de commentaires, ou vous pouvez utiliser `<#` les `#>` symboles et pour créer un bloc de commentaires.</span><span class="sxs-lookup"><span data-stu-id="0ab62-122">You can type a comment symbol `#` before each line of comments, or you can use the `<#` and `#>` symbols to create a comment block.</span></span> <span data-ttu-id="0ab62-123">Toutes les lignes dans le bloc de commentaires sont interprétées comme des commentaires.</span><span class="sxs-lookup"><span data-stu-id="0ab62-123">All the lines within the comment block are interpreted as comments.</span></span>

<span data-ttu-id="0ab62-124">Toutes les lignes d’une rubrique d’aide basée sur des commentaires doivent être contiguës.</span><span class="sxs-lookup"><span data-stu-id="0ab62-124">All of the lines in a comment-based help topic must be contiguous.</span></span> <span data-ttu-id="0ab62-125">Si une rubrique d’aide basée sur des commentaires suit un commentaire qui ne fait pas partie de la rubrique d’aide, il doit y avoir au moins une ligne vide entre la dernière ligne de commentaire non-aide et le début de l’aide basée sur les commentaires.</span><span class="sxs-lookup"><span data-stu-id="0ab62-125">If a comment-based help topic follows a comment that is not part of the help topic, there must be at least one blank line between the last non-help comment line and the beginning of the comment-based help.</span></span>

<span data-ttu-id="0ab62-126">Les mots clés définissent chaque section de l’aide basée sur des commentaires.</span><span class="sxs-lookup"><span data-stu-id="0ab62-126">Keywords define each section of comment-based help.</span></span> <span data-ttu-id="0ab62-127">Chaque mot clé d’aide basé sur des commentaires est précédé d’un point `.` .</span><span class="sxs-lookup"><span data-stu-id="0ab62-127">Each comment-based help keyword is preceded by a dot `.`.</span></span> <span data-ttu-id="0ab62-128">Les mots clés peuvent apparaître dans n’importe quel ordre.</span><span class="sxs-lookup"><span data-stu-id="0ab62-128">The keywords can appear in any order.</span></span> <span data-ttu-id="0ab62-129">Les noms de mots clés ne respectent pas la casse.</span><span class="sxs-lookup"><span data-stu-id="0ab62-129">The keyword names are not case-sensitive.</span></span>

<span data-ttu-id="0ab62-130">Par exemple, le `.Description` mot clé précède une description d’une fonction ou d’un script.</span><span class="sxs-lookup"><span data-stu-id="0ab62-130">For example, the `.Description` keyword precedes a description of a function or script.</span></span>

```
<#
.Description
Get-Function displays the name and syntax of all functions in the session.
#>
```

<span data-ttu-id="0ab62-131">Le bloc de commentaires doit contenir au moins un mot clé.</span><span class="sxs-lookup"><span data-stu-id="0ab62-131">The comment block must contain at least one keyword.</span></span> <span data-ttu-id="0ab62-132">Certains mots clés, tels que `.EXAMPLE` , peuvent apparaître plusieurs fois dans le même bloc de commentaires.</span><span class="sxs-lookup"><span data-stu-id="0ab62-132">Some of the keywords, such as `.EXAMPLE`, can appear many times in the same comment block.</span></span> <span data-ttu-id="0ab62-133">Le contenu de l’aide pour chaque mot clé commence sur la ligne qui suit le mot clé et peut s’étendre sur plusieurs lignes.</span><span class="sxs-lookup"><span data-stu-id="0ab62-133">The help content for each keyword begins on the line after the keyword and can span multiple lines.</span></span>

## <a name="syntax-for-comment-based-help-in-functions"></a><span data-ttu-id="0ab62-134">Syntaxe pour l’aide basée sur les commentaires dans les fonctions</span><span class="sxs-lookup"><span data-stu-id="0ab62-134">Syntax for comment-based help in functions</span></span>

<span data-ttu-id="0ab62-135">L’aide basée sur les commentaires pour une fonction peut apparaître dans l’un des trois emplacements suivants :</span><span class="sxs-lookup"><span data-stu-id="0ab62-135">Comment-based help for a function can appear in one of three locations:</span></span>

- <span data-ttu-id="0ab62-136">Au début du corps de la fonction.</span><span class="sxs-lookup"><span data-stu-id="0ab62-136">At the beginning of the function body.</span></span>
- <span data-ttu-id="0ab62-137">À la fin du corps de la fonction.</span><span class="sxs-lookup"><span data-stu-id="0ab62-137">At the end of the function body.</span></span>
- <span data-ttu-id="0ab62-138">Avant le `function` mot clé.</span><span class="sxs-lookup"><span data-stu-id="0ab62-138">Before the `function` keyword.</span></span> <span data-ttu-id="0ab62-139">Il ne peut pas y avoir plus d’une ligne vide entre la dernière ligne de l’aide de la fonction et le `function` mot clé.</span><span class="sxs-lookup"><span data-stu-id="0ab62-139">There cannot be more than one blank line between the last line of the function help and the `function` keyword.</span></span>

<span data-ttu-id="0ab62-140">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="0ab62-140">For example:</span></span>

```powershell
function Get-Function
{
<#
.<help keyword>
<help content>
#>

  # function logic
}
```

<span data-ttu-id="0ab62-141">or</span><span class="sxs-lookup"><span data-stu-id="0ab62-141">or</span></span>

```powershell
function Get-Function
{
   # function logic

<#
.<help keyword>
<help content>
#>
}
```

<span data-ttu-id="0ab62-142">or</span><span class="sxs-lookup"><span data-stu-id="0ab62-142">or</span></span>

```powershell
<#
.<help keyword>
<help content>
#>
function Get-Function { }
```

## <a name="syntax-for-comment-based-help-in-scripts"></a><span data-ttu-id="0ab62-143">Syntaxe pour l’aide basée sur les commentaires dans les scripts</span><span class="sxs-lookup"><span data-stu-id="0ab62-143">Syntax for comment-based help in scripts</span></span>

<span data-ttu-id="0ab62-144">L’aide sur les commentaires d’un script peut apparaître dans l’un des deux emplacements suivants du script.</span><span class="sxs-lookup"><span data-stu-id="0ab62-144">Comment-based help for a script can appear in one of the following two locations in the script.</span></span>

- <span data-ttu-id="0ab62-145">Au début du fichier de script.</span><span class="sxs-lookup"><span data-stu-id="0ab62-145">At the beginning of the script file.</span></span> <span data-ttu-id="0ab62-146">L’aide sur les scripts peut être précédée du script uniquement par des commentaires et des lignes vides.</span><span class="sxs-lookup"><span data-stu-id="0ab62-146">Script help can be preceded in the script only by comments and blank lines.</span></span>

  <span data-ttu-id="0ab62-147">Si le premier élément du corps du script (après l’aide) est une déclaration de fonction, il doit y avoir au moins deux lignes vides entre la fin de l’aide du script et la déclaration de la fonction.</span><span class="sxs-lookup"><span data-stu-id="0ab62-147">If the first item in the script body (after the help) is a function declaration, there must be at least two blank lines between the end of the script help and the function declaration.</span></span> <span data-ttu-id="0ab62-148">Dans le cas contraire, l’aide est interprétée comme une aide pour la fonction, et non pour l’aide du script.</span><span class="sxs-lookup"><span data-stu-id="0ab62-148">Otherwise, the help is interpreted as being help for the function, not help for the script.</span></span>

- <span data-ttu-id="0ab62-149">À la fin du fichier de script.</span><span class="sxs-lookup"><span data-stu-id="0ab62-149">At the end of the script file.</span></span> <span data-ttu-id="0ab62-150">Toutefois, si le script est signé, placez l’aide basée sur les commentaires au début du fichier de script.</span><span class="sxs-lookup"><span data-stu-id="0ab62-150">However, if the script is signed, place Comment-based help at the beginning of the script file.</span></span> <span data-ttu-id="0ab62-151">La fin du script est occupée par le bloc de signature.</span><span class="sxs-lookup"><span data-stu-id="0ab62-151">The end of the script is occupied by the signature block.</span></span>

<span data-ttu-id="0ab62-152">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="0ab62-152">For example:</span></span>

```powershell
<#
.<help keyword>
<help content>
#>


function Get-Function { }
```

<span data-ttu-id="0ab62-153">or</span><span class="sxs-lookup"><span data-stu-id="0ab62-153">or</span></span>

```powershell
function Get-Function { }

<#
.<help keyword>
<help content>
#>
```

## <a name="syntax-for-comment-based-help-in-script-modules"></a><span data-ttu-id="0ab62-154">Syntaxe pour l’aide basée sur les commentaires dans les modules de script</span><span class="sxs-lookup"><span data-stu-id="0ab62-154">Syntax for comment-based help in script modules</span></span>

<span data-ttu-id="0ab62-155">Dans un module de script `.psm1` , l’aide basée sur les commentaires utilise la syntaxe pour les fonctions, et non la syntaxe pour les scripts.</span><span class="sxs-lookup"><span data-stu-id="0ab62-155">In a script module `.psm1`, comment-based help uses the syntax for functions, not the syntax for scripts.</span></span> <span data-ttu-id="0ab62-156">Vous ne pouvez pas utiliser la syntaxe de script pour fournir de l’aide pour toutes les fonctions définies dans un module de script.</span><span class="sxs-lookup"><span data-stu-id="0ab62-156">You cannot use the script syntax to provide help for all functions defined in a script module.</span></span>

<span data-ttu-id="0ab62-157">Par exemple, si vous utilisez le `.ExternalHelp` mot clé pour identifier les fichiers d’aide XML pour les fonctions dans un module de script, vous devez ajouter un `.ExternalHelp` Commentaire à chaque fonction.</span><span class="sxs-lookup"><span data-stu-id="0ab62-157">For example, if you are using the `.ExternalHelp` keyword to identify the XML-based help files for the functions in a script module, you must add an `.ExternalHelp` comment to each function.</span></span>

```powershell
# .ExternalHelp <XML-file-name>
function <function-name>
{
  ...
}
```

## <a name="comment-based-help-keywords"></a><span data-ttu-id="0ab62-158">Mots clés d’aide basés sur des commentaires</span><span class="sxs-lookup"><span data-stu-id="0ab62-158">Comment-based help keywords</span></span>

<span data-ttu-id="0ab62-159">Les éléments suivants sont des mots clés d’aide basés sur des commentaires valides.</span><span class="sxs-lookup"><span data-stu-id="0ab62-159">The following are valid comment-based help keywords.</span></span> <span data-ttu-id="0ab62-160">Ils sont répertoriés dans l’ordre dans lequel ils apparaissent généralement dans une rubrique d’aide, ainsi que l’utilisation prévue.</span><span class="sxs-lookup"><span data-stu-id="0ab62-160">They are listed in the order in which they typically appear in a help topic along with their intended use.</span></span> <span data-ttu-id="0ab62-161">Ces mots clés peuvent apparaître dans n’importe quel ordre dans l’aide basée sur les commentaires, et ils ne respectent pas la casse.</span><span class="sxs-lookup"><span data-stu-id="0ab62-161">These keywords can appear in any order in the comment-based help, and they are not case-sensitive.</span></span>

### <a name="synopsis"></a><span data-ttu-id="0ab62-162">. SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="0ab62-162">.SYNOPSIS</span></span>

<span data-ttu-id="0ab62-163">Brève description de la fonction ou du script.</span><span class="sxs-lookup"><span data-stu-id="0ab62-163">A brief description of the function or script.</span></span> <span data-ttu-id="0ab62-164">Ce mot clé ne peut être utilisé qu’une seule fois dans chaque rubrique.</span><span class="sxs-lookup"><span data-stu-id="0ab62-164">This keyword can be used only once in each topic.</span></span>

### <a name="description"></a><span data-ttu-id="0ab62-165">. DESCRIPTIVE</span><span class="sxs-lookup"><span data-stu-id="0ab62-165">.DESCRIPTION</span></span>

<span data-ttu-id="0ab62-166">Description détaillée de la fonction ou du script.</span><span class="sxs-lookup"><span data-stu-id="0ab62-166">A detailed description of the function or script.</span></span> <span data-ttu-id="0ab62-167">Ce mot clé ne peut être utilisé qu’une seule fois dans chaque rubrique.</span><span class="sxs-lookup"><span data-stu-id="0ab62-167">This keyword can be used only once in each topic.</span></span>

### <a name="parameter"></a><span data-ttu-id="0ab62-168">. PARAMÈTRE</span><span class="sxs-lookup"><span data-stu-id="0ab62-168">.PARAMETER</span></span>

<span data-ttu-id="0ab62-169">Description d’un paramètre.</span><span class="sxs-lookup"><span data-stu-id="0ab62-169">The description of a parameter.</span></span> <span data-ttu-id="0ab62-170">Ajoutez un `.PARAMETER` mot clé pour chaque paramètre dans la syntaxe de la fonction ou du script.</span><span class="sxs-lookup"><span data-stu-id="0ab62-170">Add a `.PARAMETER` keyword for each parameter in the function or script syntax.</span></span>

<span data-ttu-id="0ab62-171">Tapez le nom du paramètre sur la même ligne que le `.PARAMETER` mot clé.</span><span class="sxs-lookup"><span data-stu-id="0ab62-171">Type the parameter name on the same line as the `.PARAMETER` keyword.</span></span> <span data-ttu-id="0ab62-172">Tapez la description du paramètre sur les lignes qui suivent le `.PARAMETER` mot clé.</span><span class="sxs-lookup"><span data-stu-id="0ab62-172">Type the parameter description on the lines following the `.PARAMETER` keyword.</span></span> <span data-ttu-id="0ab62-173">Windows PowerShell interprète tout le texte entre la `.PARAMETER` ligne et le mot clé suivant ou la fin du bloc de commentaires dans le cadre de la description du paramètre.</span><span class="sxs-lookup"><span data-stu-id="0ab62-173">Windows PowerShell interprets all text between the `.PARAMETER` line and the next keyword or the end of the comment block as part of the parameter description.</span></span>
<span data-ttu-id="0ab62-174">La description peut inclure des sauts de paragraphe.</span><span class="sxs-lookup"><span data-stu-id="0ab62-174">The description can include paragraph breaks.</span></span>

```
.PARAMETER  <Parameter-Name>
```

<span data-ttu-id="0ab62-175">Les mots clés des paramètres peuvent apparaître dans n’importe quel ordre dans le bloc de commentaires, mais la syntaxe de la fonction ou du script détermine l’ordre dans lequel les paramètres (et leurs descriptions) s’affichent dans la rubrique d’aide.</span><span class="sxs-lookup"><span data-stu-id="0ab62-175">The Parameter keywords can appear in any order in the comment block, but the function or script syntax determines the order in which the parameters (and their descriptions) appear in help topic.</span></span> <span data-ttu-id="0ab62-176">Pour modifier l’ordre, modifiez la syntaxe.</span><span class="sxs-lookup"><span data-stu-id="0ab62-176">To change the order, change the syntax.</span></span>

<span data-ttu-id="0ab62-177">Vous pouvez également spécifier une description de paramètre en plaçant un commentaire dans la syntaxe de la fonction ou du script juste avant le nom de la variable de paramètre.</span><span class="sxs-lookup"><span data-stu-id="0ab62-177">You can also specify a parameter description by placing a comment in the function or script syntax immediately before the parameter variable name.</span></span> <span data-ttu-id="0ab62-178">Pour que cela fonctionne, vous devez également disposer d’un bloc de commentaires avec au moins un mot clé.</span><span class="sxs-lookup"><span data-stu-id="0ab62-178">For this to work, you must also have a comment block with at least one keyword.</span></span>

<span data-ttu-id="0ab62-179">Si vous utilisez à la fois un commentaire de syntaxe et un `.PARAMETER` mot clé, la description associée au `.PARAMETER` mot clé est utilisée et le commentaire de syntaxe est ignoré.</span><span class="sxs-lookup"><span data-stu-id="0ab62-179">If you use both a syntax comment and a `.PARAMETER` keyword, the description associated with the `.PARAMETER` keyword is used, and the syntax comment is ignored.</span></span>

```powershell
<#
.SYNOPSIS
    Short description here
#>
function Verb-Noun {
    [CmdletBinding()]
    param (
        # This is the same as .Parameter
        [string]$Computername
    )
    # Verb the Noun on the computer
}
```

### <a name="example"></a><span data-ttu-id="0ab62-180">. TELS</span><span class="sxs-lookup"><span data-stu-id="0ab62-180">.EXAMPLE</span></span>

<span data-ttu-id="0ab62-181">Exemple de commande qui utilise la fonction ou le script, éventuellement suivi d’un exemple de sortie et d’une description.</span><span class="sxs-lookup"><span data-stu-id="0ab62-181">A sample command that uses the function or script, optionally followed by sample output and a description.</span></span> <span data-ttu-id="0ab62-182">Répétez ce mot clé pour chaque exemple.</span><span class="sxs-lookup"><span data-stu-id="0ab62-182">Repeat this keyword for each example.</span></span>

### <a name="inputs"></a><span data-ttu-id="0ab62-183">. PORT</span><span class="sxs-lookup"><span data-stu-id="0ab62-183">.INPUTS</span></span>

<span data-ttu-id="0ab62-184">Types .NET d’objets qui peuvent être dirigés vers la fonction ou le script.</span><span class="sxs-lookup"><span data-stu-id="0ab62-184">The .NET types of objects that can be piped to the function or script.</span></span> <span data-ttu-id="0ab62-185">Vous pouvez également inclure une description des objets d’entrée.</span><span class="sxs-lookup"><span data-stu-id="0ab62-185">You can also include a description of the input objects.</span></span>

### <a name="outputs"></a><span data-ttu-id="0ab62-186">. ENVERRA</span><span class="sxs-lookup"><span data-stu-id="0ab62-186">.OUTPUTS</span></span>

<span data-ttu-id="0ab62-187">Type .NET des objets que l’applet de commande retourne.</span><span class="sxs-lookup"><span data-stu-id="0ab62-187">The .NET type of the objects that the cmdlet returns.</span></span> <span data-ttu-id="0ab62-188">Vous pouvez également inclure une description des objets retournés.</span><span class="sxs-lookup"><span data-stu-id="0ab62-188">You can also include a description of the returned objects.</span></span>

### <a name="notes"></a><span data-ttu-id="0ab62-189">. NOTES</span><span class="sxs-lookup"><span data-stu-id="0ab62-189">.NOTES</span></span>

<span data-ttu-id="0ab62-190">Informations supplémentaires sur la fonction ou le script.</span><span class="sxs-lookup"><span data-stu-id="0ab62-190">Additional information about the function or script.</span></span>

### <a name="link"></a><span data-ttu-id="0ab62-191">. LIEN</span><span class="sxs-lookup"><span data-stu-id="0ab62-191">.LINK</span></span>

<span data-ttu-id="0ab62-192">Nom d’une rubrique associée.</span><span class="sxs-lookup"><span data-stu-id="0ab62-192">The name of a related topic.</span></span> <span data-ttu-id="0ab62-193">La valeur apparaît sur la ligne sous le «. LINK» et doit être précédé d’un symbole de commentaire `#` ou inclus dans le bloc de commentaires.</span><span class="sxs-lookup"><span data-stu-id="0ab62-193">The value appears on the line below the ".LINK" keyword and must be preceded by a comment symbol `#` or included in the comment block.</span></span>

<span data-ttu-id="0ab62-194">Répétez le `.LINK` mot clé pour chaque rubrique associée.</span><span class="sxs-lookup"><span data-stu-id="0ab62-194">Repeat the `.LINK` keyword for each related topic.</span></span>

<span data-ttu-id="0ab62-195">Ce contenu apparaît dans la section Liens connexes de la rubrique d’aide.</span><span class="sxs-lookup"><span data-stu-id="0ab62-195">This content appears in the Related Links section of the help topic.</span></span>

<span data-ttu-id="0ab62-196">Le `.Link` contenu du mot clé peut également inclure une Uniform Resource Identifier (Uri) à une version en ligne de la même rubrique d’aide.</span><span class="sxs-lookup"><span data-stu-id="0ab62-196">The `.Link` keyword content can also include a Uniform Resource Identifier (URI) to an online version of the same help topic.</span></span> <span data-ttu-id="0ab62-197">La version en ligne s’ouvre lorsque vous utilisez le paramètre **Online** de `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="0ab62-197">The online version opens when you use the **Online** parameter of `Get-Help`.</span></span> <span data-ttu-id="0ab62-198">L’URI doit commencer par « http » ou « HTTPS ».</span><span class="sxs-lookup"><span data-stu-id="0ab62-198">The URI must begin with "http" or "https".</span></span>

### <a name="component"></a><span data-ttu-id="0ab62-199">. -</span><span class="sxs-lookup"><span data-stu-id="0ab62-199">.COMPONENT</span></span>

<span data-ttu-id="0ab62-200">Nom de la technologie ou de la fonctionnalité utilisée par la fonction ou le script, ou à laquelle elle est associée.</span><span class="sxs-lookup"><span data-stu-id="0ab62-200">The name of the technology or feature that the function or script uses, or to which it is related.</span></span> <span data-ttu-id="0ab62-201">Le paramètre **Component** de `Get-Help` utilise cette valeur pour filtrer les résultats de recherche retournés par `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="0ab62-201">The **Component** parameter of `Get-Help` uses this value to filter the search results returned by `Get-Help`.</span></span>

### <a name="role"></a><span data-ttu-id="0ab62-202">. ACTIF</span><span class="sxs-lookup"><span data-stu-id="0ab62-202">.ROLE</span></span>

<span data-ttu-id="0ab62-203">Nom du rôle d’utilisateur pour la rubrique d’aide.</span><span class="sxs-lookup"><span data-stu-id="0ab62-203">The name of the user role for the help topic.</span></span> <span data-ttu-id="0ab62-204">Le paramètre **role** de `Get-Help` utilise cette valeur pour filtrer les résultats de recherche retournés par `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="0ab62-204">The **Role** parameter of `Get-Help` uses this value to filter the search results returned by `Get-Help`.</span></span>

### <a name="functionality"></a><span data-ttu-id="0ab62-205">. SES</span><span class="sxs-lookup"><span data-stu-id="0ab62-205">.FUNCTIONALITY</span></span>

<span data-ttu-id="0ab62-206">Mots clés qui décrivent l’utilisation prévue de la fonction.</span><span class="sxs-lookup"><span data-stu-id="0ab62-206">The keywords that describe the intended use of the function.</span></span> <span data-ttu-id="0ab62-207">Le paramètre de **fonctionnalité** de `Get-Help` utilise cette valeur pour filtrer les résultats de recherche retournés par `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="0ab62-207">The **Functionality** parameter of `Get-Help` uses this value to filter the search results returned by `Get-Help`.</span></span>

### <a name="forwardhelptargetname"></a><span data-ttu-id="0ab62-208">. FORWARDHELPTARGETNAME</span><span class="sxs-lookup"><span data-stu-id="0ab62-208">.FORWARDHELPTARGETNAME</span></span>

<span data-ttu-id="0ab62-209">Redirige vers la rubrique d’aide pour la commande spécifiée.</span><span class="sxs-lookup"><span data-stu-id="0ab62-209">Redirects to the help topic for the specified command.</span></span> <span data-ttu-id="0ab62-210">Vous pouvez rediriger les utilisateurs vers n’importe quelle rubrique d’aide, y compris les rubriques d’aide d’une fonction, d’un script, d’une applet de commande ou d’un fournisseur.</span><span class="sxs-lookup"><span data-stu-id="0ab62-210">You can redirect users to any help topic, including help topics for a function, script, cmdlet, or provider.</span></span>

```powershell
# .FORWARDHELPTARGETNAME <Command-Name>
```

### <a name="forwardhelpcategory"></a><span data-ttu-id="0ab62-211">. FORWARDHELPCATEGORY</span><span class="sxs-lookup"><span data-stu-id="0ab62-211">.FORWARDHELPCATEGORY</span></span>

<span data-ttu-id="0ab62-212">Spécifie la catégorie d’aide de l’élément dans `.ForwardHelpTargetName` .</span><span class="sxs-lookup"><span data-stu-id="0ab62-212">Specifies the help category of the item in `.ForwardHelpTargetName`.</span></span> <span data-ttu-id="0ab62-213">Les valeurs valides sont `Alias` , `Cmdlet` , `HelpFile` , `Function` , `Provider` , `General` , `FAQ` , `Glossary` , `ScriptCommand` , `ExternalScript` , `Filter` ou `All` .</span><span class="sxs-lookup"><span data-stu-id="0ab62-213">Valid values are `Alias`, `Cmdlet`, `HelpFile`, `Function`, `Provider`, `General`, `FAQ`, `Glossary`, `ScriptCommand`, `ExternalScript`, `Filter`, or `All`.</span></span> <span data-ttu-id="0ab62-214">Utilisez ce mot clé pour éviter les conflits lorsqu’il existe des commandes portant le même nom.</span><span class="sxs-lookup"><span data-stu-id="0ab62-214">Use this keyword to avoid conflicts when there are commands with the same name.</span></span>

```powershell
# .FORWARDHELPCATEGORY <Category>
```

### <a name="remotehelprunspace"></a><span data-ttu-id="0ab62-215">. REMOTEHELPRUNSPACE</span><span class="sxs-lookup"><span data-stu-id="0ab62-215">.REMOTEHELPRUNSPACE</span></span>

<span data-ttu-id="0ab62-216">Spécifie une session qui contient la rubrique d’aide.</span><span class="sxs-lookup"><span data-stu-id="0ab62-216">Specifies a session that contains the help topic.</span></span> <span data-ttu-id="0ab62-217">Entrez une variable qui contient un objet **PSSession** .</span><span class="sxs-lookup"><span data-stu-id="0ab62-217">Enter a variable that contains a **PSSession** object.</span></span> <span data-ttu-id="0ab62-218">Ce mot clé est utilisé par l’applet de commande [Export-PSSession](xref:Microsoft.PowerShell.Utility.Export-PSSession) pour rechercher les rubriques d’aide pour les commandes exportées.</span><span class="sxs-lookup"><span data-stu-id="0ab62-218">This keyword is used by the [Export-PSSession](xref:Microsoft.PowerShell.Utility.Export-PSSession) cmdlet to find the help topics for the exported commands.</span></span>

```powershell
# .REMOTEHELPRUNSPACE <PSSession-variable>
```

### <a name="externalhelp"></a><span data-ttu-id="0ab62-219">. Commentaire ExternalHelp</span><span class="sxs-lookup"><span data-stu-id="0ab62-219">.EXTERNALHELP</span></span>

<span data-ttu-id="0ab62-220">Spécifie un fichier d’aide XML pour le script ou la fonction.</span><span class="sxs-lookup"><span data-stu-id="0ab62-220">Specifies an XML-based help file for the script or function.</span></span>

```powershell
# .EXTERNALHELP <XML Help File>
```

<span data-ttu-id="0ab62-221">Le `.ExternalHelp` mot clé est requis lorsqu’une fonction ou un script est documenté dans des fichiers XML.</span><span class="sxs-lookup"><span data-stu-id="0ab62-221">The `.ExternalHelp` keyword is required when a function or script is documented in XML files.</span></span> <span data-ttu-id="0ab62-222">Sans ce mot clé, `Get-Help` le fichier d’aide XML pour la fonction ou le script est introuvable.</span><span class="sxs-lookup"><span data-stu-id="0ab62-222">Without this keyword, `Get-Help` cannot find the XML-based help file for the function or script.</span></span>

<span data-ttu-id="0ab62-223">Le `.ExternalHelp` mot clé est prioritaire sur les autres mots clés d’aide basés sur des commentaires.</span><span class="sxs-lookup"><span data-stu-id="0ab62-223">The `.ExternalHelp` keyword takes precedence over other comment-based help keywords.</span></span> <span data-ttu-id="0ab62-224">Si `.ExternalHelp` est présent, `Get-Help` n’affiche pas l’aide basée sur les commentaires, même s’il ne trouve pas de rubrique d’aide qui correspond à la valeur du `.ExternalHelp` mot clé.</span><span class="sxs-lookup"><span data-stu-id="0ab62-224">If `.ExternalHelp` is present, `Get-Help` does not display comment-based help, even if it cannot find a help topic that matches the value of the `.ExternalHelp` keyword.</span></span>

<span data-ttu-id="0ab62-225">Si la fonction est exportée par un module, définissez la valeur du `.ExternalHelp` mot clé sur un nom de fichier sans chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="0ab62-225">If the function is exported by a module, set the value of the `.ExternalHelp` keyword to a filename without a path.</span></span> <span data-ttu-id="0ab62-226">`Get-Help` recherche le nom de fichier spécifié dans un sous-répertoire spécifique à la langue du répertoire du module.</span><span class="sxs-lookup"><span data-stu-id="0ab62-226">`Get-Help` looks for the specified file name in a language-specific subdirectory of the module directory.</span></span> <span data-ttu-id="0ab62-227">Il n’existe aucune condition requise pour le nom du fichier d’aide XML pour une fonction, mais il est recommandé d’utiliser le format suivant :</span><span class="sxs-lookup"><span data-stu-id="0ab62-227">There are no requirements for the name of the XML-based help file for a function, but a best practice is to use the following format:</span></span>

```
<ScriptModule.psm1>-help.xml
```

<span data-ttu-id="0ab62-228">Si la fonction n’est pas incluse dans un module, incluez un chemin d’accès au fichier d’aide XML.</span><span class="sxs-lookup"><span data-stu-id="0ab62-228">If the function is not included in a module, include a path to the XML-based help file.</span></span> <span data-ttu-id="0ab62-229">Si la valeur inclut un chemin d’accès et que le chemin d’accès contient des sous-répertoires spécifiques à la culture de l’interface utilisateur, `Get-Help` recherche les sous-répertoires de manière récursive pour un fichier XML portant le nom du script ou de la fonction conformément aux normes de langue de secours établies pour Windows, tout comme dans un répertoire de module.</span><span class="sxs-lookup"><span data-stu-id="0ab62-229">If the value includes a path and the path contains UI-culture-specific subdirectories, `Get-Help` searches the subdirectories recursively for an XML file with the name of the script or function in accordance with the language fallback standards established for Windows, just as it does in a module directory.</span></span>

<span data-ttu-id="0ab62-230">Pour plus d’informations sur le format de fichier d’aide XML de l’applet de commande, consultez [Comment écrire l’aide sur les applets de](/powershell/scripting/developer/help/writing-comment-based-help-topics)commande.</span><span class="sxs-lookup"><span data-stu-id="0ab62-230">For more information about the cmdlet help XML-based help file format, see [How to Write Cmdlet Help](/powershell/scripting/developer/help/writing-comment-based-help-topics).</span></span>

## <a name="autogenerated-content"></a><span data-ttu-id="0ab62-231">Contenu généré automatiquement</span><span class="sxs-lookup"><span data-stu-id="0ab62-231">Autogenerated content</span></span>

<span data-ttu-id="0ab62-232">Le nom, la syntaxe, la liste de paramètres, la table d’attributs des paramètres, les paramètres communs et les notes sont générés automatiquement par l’applet de commande `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="0ab62-232">The name, syntax, parameter list, parameter attribute table, common parameters, and remarks are automatically generated by the `Get-Help` cmdlet.</span></span>

### <a name="name"></a><span data-ttu-id="0ab62-233">Nom</span><span class="sxs-lookup"><span data-stu-id="0ab62-233">Name</span></span>

<span data-ttu-id="0ab62-234">La section **nom** d’une rubrique d’aide de la fonction est extraite du nom de la fonction dans la syntaxe de la fonction.</span><span class="sxs-lookup"><span data-stu-id="0ab62-234">The **Name** section of a function help topic is taken from the function name in the function syntax.</span></span> <span data-ttu-id="0ab62-235">Le **nom** d’une rubrique d’aide de script est extrait du nom de fichier du script.</span><span class="sxs-lookup"><span data-stu-id="0ab62-235">The **Name** of a script help topic is taken from the script filename.</span></span> <span data-ttu-id="0ab62-236">Pour modifier le nom ou la mise en majuscules, modifiez la syntaxe de la fonction ou le nom de fichier du script.</span><span class="sxs-lookup"><span data-stu-id="0ab62-236">To change the name or its capitalization, change the function syntax or the script filename.</span></span>

### <a name="syntax"></a><span data-ttu-id="0ab62-237">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0ab62-237">Syntax</span></span>

<span data-ttu-id="0ab62-238">La section **syntaxe** de la rubrique d’aide est générée à partir de la syntaxe de la fonction ou du script.</span><span class="sxs-lookup"><span data-stu-id="0ab62-238">The **Syntax** section of the help topic is generated from the function or script syntax.</span></span> <span data-ttu-id="0ab62-239">Pour ajouter des détails à la syntaxe de la rubrique d’aide, comme le type .NET d’un paramètre, ajoutez les détails à la syntaxe.</span><span class="sxs-lookup"><span data-stu-id="0ab62-239">To add detail to the help topic syntax, such as the .NET type of a parameter, add the detail to the syntax.</span></span> <span data-ttu-id="0ab62-240">Si vous ne spécifiez pas de type de paramètre, le type d' **objet** est inséré en tant que valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="0ab62-240">If you do not specify a parameter type, the **Object** type is inserted as the default value.</span></span>

### <a name="parameter-list"></a><span data-ttu-id="0ab62-241">Liste de paramètres</span><span class="sxs-lookup"><span data-stu-id="0ab62-241">Parameter List</span></span>

<span data-ttu-id="0ab62-242">La liste de paramètres de la rubrique d’aide est générée à partir de la syntaxe de la fonction ou du script et des descriptions que vous ajoutez à l’aide du `.Parameter` mot clé.</span><span class="sxs-lookup"><span data-stu-id="0ab62-242">The parameter list in the help topic is generated from the function or script syntax and from the descriptions that you add by using the `.Parameter` keyword.</span></span> <span data-ttu-id="0ab62-243">Les paramètres de fonction s’affichent dans la section **paramètres** de la rubrique d’aide dans l’ordre dans lequel ils apparaissent dans la syntaxe de la fonction ou du script.</span><span class="sxs-lookup"><span data-stu-id="0ab62-243">The function parameters appear in the **Parameters** section of the help topic in the same order that they appear in the function or script syntax.</span></span> <span data-ttu-id="0ab62-244">L’orthographe et la mise en majuscules des noms de paramètres proviennent également de la syntaxe.</span><span class="sxs-lookup"><span data-stu-id="0ab62-244">The spelling and capitalization of parameter names is also taken from the syntax.</span></span> <span data-ttu-id="0ab62-245">Elle n’est pas affectée par le nom de paramètre spécifié par le `.Parameter` mot clé.</span><span class="sxs-lookup"><span data-stu-id="0ab62-245">It is not affected by the parameter name specified by the `.Parameter` keyword.</span></span>

### <a name="common-parameters"></a><span data-ttu-id="0ab62-246">Paramètres communs</span><span class="sxs-lookup"><span data-stu-id="0ab62-246">Common Parameters</span></span>

<span data-ttu-id="0ab62-247">Les **paramètres communs** sont ajoutés à la liste de syntaxe et de paramètres de la rubrique d’aide, même s’ils n’ont aucun effet.</span><span class="sxs-lookup"><span data-stu-id="0ab62-247">The **Common parameters** are added to the syntax and parameter list of the help topic, even if they have no effect.</span></span> <span data-ttu-id="0ab62-248">Pour plus d’informations sur les paramètres communs, consultez [about_CommonParameters](about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="0ab62-248">For more information about the common parameters, see [about_CommonParameters](about_CommonParameters.md).</span></span>

### <a name="parameter-attribute-table"></a><span data-ttu-id="0ab62-249">Table d’attributs de paramètre</span><span class="sxs-lookup"><span data-stu-id="0ab62-249">Parameter Attribute Table</span></span>

<span data-ttu-id="0ab62-250">`Get-Help` génère la table d’attributs de paramètres qui apparaît lorsque vous utilisez le paramètre **complet** ou le paramètre de **paramètre** de `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="0ab62-250">`Get-Help` generates the table of parameter attributes that appears when you use the **Full** or **Parameter** parameter of `Get-Help`.</span></span> <span data-ttu-id="0ab62-251">La valeur des attributs **requis** , de **position** et de valeur **par défaut** est extraite de la syntaxe de la fonction ou du script.</span><span class="sxs-lookup"><span data-stu-id="0ab62-251">The value of the **Required** , **Position** , and **Default** value attributes is taken from the function or script syntax.</span></span>

<span data-ttu-id="0ab62-252">Les valeurs par défaut et une valeur pour **accepter les caractères génériques** n’apparaissent pas dans la table attribut de paramètre, même lorsqu’elles sont définies dans la fonction ou le script.</span><span class="sxs-lookup"><span data-stu-id="0ab62-252">Default values and a value for **Accept Wildcard characters** do not appear in the parameter attribute table even when they are defined in the function or script.</span></span> <span data-ttu-id="0ab62-253">Pour aider les utilisateurs, fournissez ces informations dans la description du paramètre.</span><span class="sxs-lookup"><span data-stu-id="0ab62-253">To help users, provide this information in the parameter description.</span></span>

### <a name="remarks"></a><span data-ttu-id="0ab62-254">Remarques</span><span class="sxs-lookup"><span data-stu-id="0ab62-254">Remarks</span></span>

<span data-ttu-id="0ab62-255">La section **Notes** de la rubrique d’aide est générée automatiquement à partir du nom de la fonction ou du script.</span><span class="sxs-lookup"><span data-stu-id="0ab62-255">The **Remarks** section of the help topic is automatically generated from the function or script name.</span></span> <span data-ttu-id="0ab62-256">Vous ne pouvez pas modifier ou affecter son contenu.</span><span class="sxs-lookup"><span data-stu-id="0ab62-256">You cannot change or affect its content.</span></span>

## <a name="examples"></a><span data-ttu-id="0ab62-257">Exemples</span><span class="sxs-lookup"><span data-stu-id="0ab62-257">Examples</span></span>

### <a name="comment-based-help-for-a-function"></a><span data-ttu-id="0ab62-258">Aide sur les commentaires pour une fonction</span><span class="sxs-lookup"><span data-stu-id="0ab62-258">Comment-based Help for a Function</span></span>

<span data-ttu-id="0ab62-259">L’exemple de fonction suivant comprend une aide basée sur des commentaires :</span><span class="sxs-lookup"><span data-stu-id="0ab62-259">The following sample function includes comment-based help:</span></span>

```powershell
function Add-Extension
{
param ([string]$Name,[string]$Extension = "txt")
$name = $name + "." + $extension
$name

<#
.SYNOPSIS

Adds a file name extension to a supplied name.

.DESCRIPTION

Adds a file name extension to a supplied name.
Takes any strings for the file name or extension.

.PARAMETER Name
Specifies the file name.

.PARAMETER Extension
Specifies the extension. "Txt" is the default.

.INPUTS

None. You cannot pipe objects to Add-Extension.

.OUTPUTS

System.String. Add-Extension returns a string with the extension
or file name.

.EXAMPLE

PS> extension -name "File"
File.txt

.EXAMPLE

PS> extension -name "File" -extension "doc"
File.doc

.EXAMPLE

PS> extension "File" "doc"
File.doc

.LINK

http://www.fabrikam.com/extension.html

.LINK

Set-Item
#>
}
```

<span data-ttu-id="0ab62-260">Les résultats sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="0ab62-260">The results are as follows:</span></span>

```powershell
Get-Help -Name "Add-Extension" -Full
```

```Output
NAME

Add-Extension

SYNOPSIS

Adds a file name extension to a supplied name.

SYNTAX

Add-Extension [[-Name] <String>] [[-Extension] <String>]
[<CommonParameters>]

DESCRIPTION

Adds a file name extension to a supplied name. Takes any strings for the
file name or extension.

PARAMETERS

-Name
Specifies the file name.

Required?                    false
Position?                    0
Default value
Accept pipeline input?       false
Accept wildcard characters?

-Extension
Specifies the extension. "Txt" is the default.

Required?                    false
Position?                    1
Default value
Accept pipeline input?       false
Accept wildcard characters?

<CommonParameters>
This cmdlet supports the common parameters: -Verbose, -Debug,
-ErrorAction, -ErrorVariable, -WarningAction, -WarningVariable,
-OutBuffer and -OutVariable. For more information, type
"get-help about_commonparameters".

INPUTS
None. You cannot pipe objects to Add-Extension.

OUTPUTS

System.String. Add-Extension returns a string with the extension or
file name.

Example 1

PS> extension -name "File"
File.txt

Example 2

PS> extension -name "File" -extension "doc"
File.doc

Example 3

PS> extension "File" "doc"
File.doc

RELATED LINKS

http://www.fabrikam.com/extension.html
Set-Item
```

### <a name="parameter-descriptions-in-function-syntax"></a><span data-ttu-id="0ab62-261">Descriptions des paramètres dans la syntaxe de fonction</span><span class="sxs-lookup"><span data-stu-id="0ab62-261">Parameter Descriptions in Function Syntax</span></span>

<span data-ttu-id="0ab62-262">Cet exemple est identique au précédent, hormis le fait que les descriptions des paramètres sont insérées dans la syntaxe de la fonction.</span><span class="sxs-lookup"><span data-stu-id="0ab62-262">This example is the same as the previous one, except that the parameter descriptions are inserted in the function syntax.</span></span> <span data-ttu-id="0ab62-263">Ce format est particulièrement utile lorsque les descriptions sont courtes.</span><span class="sxs-lookup"><span data-stu-id="0ab62-263">This format is most useful when the descriptions are brief.</span></span>

```powershell
function Add-Extension
{
param
(

[string]
#Specifies the file name.
$name,

[string]
#Specifies the file name extension. "Txt" is the default.
$extension = "txt"
)

$name = $name + "." + $extension
$name

<#
.SYNOPSIS

Adds a file name extension to a supplied name.

.DESCRIPTION

Adds a file name extension to a supplied name. Takes any strings for the
file name or extension.

.INPUTS

None. You cannot pipe objects to Add-Extension.

.OUTPUTS

System.String. Add-Extension returns a string with the extension or
file name.

.EXAMPLE

PS> extension -name "File"
File.txt

.EXAMPLE

PS> extension -name "File" -extension "doc"
File.doc

.EXAMPLE

PS> extension "File" "doc"
File.doc

.LINK

http://www.fabrikam.com/extension.html

.LINK

Set-Item
#>
}
```

### <a name="comment-based-help-for-a-script"></a><span data-ttu-id="0ab62-264">Aide sur les commentaires pour un script</span><span class="sxs-lookup"><span data-stu-id="0ab62-264">Comment-based Help for a Script</span></span>

<span data-ttu-id="0ab62-265">L’exemple de script suivant comprend une aide basée sur des commentaires.</span><span class="sxs-lookup"><span data-stu-id="0ab62-265">The following sample script includes comment-based help.</span></span> <span data-ttu-id="0ab62-266">Notez les lignes vides entre la fermeture `#>` et l' `Param` instruction.</span><span class="sxs-lookup"><span data-stu-id="0ab62-266">Notice the blank lines between the closing `#>` and the `Param` statement.</span></span> <span data-ttu-id="0ab62-267">Dans un script qui n’a pas d' `Param` instruction, il doit y avoir au moins deux lignes vides entre le commentaire final de la rubrique d’aide et la première déclaration de fonction.</span><span class="sxs-lookup"><span data-stu-id="0ab62-267">In a script that does not have a `Param` statement, there must be at least two blank lines between the final comment in the help topic and the first function declaration.</span></span> <span data-ttu-id="0ab62-268">Sans ces lignes vides, `Get-Help` associe la rubrique d’aide à la fonction, et non pas au script.</span><span class="sxs-lookup"><span data-stu-id="0ab62-268">Without these blank lines, `Get-Help` associates the help topic with the function, not the script.</span></span>

```powershell
<#
.SYNOPSIS

Performs monthly data updates.

.DESCRIPTION

The Update-Month.ps1 script updates the registry with new data generated
during the past month and generates a report.

.PARAMETER InputPath
Specifies the path to the CSV-based input file.

.PARAMETER OutputPath
Specifies the name and path for the CSV-based output file. By default,
MonthlyUpdates.ps1 generates a name from the date and time it runs, and
saves the output in the local directory.

.INPUTS

None. You cannot pipe objects to Update-Month.ps1.

.OUTPUTS

None. Update-Month.ps1 does not generate any output.

.EXAMPLE

PS> .\Update-Month.ps1

.EXAMPLE

PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv

.EXAMPLE

PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv -outputPath `
C:\Reports\2009\January.csv
#>

param ([string]$InputPath, [string]$OutPutPath)

function Get-Data { }
...
```

<span data-ttu-id="0ab62-269">La commande suivante obtient l’aide du script.</span><span class="sxs-lookup"><span data-stu-id="0ab62-269">The following command gets the script help.</span></span> <span data-ttu-id="0ab62-270">Étant donné que le script n’est pas dans un répertoire qui est listé dans la `$env:Path` variable d’environnement, la `Get-Help` commande qui obtient l’aide du script doit spécifier le chemin d’accès du script.</span><span class="sxs-lookup"><span data-stu-id="0ab62-270">Because the script is not in a directory that is listed in the `$env:Path` environment variable, the `Get-Help` command that gets the script help must specify the script path.</span></span>

```powershell
Get-Help -Path .\update-month.ps1 -Full
```

```Output
# NAME

C:\ps-test\Update-Month.ps1

# SYNOPSIS

Performs monthly data updates.

# SYNTAX

C:\ps-test\Update-Month.ps1 [-InputPath] <String> [[-OutputPath]
<String>] [<CommonParameters>]

# DESCRIPTION

The Update-Month.ps1 script updates the registry with new data
generated during the past month and generates a report.

# PARAMETERS

-InputPath
Specifies the path to the CSV-based input file.

Required?                    true
Position?                    0
Default value
Accept pipeline input?       false
Accept wildcard characters?

-OutputPath
Specifies the name and path for the CSV-based output file. By
default, MonthlyUpdates.ps1 generates a name from the date
and time it runs, and saves the output in the local directory.

Required?                    false
Position?                    1
Default value
Accept pipeline input?       false
Accept wildcard characters?

<CommonParameters>
This cmdlet supports the common parameters: -Verbose, -Debug,
-ErrorAction, -ErrorVariable, -WarningAction, -WarningVariable,
-OutBuffer and -OutVariable. For more information, type,
"get-help about_commonparameters".

# INPUTS

None. You cannot pipe objects to Update-Month.ps1.

# OUTPUTS

None. Update-Month.ps1 does not generate any output.

Example 1

PS> .\Update-Month.ps1

Example 2

PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv

Example 3

PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv -outputPath
C:\Reports\2009\January.csv

# RELATED LINKS
```

### <a name="redirecting-to-an-xml-file"></a><span data-ttu-id="0ab62-271">Redirection vers un fichier XML</span><span class="sxs-lookup"><span data-stu-id="0ab62-271">Redirecting to an XML File</span></span>

<span data-ttu-id="0ab62-272">Vous pouvez écrire des rubriques d’aide basées sur XML pour des fonctions et des scripts.</span><span class="sxs-lookup"><span data-stu-id="0ab62-272">You can write XML-based help topics for functions and scripts.</span></span> <span data-ttu-id="0ab62-273">Bien que l’aide basée sur les commentaires soit plus facile à implémenter, une aide XML est nécessaire pour obtenir de l’aide actualisable et pour fournir des rubriques d’aide dans plusieurs langues.</span><span class="sxs-lookup"><span data-stu-id="0ab62-273">Although comment-based help is easier to implement, XML-based help is required for Updatable Help and to provide help topics in multiple languages.</span></span>

<span data-ttu-id="0ab62-274">L’exemple suivant montre les premières lignes du script de Update-Month.ps1.</span><span class="sxs-lookup"><span data-stu-id="0ab62-274">The following example shows the first few lines of the Update-Month.ps1 script.</span></span>
<span data-ttu-id="0ab62-275">Le script utilise le `.ExternalHelp` mot clé pour spécifier le chemin d’accès à une rubrique d’aide XML pour le script.</span><span class="sxs-lookup"><span data-stu-id="0ab62-275">The script uses the `.ExternalHelp` keyword to specify the path to an XML-based help topic for the script.</span></span>

<span data-ttu-id="0ab62-276">Notez que la valeur du `.ExternalHelp` mot clé apparaît sur la même ligne que le mot clé.</span><span class="sxs-lookup"><span data-stu-id="0ab62-276">Note that the value of the `.ExternalHelp` keyword appears on the same line as the keyword.</span></span> <span data-ttu-id="0ab62-277">Tout autre placement est inefficace.</span><span class="sxs-lookup"><span data-stu-id="0ab62-277">Any other placement is ineffective.</span></span>

```powershell
# .ExternalHelp C:\MyScripts\Update-Month-Help.xml

param ([string]$InputPath, [string]$OutPutPath)
function Get-Data { }
...
```

<span data-ttu-id="0ab62-278">Les exemples suivants illustrent trois emplacements valides du `.ExternalHelp` mot clé dans une fonction.</span><span class="sxs-lookup"><span data-stu-id="0ab62-278">The following examples show three valid placements of the `.ExternalHelp` keyword in a function.</span></span>

```powershell
function Add-Extension
{
# .ExternalHelp C:\ps-test\Add-Extension.xml

param ([string] $name, [string]$extension = "txt")
$name = $name + "." + $extension
$name
}
```

```powershell
function Add-Extension
{
param ([string] $name, [string]$extension = "txt")
$name = $name + "." + $extension
$name

# .ExternalHelp C:\ps-test\Add-Extension.xml
}
```

```powershell
# .ExternalHelp C:\ps-test\Add-Extension.xml
function Add-Extension
{
param ([string] $name, [string]$extension = "txt")
$name = $name + "." + $extension
$name
}
```

### <a name="redirecting-to-a-different-help-topic"></a><span data-ttu-id="0ab62-279">Redirection vers une autre rubrique d’aide</span><span class="sxs-lookup"><span data-stu-id="0ab62-279">Redirecting to a Different Help Topic</span></span>

<span data-ttu-id="0ab62-280">Le code suivant est un extrait du début de la fonction d’aide intégrée dans PowerShell, qui affiche un écran de texte d’aide à la fois.</span><span class="sxs-lookup"><span data-stu-id="0ab62-280">The following code is an excerpt from the beginning of the built-in help function in PowerShell, which displays one screen of help text at a time.</span></span>
<span data-ttu-id="0ab62-281">Étant donné que la rubrique d’aide de l’applet de commande `Get-Help` décrit la fonction d’aide, la fonction d’aide utilise les `.ForwardHelpTargetName` `.ForwardHelpCategory` Mots clés et pour rediriger l’utilisateur vers la `Get-Help` rubrique d’aide de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="0ab62-281">Because the help topic for the `Get-Help` cmdlet describes the help function, the help function uses the `.ForwardHelpTargetName` and `.ForwardHelpCategory` keywords to redirect the user to the `Get-Help` cmdlet help topic.</span></span>

```powershell
function help
{

<#
.FORWARDHELPTARGETNAME Get-Help
.FORWARDHELPCATEGORY Cmdlet
#>
[CmdletBinding(DefaultParameterSetName='AllUsersView')]
param(
[Parameter(Position=0, ValueFromPipelineByPropertyName=$true)]
[System.String]
${Name},
...
```

<span data-ttu-id="0ab62-282">La commande suivante utilise cette fonctionnalité :</span><span class="sxs-lookup"><span data-stu-id="0ab62-282">The following command uses this feature:</span></span>

```powershell
Get-Help -Name help
```

```Output
NAME

Get-Help

SYNOPSIS

Displays information about PowerShell cmdlets and concepts.
...
```

## <a name="see-also"></a><span data-ttu-id="0ab62-283">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0ab62-283">See also</span></span>

[<span data-ttu-id="0ab62-284">about_Functions</span><span class="sxs-lookup"><span data-stu-id="0ab62-284">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="0ab62-285">about_Functions_Advanced_Parameters</span><span class="sxs-lookup"><span data-stu-id="0ab62-285">about_Functions_Advanced_Parameters</span></span>](about_Functions_Advanced_Parameters.md)

[<span data-ttu-id="0ab62-286">about_Scripts</span><span class="sxs-lookup"><span data-stu-id="0ab62-286">about_Scripts</span></span>](about_Scripts.md)

[<span data-ttu-id="0ab62-287">Comment écrire l’aide sur les applets de commande</span><span class="sxs-lookup"><span data-stu-id="0ab62-287">How to Write Cmdlet Help</span></span>](https://go.microsoft.com/fwlink/?LinkID=123415)
