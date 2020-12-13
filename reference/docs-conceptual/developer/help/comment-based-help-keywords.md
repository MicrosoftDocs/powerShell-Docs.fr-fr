---
ms.date: 06/09/2020
ms.topic: reference
title: Mots clés de l’aide basée sur les commentaires
description: Mots clés de l’aide basée sur les commentaires
ms.openlocfilehash: d87dde8700813767f6c09cfce70ed06c7964ebc7
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645480"
---
# <a name="comment-based-help-keywords"></a><span data-ttu-id="fa8fd-103">Mots clés de l’aide basée sur les commentaires</span><span class="sxs-lookup"><span data-stu-id="fa8fd-103">Comment-Based Help Keywords</span></span>

<span data-ttu-id="fa8fd-104">Cette rubrique répertorie et décrit les mots clés de l’aide basée sur les commentaires.</span><span class="sxs-lookup"><span data-stu-id="fa8fd-104">This topic lists and describes the keywords in comment-based help.</span></span>

## <a name="keywords-in-comment-based-help"></a><span data-ttu-id="fa8fd-105">Mots clés dans Comment-Based aide</span><span class="sxs-lookup"><span data-stu-id="fa8fd-105">Keywords in Comment-Based Help</span></span>

<span data-ttu-id="fa8fd-106">Les éléments suivants sont des mots clés d’aide basés sur des commentaires valides.</span><span class="sxs-lookup"><span data-stu-id="fa8fd-106">The following are valid comment-based Help keywords.</span></span> <span data-ttu-id="fa8fd-107">Ils sont répertoriés dans l’ordre dans lequel ils apparaissent généralement dans une rubrique d’aide, ainsi que l’utilisation prévue.</span><span class="sxs-lookup"><span data-stu-id="fa8fd-107">They are listed in the order in which they typically appear in a Help topic along with their intended use.</span></span> <span data-ttu-id="fa8fd-108">Ces mots clés peuvent apparaître dans n’importe quel ordre dans l’aide basée sur les commentaires, et ils ne respectent pas la casse.</span><span class="sxs-lookup"><span data-stu-id="fa8fd-108">These keywords can appear in any order in the comment-based Help, and they are not case-sensitive.</span></span>

<span data-ttu-id="fa8fd-109">Notez que le `.EXTERNALHELP` mot clé est prioritaire sur tous les autres mots clés d’aide basés sur les commentaires.</span><span class="sxs-lookup"><span data-stu-id="fa8fd-109">Note that the `.EXTERNALHELP` keyword takes precedence over all other comment-based help keywords.</span></span>
<span data-ttu-id="fa8fd-110">Lorsque `.EXTERNALHELP` est présent, l’applet de [commande Microsoft. PowerShell. Commands. GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) n’affiche pas d’aide basée sur les commentaires, même lorsqu’il ne trouve pas de fichier d’aide qui correspond à la valeur du mot clé.</span><span class="sxs-lookup"><span data-stu-id="fa8fd-110">When `.EXTERNALHELP` is present, the [Microsoft.PowerShell.Commands.GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) cmdlet does not display comment-based help, even when it cannot find a help file that matches the value of the keyword.</span></span>

## <a name="synopsis"></a><span data-ttu-id="fa8fd-111">. SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="fa8fd-111">.SYNOPSIS</span></span>

<span data-ttu-id="fa8fd-112">Brève description de la fonction ou du script.</span><span class="sxs-lookup"><span data-stu-id="fa8fd-112">A brief description of the function or script.</span></span> <span data-ttu-id="fa8fd-113">Ce mot clé ne peut être utilisé qu’une seule fois dans chaque rubrique.</span><span class="sxs-lookup"><span data-stu-id="fa8fd-113">This keyword can be used only once in each topic.</span></span>

## <a name="description"></a><span data-ttu-id="fa8fd-114">. DESCRIPTIVE</span><span class="sxs-lookup"><span data-stu-id="fa8fd-114">.DESCRIPTION</span></span>

<span data-ttu-id="fa8fd-115">Description détaillée de la fonction ou du script.</span><span class="sxs-lookup"><span data-stu-id="fa8fd-115">A detailed description of the function or script.</span></span> <span data-ttu-id="fa8fd-116">Ce mot clé ne peut être utilisé qu’une seule fois dans chaque rubrique.</span><span class="sxs-lookup"><span data-stu-id="fa8fd-116">This keyword can be used only once in each topic.</span></span>

## <a name="parameter-parameter-name"></a><span data-ttu-id="fa8fd-117">. PARAMÈTRE \<Parameter-Name></span><span class="sxs-lookup"><span data-stu-id="fa8fd-117">.PARAMETER \<Parameter-Name></span></span>

<span data-ttu-id="fa8fd-118">Description d’un paramètre.</span><span class="sxs-lookup"><span data-stu-id="fa8fd-118">The description of a parameter.</span></span> <span data-ttu-id="fa8fd-119">Vous pouvez inclure un `.PARAMETER` mot clé pour chaque paramètre dans la fonction ou le script.</span><span class="sxs-lookup"><span data-stu-id="fa8fd-119">You can include a `.PARAMETER` keyword for each parameter in the function or script.</span></span>

<span data-ttu-id="fa8fd-120">Les `.PARAMETER` Mots clés peuvent apparaître dans n’importe quel ordre dans le bloc de commentaires, mais l’ordre dans lequel les paramètres apparaissent dans la `Param` déclaration d’instruction ou de fonction détermine l’ordre dans lequel les paramètres apparaissent dans la rubrique d’aide.</span><span class="sxs-lookup"><span data-stu-id="fa8fd-120">The `.PARAMETER` keywords can appear in any order in the comment block, but the order in which the parameters appear in the `Param` statement or function declaration determines the order in which the parameters appear in Help topic.</span></span> <span data-ttu-id="fa8fd-121">Pour modifier l’ordre des paramètres dans la rubrique d’aide, modifiez l’ordre des paramètres dans la `Param` déclaration de l’instruction ou de la fonction.</span><span class="sxs-lookup"><span data-stu-id="fa8fd-121">To change the order of parameters in the Help topic, change the order of the parameters in the `Param` statement or function declaration.</span></span>

<span data-ttu-id="fa8fd-122">Vous pouvez également spécifier une description de paramètre en plaçant un commentaire dans l' `Param` instruction juste avant le nom de la variable de paramètre.</span><span class="sxs-lookup"><span data-stu-id="fa8fd-122">You can also specify a parameter description by placing a comment in the `Param` statement immediately before the parameter variable name.</span></span> <span data-ttu-id="fa8fd-123">Si vous utilisez à la fois un `Param` commentaire d’instruction et un `.PARAMETER` mot clé, la description associée au `.PARAMETER` mot clé est utilisée et le commentaire de l' `Param` instruction est ignoré.</span><span class="sxs-lookup"><span data-stu-id="fa8fd-123">If you use both a `Param` statement comment and a `.PARAMETER` keyword, the description associated with the `.PARAMETER` keyword is used, and the `Param` statement comment is ignored.</span></span>

## <a name="example"></a><span data-ttu-id="fa8fd-124">. TELS</span><span class="sxs-lookup"><span data-stu-id="fa8fd-124">.EXAMPLE</span></span>

<span data-ttu-id="fa8fd-125">Exemple de commande qui utilise la fonction ou le script, éventuellement suivi d’un exemple de sortie et d’une description.</span><span class="sxs-lookup"><span data-stu-id="fa8fd-125">A sample command that uses the function or script, optionally followed by sample output and a description.</span></span> <span data-ttu-id="fa8fd-126">Répétez ce mot clé pour chaque exemple.</span><span class="sxs-lookup"><span data-stu-id="fa8fd-126">Repeat this keyword for each example.</span></span>

## <a name="inputs"></a><span data-ttu-id="fa8fd-127">. PORT</span><span class="sxs-lookup"><span data-stu-id="fa8fd-127">.INPUTS</span></span>

<span data-ttu-id="fa8fd-128">Microsoft .NET Framework types d’objets qui peuvent être dirigés vers la fonction ou le script.</span><span class="sxs-lookup"><span data-stu-id="fa8fd-128">The Microsoft .NET Framework types of objects that can be piped to the function or script.</span></span> <span data-ttu-id="fa8fd-129">Vous pouvez également inclure une description des objets d’entrée.</span><span class="sxs-lookup"><span data-stu-id="fa8fd-129">You can also include a description of the input objects.</span></span>

## <a name="outputs"></a><span data-ttu-id="fa8fd-130">. ENVERRA</span><span class="sxs-lookup"><span data-stu-id="fa8fd-130">.OUTPUTS</span></span>

<span data-ttu-id="fa8fd-131">.NET Framework type des objets que l’applet de commande retourne.</span><span class="sxs-lookup"><span data-stu-id="fa8fd-131">The .NET Framework type of the objects that the cmdlet returns.</span></span> <span data-ttu-id="fa8fd-132">Vous pouvez également inclure une description des objets retournés.</span><span class="sxs-lookup"><span data-stu-id="fa8fd-132">You can also include a description of the returned objects.</span></span>

## <a name="notes"></a><span data-ttu-id="fa8fd-133">. NOTES</span><span class="sxs-lookup"><span data-stu-id="fa8fd-133">.NOTES</span></span>

<span data-ttu-id="fa8fd-134">Informations supplémentaires sur la fonction ou le script.</span><span class="sxs-lookup"><span data-stu-id="fa8fd-134">Additional information about the function or script.</span></span>

## <a name="link"></a><span data-ttu-id="fa8fd-135">. LIEN</span><span class="sxs-lookup"><span data-stu-id="fa8fd-135">.LINK</span></span>

<span data-ttu-id="fa8fd-136">Nom d’une rubrique associée.</span><span class="sxs-lookup"><span data-stu-id="fa8fd-136">The name of a related topic.</span></span> <span data-ttu-id="fa8fd-137">Répétez ce mot clé pour chaque rubrique associée.</span><span class="sxs-lookup"><span data-stu-id="fa8fd-137">Repeat this keyword for each related topic.</span></span> <span data-ttu-id="fa8fd-138">Ce contenu apparaît dans la section Liens connexes de la rubrique d’aide.</span><span class="sxs-lookup"><span data-stu-id="fa8fd-138">This content appears in the Related Links section of the Help topic.</span></span>

<span data-ttu-id="fa8fd-139">Le `.LINK` contenu du mot clé peut également inclure une Uniform Resource Identifier (Uri) à une version en ligne de la même rubrique d’aide.</span><span class="sxs-lookup"><span data-stu-id="fa8fd-139">The `.LINK` keyword content can also include a Uniform Resource Identifier (URI) to an online version of the same Help topic.</span></span> <span data-ttu-id="fa8fd-140">La version en ligne s’ouvre lorsque vous utilisez le `Online` paramètre de `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="fa8fd-140">The online version opens when you use the `Online` parameter of `Get-Help`.</span></span> <span data-ttu-id="fa8fd-141">L’URI doit commencer par « http » ou « HTTPS ».</span><span class="sxs-lookup"><span data-stu-id="fa8fd-141">The URI must begin with "http" or "https".</span></span>

## <a name="component"></a><span data-ttu-id="fa8fd-142">. -</span><span class="sxs-lookup"><span data-stu-id="fa8fd-142">.COMPONENT</span></span>

<span data-ttu-id="fa8fd-143">Nom de la technologie ou de la fonctionnalité utilisée par la fonction ou le script, ou à laquelle elle est associée.</span><span class="sxs-lookup"><span data-stu-id="fa8fd-143">The name of the technology or feature that the function or script uses, or to which it is related.</span></span>
<span data-ttu-id="fa8fd-144">Le paramètre **Component** de `Get-Help` utilise cette valeur pour filtrer les résultats de recherche retournés par `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="fa8fd-144">The **Component** parameter of `Get-Help` uses this value to filter the search results returned by `Get-Help`.</span></span>

## <a name="role"></a><span data-ttu-id="fa8fd-145">. Actif</span><span class="sxs-lookup"><span data-stu-id="fa8fd-145">.Role</span></span>

<span data-ttu-id="fa8fd-146">Nom du rôle d’utilisateur pour la rubrique d’aide.</span><span class="sxs-lookup"><span data-stu-id="fa8fd-146">The name of the user role for the help topic.</span></span> <span data-ttu-id="fa8fd-147">Le paramètre **role** de `Get-Help` utilise cette valeur pour filtrer les résultats de recherche retournés par `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="fa8fd-147">The **Role** parameter of `Get-Help` uses this value to filter the search results returned by `Get-Help`.</span></span>

## <a name="functionality"></a><span data-ttu-id="fa8fd-148">. SES</span><span class="sxs-lookup"><span data-stu-id="fa8fd-148">.FUNCTIONALITY</span></span>

<span data-ttu-id="fa8fd-149">Mots clés qui décrivent l’utilisation prévue de la fonction.</span><span class="sxs-lookup"><span data-stu-id="fa8fd-149">The keywords that describe the intended use of the function.</span></span> <span data-ttu-id="fa8fd-150">Le paramètre de **fonctionnalité** de `Get-Help` utilise cette valeur pour filtrer les résultats de recherche retournés par `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="fa8fd-150">The **Functionality** parameter of `Get-Help` uses this value to filter the search results returned by `Get-Help`.</span></span>

## <a name="forwardhelptargetname-command-name"></a><span data-ttu-id="fa8fd-151">. FORWARDHELPTARGETNAME \<Command-Name></span><span class="sxs-lookup"><span data-stu-id="fa8fd-151">.FORWARDHELPTARGETNAME \<Command-Name></span></span>

<span data-ttu-id="fa8fd-152">Redirige vers la rubrique d’aide pour la commande spécifiée.</span><span class="sxs-lookup"><span data-stu-id="fa8fd-152">Redirects to the Help topic for the specified command.</span></span> <span data-ttu-id="fa8fd-153">Vous pouvez rediriger les utilisateurs vers n’importe quelle rubrique d’aide, y compris les rubriques d’aide d’une fonction, d’un script, d’une applet de commande ou d’un fournisseur.</span><span class="sxs-lookup"><span data-stu-id="fa8fd-153">You can redirect users to any Help topic, including Help topics for a function, script, cmdlet, or provider.</span></span>

## <a name="forwardhelpcategory-category"></a><span data-ttu-id="fa8fd-154">. FORWARDHELPCATEGORY \<Category></span><span class="sxs-lookup"><span data-stu-id="fa8fd-154">.FORWARDHELPCATEGORY \<Category></span></span>

<span data-ttu-id="fa8fd-155">Spécifie la catégorie d’aide de l’élément dans `.FORWARDHELPTARGETNAME` .</span><span class="sxs-lookup"><span data-stu-id="fa8fd-155">Specifies the Help category of the item in `.FORWARDHELPTARGETNAME`.</span></span> <span data-ttu-id="fa8fd-156">Utilisez ce mot clé pour éviter les conflits lorsqu’il existe des commandes portant le même nom.</span><span class="sxs-lookup"><span data-stu-id="fa8fd-156">Use this keyword to avoid conflicts when there are commands with the same name.</span></span>

<span data-ttu-id="fa8fd-157">Les valeurs autorisées sont :</span><span class="sxs-lookup"><span data-stu-id="fa8fd-157">Valid values are:</span></span>

- <span data-ttu-id="fa8fd-158">Alias</span><span class="sxs-lookup"><span data-stu-id="fa8fd-158">Alias</span></span>
- <span data-ttu-id="fa8fd-159">Applet de commande</span><span class="sxs-lookup"><span data-stu-id="fa8fd-159">Cmdlet</span></span>
- <span data-ttu-id="fa8fd-160">HelpFile</span><span class="sxs-lookup"><span data-stu-id="fa8fd-160">HelpFile</span></span>
- <span data-ttu-id="fa8fd-161">Fonction</span><span class="sxs-lookup"><span data-stu-id="fa8fd-161">Function</span></span>
- <span data-ttu-id="fa8fd-162">Fournisseur</span><span class="sxs-lookup"><span data-stu-id="fa8fd-162">Provider</span></span>
- <span data-ttu-id="fa8fd-163">Général</span><span class="sxs-lookup"><span data-stu-id="fa8fd-163">General</span></span>
- <span data-ttu-id="fa8fd-164">Questions fréquentes (FAQ)</span><span class="sxs-lookup"><span data-stu-id="fa8fd-164">FAQ</span></span>
- <span data-ttu-id="fa8fd-165">Glossaire</span><span class="sxs-lookup"><span data-stu-id="fa8fd-165">Glossary</span></span>
- <span data-ttu-id="fa8fd-166">ScriptCommand</span><span class="sxs-lookup"><span data-stu-id="fa8fd-166">ScriptCommand</span></span>
- <span data-ttu-id="fa8fd-167">ExternalScript</span><span class="sxs-lookup"><span data-stu-id="fa8fd-167">ExternalScript</span></span>
- <span data-ttu-id="fa8fd-168">Filtrer</span><span class="sxs-lookup"><span data-stu-id="fa8fd-168">Filter</span></span>
- <span data-ttu-id="fa8fd-169">Tous</span><span class="sxs-lookup"><span data-stu-id="fa8fd-169">All</span></span>

## <a name="remotehelprunspace-pssession-variable"></a><span data-ttu-id="fa8fd-170">. REMOTEHELPRUNSPACE \<PSSession-variable></span><span class="sxs-lookup"><span data-stu-id="fa8fd-170">.REMOTEHELPRUNSPACE \<PSSession-variable></span></span>

<span data-ttu-id="fa8fd-171">Spécifie une session qui contient la rubrique d’aide.</span><span class="sxs-lookup"><span data-stu-id="fa8fd-171">Specifies a session that contains the Help topic.</span></span> <span data-ttu-id="fa8fd-172">Entrez une variable qui contient une session PSSession.</span><span class="sxs-lookup"><span data-stu-id="fa8fd-172">Enter a variable that contains a PSSession.</span></span> <span data-ttu-id="fa8fd-173">Ce mot clé est utilisé par l' `Export-PSSession` applet de commande pour rechercher les rubriques d’aide pour les commandes exportées.</span><span class="sxs-lookup"><span data-stu-id="fa8fd-173">This keyword is used by the `Export-PSSession` cmdlet to find the Help topics for the exported commands.</span></span>

## <a name="externalhelp-xml-help-file"></a><span data-ttu-id="fa8fd-174">. Commentaire ExternalHelp \<XML Help File></span><span class="sxs-lookup"><span data-stu-id="fa8fd-174">.EXTERNALHELP \<XML Help File></span></span>

<span data-ttu-id="fa8fd-175">Spécifie le chemin d’accès et/ou le nom d’un fichier d’aide XML pour le script ou la fonction.</span><span class="sxs-lookup"><span data-stu-id="fa8fd-175">Specifies the path and/or name of an XML-based Help file for the script or function.</span></span>

<span data-ttu-id="fa8fd-176">Le `.EXTERNALHELP` mot clé indique à l’applet de [commande Microsoft. PowerShell. Commands. GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) d’obtenir de l’aide sur le script ou la fonction dans un fichier XML.</span><span class="sxs-lookup"><span data-stu-id="fa8fd-176">The `.EXTERNALHELP` keyword tells the [Microsoft.PowerShell.Commands.GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) cmdlet to get help for the script or function in an XML-based file.</span></span> <span data-ttu-id="fa8fd-177">Le `.EXTERNALHELP` mot clé est requis lors de l’utilisation d’un fichier d’aide XML pour un script ou une fonction.</span><span class="sxs-lookup"><span data-stu-id="fa8fd-177">The `.EXTERNALHELP` keyword is required when using an XML-based help file for a script or function.</span></span> <span data-ttu-id="fa8fd-178">Sans celui-ci, `Get-Help` ne trouvera pas de fichier d’aide pour la fonction ou le script.</span><span class="sxs-lookup"><span data-stu-id="fa8fd-178">Without it, `Get-Help` will not find a help file for the function or script.</span></span>

<span data-ttu-id="fa8fd-179">Le `.EXTERNALHELP` mot clé est prioritaire sur tous les autres mots clés d’aide basés sur les commentaires.</span><span class="sxs-lookup"><span data-stu-id="fa8fd-179">The `.EXTERNALHELP` keyword takes precedence over all other comment-based help keywords.</span></span> <span data-ttu-id="fa8fd-180">Lorsque `.EXTERNALHELP` est présent, l’applet de [commande Microsoft. PowerShell. Commands. GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) n’affiche pas d’aide basée sur les commentaires, même lorsqu’il ne trouve pas de fichier d’aide qui correspond à la valeur du mot clé.</span><span class="sxs-lookup"><span data-stu-id="fa8fd-180">When `.EXTERNALHELP` is present, the [Microsoft.PowerShell.Commands.GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) cmdlet does not display comment-based help, even when it cannot find a help file that matches the value of the keyword.</span></span>

<span data-ttu-id="fa8fd-181">Lorsque la fonction est exportée par un module de script, la valeur de `.EXTERNALHELP` doit être un nom de fichier sans chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="fa8fd-181">When the function is exported by a script module, the value of `.EXTERNALHELP` should be a filename without a path.</span></span> <span data-ttu-id="fa8fd-182">`Get-Help` recherche le fichier dans un sous-répertoire spécifique aux paramètres régionaux du répertoire du module.</span><span class="sxs-lookup"><span data-stu-id="fa8fd-182">`Get-Help` looks for the file in a locale-specific subdirectory of the module directory.</span></span> <span data-ttu-id="fa8fd-183">Il n’existe aucune condition requise pour le nom de fichier, mais il est recommandé d’utiliser le format de nom de fichier suivant : `<ScriptModule>.psm1-help.xml` .</span><span class="sxs-lookup"><span data-stu-id="fa8fd-183">There are no requirements for the filename, but a best practice is to use the following filename format: `<ScriptModule>.psm1-help.xml`.</span></span>

<span data-ttu-id="fa8fd-184">Lorsque la fonction n’est pas associée à un module, incluez un chemin d’accès et un nom de fichier dans la valeur du `.EXTERNALHELP` mot clé.</span><span class="sxs-lookup"><span data-stu-id="fa8fd-184">When the function is not associated with a module, include a path and filename in the value of the `.EXTERNALHELP` keyword.</span></span> <span data-ttu-id="fa8fd-185">Si le chemin d’accès spécifié au fichier XML contient des sous-répertoires spécifiques à la culture de l’interface utilisateur, `Get-Help` recherche les sous-répertoires de manière récursive pour un fichier XML portant le nom du script ou de la fonction conformément aux normes de langue de secours établies pour Windows, tout comme pour toutes les rubriques d’aide basées sur XML.</span><span class="sxs-lookup"><span data-stu-id="fa8fd-185">If the specified path to the XML file contains UI-culture-specific subdirectories, `Get-Help` searches the subdirectories recursively for an XML file with the name of the script or function in accordance with the language fallback standards established for Windows, just as it does for all XML-based Help topics.</span></span>

<span data-ttu-id="fa8fd-186">Pour plus d’informations sur le format de fichier d’aide XML de l’applet de commande, consultez écriture de l’aide sur les [applets de commande Windows PowerShell](./writing-help-for-windows-powershell-cmdlets.md).</span><span class="sxs-lookup"><span data-stu-id="fa8fd-186">For more information about the cmdlet Help XML-based Help file format, see [Writing Windows PowerShell Cmdlet Help](./writing-help-for-windows-powershell-cmdlets.md).</span></span>
