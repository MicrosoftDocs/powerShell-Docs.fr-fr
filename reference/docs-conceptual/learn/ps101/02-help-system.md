---
title: Système d’aide
description: La maîtrise du système d’aide est la clé d’une utilisation optimale de PowerShell.
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 98876cf324b367fd5bb3c3462cb90ea6d7c7d5b9
ms.sourcegitcommit: 0942a6de384f4a1c624e89b1889434a30d22f4d6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2020
ms.locfileid: "93143312"
---
# <a name="chapter-2---the-help-system"></a><span data-ttu-id="df76f-103">Chapitre 2 – Le système d’aide</span><span class="sxs-lookup"><span data-stu-id="df76f-103">Chapter 2 - The Help System</span></span>

<span data-ttu-id="df76f-104">Deux groupes de professionnels de l’informatique ont été soumis à une épreuve écrite sans ordinateur pour déterminer leur niveau de compétence PowerShell.</span><span class="sxs-lookup"><span data-stu-id="df76f-104">Two groups of IT pros were given a written test without access to a computer to determine their skill level with PowerShell.</span></span> <span data-ttu-id="df76f-105">Les utilisateurs novices de PowerShell ont été placés dans un groupe et les experts dans un autre.</span><span class="sxs-lookup"><span data-stu-id="df76f-105">PowerShell beginners were placed in one group and experts in another.</span></span>
<span data-ttu-id="df76f-106">Au vu des résultats de l’épreuve, le niveau de compétence entre les deux groupes ne semblait pas très différent.</span><span class="sxs-lookup"><span data-stu-id="df76f-106">Based on the results of the test, there didn't seem to be much difference in the skill level between the two groups.</span></span> <span data-ttu-id="df76f-107">Une deuxième épreuve comparable à la première a été soumise aux deux groupes.</span><span class="sxs-lookup"><span data-stu-id="df76f-107">Both groups were given a second test similar to the first one.</span></span> <span data-ttu-id="df76f-108">Cette fois, un ordinateur leur a été fourni avec PowerShell, mais sans accès à Internet.</span><span class="sxs-lookup"><span data-stu-id="df76f-108">This time they were given access to a computer with PowerShell that didn't have access to the internet.</span></span> <span data-ttu-id="df76f-109">Les résultats de la deuxième épreuve ont révélé une grande différence dans le niveau de compétence entre les deux groupes.</span><span class="sxs-lookup"><span data-stu-id="df76f-109">The results of the second test showed a huge difference in the skill level between the two groups.</span></span> <span data-ttu-id="df76f-110">Les experts ne connaissaient pas toujours les réponses, mais ils savaient comment les trouver.</span><span class="sxs-lookup"><span data-stu-id="df76f-110">Experts don't always know the answers, but they know how to figure out the answers.</span></span>

<span data-ttu-id="df76f-111">Quelle a été la différence dans les résultats des première et deuxième épreuves entre ces deux groupes ?</span><span class="sxs-lookup"><span data-stu-id="df76f-111">What was the difference in the results of the first and second test between these two groups?</span></span>

<span data-ttu-id="df76f-112">Les différences observées dans ces deux épreuves ne s’expliquent pas par le fait que les experts savent comment utiliser les milliers de commandes qui existent dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="df76f-112">The differences observed in these two tests were because experts don't memorize how to use thousands of commands in PowerShell.</span></span> <span data-ttu-id="df76f-113">Ils apprennent à utiliser parfaitement le système d’aide de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="df76f-113">They learn how to use the help system within PowerShell extremely well.</span></span>
<span data-ttu-id="df76f-114">Ils peuvent ainsi trouver les commandes nécessaires quand ils en ont besoin et savoir comment les utiliser une fois qu’ils les ont trouvées.</span><span class="sxs-lookup"><span data-stu-id="df76f-114">This allows them to find the necessary commands when needed and how to use those commands once they've found them.</span></span>

<span data-ttu-id="df76f-115">J’ai souvent entendu Jeffrey Snover, l’inventeur de PowerShell, dire des choses similaires.</span><span class="sxs-lookup"><span data-stu-id="df76f-115">I've heard Jeffrey Snover, the inventor of PowerShell, tell a similar story a number of times.</span></span>

<span data-ttu-id="df76f-116">La maîtrise du système d’aide est la clé d’une utilisation optimale de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="df76f-116">Mastering the help system is the key to being successful with PowerShell.</span></span>

## <a name="discoverability"></a><span data-ttu-id="df76f-117">Détectabilité</span><span class="sxs-lookup"><span data-stu-id="df76f-117">Discoverability</span></span>

<span data-ttu-id="df76f-118">Les commandes compilées dans PowerShell s’appellent des applets de commande.</span><span class="sxs-lookup"><span data-stu-id="df76f-118">Compiled commands in PowerShell are called cmdlets.</span></span> <span data-ttu-id="df76f-119">Leur abréviation en anglais est « cmdlet », qui se prononce « command-let » (et non CMD-let).</span><span class="sxs-lookup"><span data-stu-id="df76f-119">Cmdlet is pronounced "command-let" (not CMD-let).</span></span> <span data-ttu-id="df76f-120">Le nom des applets de commande se présente sous la forme « Verbe-Nom » pour en faciliter la recherche.</span><span class="sxs-lookup"><span data-stu-id="df76f-120">Cmdlets names have the form of singular "Verb-Noun" commands to make them easily discoverable.</span></span> <span data-ttu-id="df76f-121">Par exemple, l’applet de commande permettant d’identifier les processus en cours d’exécution est `Get-Process` et l’applet de commande destinée à récupérer la liste des services et leur état est `Get-Service`.</span><span class="sxs-lookup"><span data-stu-id="df76f-121">For example, the cmdlet for determining what processes are running is `Get-Process` and the cmdlet for retrieving a list of services and their statuses is `Get-Service`.</span></span> <span data-ttu-id="df76f-122">Il existe d’autres types de commandes dans PowerShell comme les alias et les fonctions qui seront abordées plus loin dans ce livre.</span><span class="sxs-lookup"><span data-stu-id="df76f-122">There are other types of commands in PowerShell such as aliases and functions that will be covered later in this book.</span></span> <span data-ttu-id="df76f-123">Le terme « commande PowerShell » est un terme générique qui est souvent employé pour désigner n’importe quel type de commande dans PowerShell, qu’il s’agisse d’une applet de commande, d’une fonction ou d’un alias.</span><span class="sxs-lookup"><span data-stu-id="df76f-123">The term PowerShell command is a generic term that's often used to refer to any type of command in PowerShell, regardless of whether or not it's a cmdlet, function, or alias.</span></span>

## <a name="the-three-core-cmdlets-in-powershell"></a><span data-ttu-id="df76f-124">Les trois principales applets de commande dans PowerShell</span><span class="sxs-lookup"><span data-stu-id="df76f-124">The Three Core Cmdlets in PowerShell</span></span>

- `Get-Command`
- `Get-Help`
- <span data-ttu-id="df76f-125">`Get-Member` (décrite dans le chapitre 3)</span><span class="sxs-lookup"><span data-stu-id="df76f-125">`Get-Member` (covered in chapter 3)</span></span>

<span data-ttu-id="df76f-126">On me pose souvent la question suivante : comment savoir à quoi servent les différentes commandes dans PowerShell ?</span><span class="sxs-lookup"><span data-stu-id="df76f-126">One question I'm often asked is how do you figure out what the commands are in PowerShell?</span></span> <span data-ttu-id="df76f-127">`Get-Command` et `Get-Help` permettent toutes deux d’identifier les commandes.</span><span class="sxs-lookup"><span data-stu-id="df76f-127">Both `Get-Command` and `Get-Help` can be used to determine the commands.</span></span>

## <a name="get-help"></a><span data-ttu-id="df76f-128">Get-Help</span><span class="sxs-lookup"><span data-stu-id="df76f-128">Get-Help</span></span>

<span data-ttu-id="df76f-129">`Get-Help` est une commande polyvalente.</span><span class="sxs-lookup"><span data-stu-id="df76f-129">`Get-Help` is a multipurpose command.</span></span> <span data-ttu-id="df76f-130">`Get-Help` vous indique comment utiliser les commandes une fois que vous les avez trouvées.</span><span class="sxs-lookup"><span data-stu-id="df76f-130">`Get-Help` helps you learn how to use commands once you find them.</span></span> <span data-ttu-id="df76f-131">`Get-Help` permet aussi de localiser les commandes, mais pas de la même manière qu’avec `Get-Command` et pas de façon aussi directe.</span><span class="sxs-lookup"><span data-stu-id="df76f-131">`Get-Help` can also be used to help locate commands, but in a different and more indirect way when compared to `Get-Command`.</span></span>

<span data-ttu-id="df76f-132">Quand la commande `Get-Help` est utilisée pour localiser des commandes, l’entrée fournie est d’abord comparée aux noms de commandes.</span><span class="sxs-lookup"><span data-stu-id="df76f-132">When `Get-Help` is used to locate commands, it first searches for wildcard matches of command names based on the provided input.</span></span> <span data-ttu-id="df76f-133">Si l’opération ne donne rien, la recherche porte alors sur les rubriques d’aide proprement dites. Si aucune correspondance n’est trouvée, une erreur est retournée.</span><span class="sxs-lookup"><span data-stu-id="df76f-133">If it doesn't find a match, it searches through the help topics themselves, and if no match is found an error is returned.</span></span> <span data-ttu-id="df76f-134">Contrairement à l’idée reçue, `Get-Help` peut servir à rechercher des commandes pour lesquelles il n’existe pas de rubriques d’aide.</span><span class="sxs-lookup"><span data-stu-id="df76f-134">Contrary to popular belief, `Get-Help` can be used to find commands that don't have help topics.</span></span>

<span data-ttu-id="df76f-135">La première chose à savoir concernant le système d’aide de PowerShell, c’est la façon d’utiliser l’applet de commande `Get-Help`.</span><span class="sxs-lookup"><span data-stu-id="df76f-135">The first thing you need to know about the help system in PowerShell is how to use the `Get-Help` cmdlet.</span></span> <span data-ttu-id="df76f-136">La commande suivante sert à afficher la rubrique d’aide pour `Get-Help`.</span><span class="sxs-lookup"><span data-stu-id="df76f-136">The following command is used to display the help topic for `Get-Help`.</span></span>

```powershell
Get-Help -Name Get-Help
```

```Output
Do you want to run Update-Help?
The Update-Help cmdlet downloads the most current Help files for Windows PowerShell
modules, and installs them on your computer. For more information about the Update-Help
cmdlet, see http://go.microsoft.com/fwlink/?LinkId=210614.
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="df76f-137">Depuis PowerShell version 3, l’aide de PowerShell n’est pas intégrée au système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="df76f-137">Beginning with PowerShell version 3, PowerShell help doesn't ship with the operating system.</span></span> <span data-ttu-id="df76f-138">La première fois que `Get-Help` est exécutée pour une commande, le message précédent s’affiche.</span><span class="sxs-lookup"><span data-stu-id="df76f-138">The first time `Get-Help` is run for a command, the previous message is displayed.</span></span> <span data-ttu-id="df76f-139">Si la fonction `help` ou l’alias `man` est utilisé à la place de l’applet de commande `Get-Help`, vous n’obtenez pas cette invite.</span><span class="sxs-lookup"><span data-stu-id="df76f-139">If the `help` function or `man` alias is used instead of the `Get-Help` cmdlet, you don't receive this prompt.</span></span>

<span data-ttu-id="df76f-140">Si vous répondez par Oui en appuyant sur <kbd>Y</kbd>, l’applet de commande `Update-Help` s’exécute, ce qui nécessite un accès à Internet par défaut.</span><span class="sxs-lookup"><span data-stu-id="df76f-140">Answering yes by pressing <kbd>Y</kbd> runs the `Update-Help` cmdlet, which requires internet access by default.</span></span> <span data-ttu-id="df76f-141">`Y` peut être spécifié en majuscules ou en minuscules.</span><span class="sxs-lookup"><span data-stu-id="df76f-141">`Y` can be specified in either upper or lower case.</span></span>

<span data-ttu-id="df76f-142">Une fois que l’aide est téléchargée et la mise à jour terminée, la rubrique d’aide est retournée pour la commande spécifiée :</span><span class="sxs-lookup"><span data-stu-id="df76f-142">Once the help is downloaded and the update is complete, the help topic is returned for the specified command:</span></span>

```powershell
Get-Help -Name Get-Help
```

<span data-ttu-id="df76f-143">Prenez le temps d’exécuter cet exemple sur votre ordinateur, d’examiner la sortie et d’observer la façon dont les informations sont regroupées :</span><span class="sxs-lookup"><span data-stu-id="df76f-143">Take a moment to run that example on your computer, review the output, and take note of how the information is grouped:</span></span>

- <span data-ttu-id="df76f-144">NOM</span><span class="sxs-lookup"><span data-stu-id="df76f-144">NAME</span></span>
- <span data-ttu-id="df76f-145">RÉSUMÉ</span><span class="sxs-lookup"><span data-stu-id="df76f-145">SYNOPSIS</span></span>
- <span data-ttu-id="df76f-146">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="df76f-146">SYNTAX</span></span>
- <span data-ttu-id="df76f-147">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="df76f-147">DESCRIPTION</span></span>
- <span data-ttu-id="df76f-148">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="df76f-148">RELATED LINKS</span></span>
- <span data-ttu-id="df76f-149">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="df76f-149">REMARKS</span></span>

<span data-ttu-id="df76f-150">Comme vous pouvez le constater, les rubriques d’aide peuvent contenir une masse d’informations, encore que vous ne voyez là qu’une partie de la rubrique d’aide.</span><span class="sxs-lookup"><span data-stu-id="df76f-150">As you can see, help topics can contain an enormous amount of information and this isn't even the entire help topic.</span></span>

<span data-ttu-id="df76f-151">Bien que cela ne soit pas propre à PowerShell, un paramètre offre un moyen de fournir une entrée à une commande.</span><span class="sxs-lookup"><span data-stu-id="df76f-151">While not specific to PowerShell, a parameter is a way to provide input to a command.</span></span> <span data-ttu-id="df76f-152">`Get-Help` compte de nombreux paramètres qui, lorsqu’ils sont spécifiés, permettent de retourner l’intégralité de la rubrique d’aide ou une partie de celle-ci.</span><span class="sxs-lookup"><span data-stu-id="df76f-152">`Get-Help` has many parameters that can be specified in order to return the entire help topic or a subset of it.</span></span>

<span data-ttu-id="df76f-153">La section syntaxe de la rubrique d’aide présentée dans le jeu de résultats précédent liste tous les paramètres de `Get-Help`.</span><span class="sxs-lookup"><span data-stu-id="df76f-153">The syntax section of the help topic shown in the previous set of results lists all of the parameters for `Get-Help`.</span></span> <span data-ttu-id="df76f-154">À première vue, il semble que les mêmes paramètres sont listés à six différentes reprises.</span><span class="sxs-lookup"><span data-stu-id="df76f-154">At first glance, it appears the same parameters are listed six different times.</span></span> <span data-ttu-id="df76f-155">Chacun de ces différents blocs de la section syntaxe est un jeu de paramètres.</span><span class="sxs-lookup"><span data-stu-id="df76f-155">Each of those different blocks in the syntax section is a parameter set.</span></span> <span data-ttu-id="df76f-156">Cela signifie que l’applet de commande `Get-Help` compte six jeux de paramètres différents.</span><span class="sxs-lookup"><span data-stu-id="df76f-156">This means the `Get-Help` cmdlet has six different parameter sets.</span></span> <span data-ttu-id="df76f-157">À y regarder de plus près, vous remarquerez que chaque jeu de paramètres contient un paramètre différent.</span><span class="sxs-lookup"><span data-stu-id="df76f-157">If you take a closer look, you'll notice that at least one parameter is different in each of the parameter sets.</span></span>

<span data-ttu-id="df76f-158">Les jeux de paramètres s’excluent mutuellement.</span><span class="sxs-lookup"><span data-stu-id="df76f-158">Parameter sets are mutually exclusive.</span></span> <span data-ttu-id="df76f-159">Dès lors qu’un paramètre unique qui n’existe que dans un seul des jeux de paramètres est utilisé, seuls les paramètres contenus dans ce jeu de paramètres peuvent être utilisés.</span><span class="sxs-lookup"><span data-stu-id="df76f-159">Once a unique parameter that only exists in one of the parameter sets is used, only parameters contained within that parameter set can be used.</span></span> <span data-ttu-id="df76f-160">Par exemple, il n’est pas possible de spécifier les paramètres **Full** et **Detailed** en même temps, car ils se trouvent dans des jeux de paramètres différents.</span><span class="sxs-lookup"><span data-stu-id="df76f-160">For example, both the **Full** and **Detailed** parameters couldn't be specified at the same time because they are in different parameter sets.</span></span>

<span data-ttu-id="df76f-161">Chacun des paramètres suivants se trouve dans des jeux de paramètres différents :</span><span class="sxs-lookup"><span data-stu-id="df76f-161">Each of the following parameters are in different parameter sets:</span></span>

- <span data-ttu-id="df76f-162">Full</span><span class="sxs-lookup"><span data-stu-id="df76f-162">Full</span></span>
- <span data-ttu-id="df76f-163">Detailed</span><span class="sxs-lookup"><span data-stu-id="df76f-163">Detailed</span></span>
- <span data-ttu-id="df76f-164">Examples</span><span class="sxs-lookup"><span data-stu-id="df76f-164">Examples</span></span>
- <span data-ttu-id="df76f-165">Online</span><span class="sxs-lookup"><span data-stu-id="df76f-165">Online</span></span>
- <span data-ttu-id="df76f-166">Parameter</span><span class="sxs-lookup"><span data-stu-id="df76f-166">Parameter</span></span>
- <span data-ttu-id="df76f-167">ShowWindow</span><span class="sxs-lookup"><span data-stu-id="df76f-167">ShowWindow</span></span>

<span data-ttu-id="df76f-168">Toute la syntaxe énigmatique comme les crochets et les accolades figurant dans la section syntaxe a une signification, mais ce point sera abordé dans l’Annexe A de ce livre.</span><span class="sxs-lookup"><span data-stu-id="df76f-168">All of the cryptic syntax such as square and angle brackets in the syntax section means something but will be covered in Appendix A of this book.</span></span> <span data-ttu-id="df76f-169">Bien qu’il soit important d’apprendre ce à quoi correspond cette syntaxe énigmatique, il est souvent difficile de s’en souvenir pour une personne qui débute sur PowerShell et qui ne l’utilise pas forcément tous les jours.</span><span class="sxs-lookup"><span data-stu-id="df76f-169">While important, learning the cryptic syntax is often difficult to retain for someone who is new to PowerShell and may not use it everyday.</span></span>

<span data-ttu-id="df76f-170">Pour plus d’informations sur la syntaxe énigmatique, consultez l’[Annexe A][].</span><span class="sxs-lookup"><span data-stu-id="df76f-170">For more information to better understand the cryptic syntax, see [Appendix A][].</span></span>

<span data-ttu-id="df76f-171">Pour les débutants, il existe un moyen plus simple d’obtenir les mêmes informations, mais dans un langage compréhensible.</span><span class="sxs-lookup"><span data-stu-id="df76f-171">For beginners, there's an easier way to figure out the same information except in plain language.</span></span>

<span data-ttu-id="df76f-172">Quand le paramètre **Full** de `Get-Help` est spécifié, la rubrique d’aide entière est retournée.</span><span class="sxs-lookup"><span data-stu-id="df76f-172">When the **Full** parameter of `Get-Help` is specified, the entire help topic is returned.</span></span>

```powershell
Get-Help -Name Get-Help -Full
```

<span data-ttu-id="df76f-173">Prenez le temps d’exécuter cet exemple sur votre ordinateur, d’examiner la sortie et d’observer la façon dont les informations sont regroupées :</span><span class="sxs-lookup"><span data-stu-id="df76f-173">Take a moment to run that example on your computer, review the output, and take note of how the information is grouped:</span></span>

- <span data-ttu-id="df76f-174">NOM</span><span class="sxs-lookup"><span data-stu-id="df76f-174">NAME</span></span>
- <span data-ttu-id="df76f-175">RÉSUMÉ</span><span class="sxs-lookup"><span data-stu-id="df76f-175">SYNOPSIS</span></span>
- <span data-ttu-id="df76f-176">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="df76f-176">SYNTAX</span></span>
- <span data-ttu-id="df76f-177">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="df76f-177">DESCRIPTION</span></span>
- <span data-ttu-id="df76f-178">PARAMÈTRES</span><span class="sxs-lookup"><span data-stu-id="df76f-178">PARAMETERS</span></span>
- <span data-ttu-id="df76f-179">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="df76f-179">INPUTS</span></span>
- <span data-ttu-id="df76f-180">SORTIES</span><span class="sxs-lookup"><span data-stu-id="df76f-180">OUTPUTS</span></span>
- <span data-ttu-id="df76f-181">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="df76f-181">NOTES</span></span>
- <span data-ttu-id="df76f-182">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="df76f-182">EXAMPLES</span></span>
- <span data-ttu-id="df76f-183">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="df76f-183">RELATED LINKS</span></span>

<span data-ttu-id="df76f-184">Notez que l’utilisation du paramètre **Full** a retourné plusieurs sections supplémentaires, dont celle intitulée PARAMÈTRES qui fournit davantage d’informations que la section SYNTAXE énigmatique.</span><span class="sxs-lookup"><span data-stu-id="df76f-184">Notice that using the **Full** parameter returned several additional sections, one of which is the PARAMETERS section that provides more information than the cryptic SYNTAX section.</span></span>

<span data-ttu-id="df76f-185">Le paramètre **Full** est un paramètre booléen.</span><span class="sxs-lookup"><span data-stu-id="df76f-185">The **Full** parameter is a switch parameter.</span></span> <span data-ttu-id="df76f-186">Un paramètre booléen est un paramètre qui ne nécessite pas de valeur.</span><span class="sxs-lookup"><span data-stu-id="df76f-186">A parameter that doesn't require a value is called a switch parameter.</span></span> <span data-ttu-id="df76f-187">Quand un paramètre de ce type est spécifié, sa valeur est true. Quand il ne l’est pas, sa valeur est false.</span><span class="sxs-lookup"><span data-stu-id="df76f-187">When a switch parameter is specified, its value is true and when it's not, its value is false.</span></span>

<span data-ttu-id="df76f-188">Si vous avez parcouru ce chapitre dans la console PowerShell, vous avez remarqué que la commande précédente qui permet d’afficher l’intégralité de la rubrique d’aide pour `Get-Help` est passée à toute vitesse sur l’écran sans même vous laisser le temps de la lire.</span><span class="sxs-lookup"><span data-stu-id="df76f-188">If you've been working through this chapter in the PowerShell console, you noticed that the previous command to display the full help topic for `Get-Help` flew by on the screen without giving you a chance to read it.</span></span> <span data-ttu-id="df76f-189">Il existe une meilleure solution.</span><span class="sxs-lookup"><span data-stu-id="df76f-189">There's a better way.</span></span>

<span data-ttu-id="df76f-190">`Help` est une fonction qui canalise `Get-Help` vers une fonction nommée `more`, qui est un wrapper pour le fichier exécutable `more.com` dans Windows.</span><span class="sxs-lookup"><span data-stu-id="df76f-190">`Help` is a function that pipes `Get-Help` to a function named `more`, which is a wrapper for the `more.com` executable file in Windows.</span></span> <span data-ttu-id="df76f-191">Dans la console PowerShell, `help` fournit une page d’aide à la fois.</span><span class="sxs-lookup"><span data-stu-id="df76f-191">In the PowerShell console, `help` provides one page of help at a time.</span></span> <span data-ttu-id="df76f-192">Dans l’environnement ISE, elle fonctionne de la même façon que `Get-Help`.</span><span class="sxs-lookup"><span data-stu-id="df76f-192">In the ISE, it works the same way as `Get-Help`.</span></span> <span data-ttu-id="df76f-193">Ma recommandation est d’utiliser la fonction `help` à la place de l’applet de commande `Get-Help`, car elle offre une meilleure expérience et nécessite moins de saisie.</span><span class="sxs-lookup"><span data-stu-id="df76f-193">My recommendation is to use the `help` function instead of the `Get-Help` cmdlet since it provides a better experience and it's less to type.</span></span>

<span data-ttu-id="df76f-194">Cependant, saisir moins n’est pas toujours un avantage.</span><span class="sxs-lookup"><span data-stu-id="df76f-194">Less typing isn't always a good thing, however.</span></span> <span data-ttu-id="df76f-195">Si vous envisagez d’enregistrer vos commandes sous forme de script ou de les partager avec d’autres utilisateurs, veillez à utiliser des noms complets d’applets de commande et de paramètres.</span><span class="sxs-lookup"><span data-stu-id="df76f-195">If you're going to save your commands as a script or share them with someone else, be sure to use full cmdlet and parameter names.</span></span> <span data-ttu-id="df76f-196">Les noms complets sont explicites et plus faciles à comprendre.</span><span class="sxs-lookup"><span data-stu-id="df76f-196">The full names are self-documenting, which makes them easier to understand.</span></span> <span data-ttu-id="df76f-197">Pensez à la prochaine personne qui va devoir lire et comprendre vos commandes.</span><span class="sxs-lookup"><span data-stu-id="df76f-197">Think about the next person that has to read and understand your commands.</span></span> <span data-ttu-id="df76f-198">Ce sera peut-être vous.</span><span class="sxs-lookup"><span data-stu-id="df76f-198">It could be you.</span></span> <span data-ttu-id="df76f-199">Vos collègues et vous-même vous en féliciterez.</span><span class="sxs-lookup"><span data-stu-id="df76f-199">Your coworkers and future self will thank you.</span></span>

<span data-ttu-id="df76f-200">Essayez d’exécuter les commandes suivantes dans la console PowerShell de l’ordinateur de votre environnement lab Windows 10.</span><span class="sxs-lookup"><span data-stu-id="df76f-200">Try running the following commands in the PowerShell console on your Windows 10 lab environment computer.</span></span>

```powershell
Get-Help -Name Get-Help -Full
help -Name Get-Help -Full
help Get-Help -Full
```

<span data-ttu-id="df76f-201">Après les avoir exécutées sur l’ordinateur de votre environnement lab Windows 10, avez-vous remarqué des différences par rapport à la sortie des commandes listées précédemment ?</span><span class="sxs-lookup"><span data-stu-id="df76f-201">Did you notice any differences in the output from the previously listed commands when you ran them on your Windows 10 lab environment computer?</span></span>

<span data-ttu-id="df76f-202">Il n’y a pas de différences hormis le fait que les deux dernières options retournent les résultats une page à la fois.</span><span class="sxs-lookup"><span data-stu-id="df76f-202">There aren't any differences other than the last two options return the results one page at a time.</span></span>
<span data-ttu-id="df76f-203">Quand la fonction `Help` est utilisée, la <kbd>barre d’espace</kbd> permet d’afficher la page de contenu suivante, et <kbd>Ctrl</kbd>+<kbd>C</kbd> annule les commandes qui s’exécutent dans la console PowerShell.</span><span class="sxs-lookup"><span data-stu-id="df76f-203">The <kbd>spacebar</kbd> is used to display the next page of content when using the `Help` function and <kbd>Ctrl</kbd>+<kbd>C</kbd> cancels commands that are running in the PowerShell console.</span></span>

<span data-ttu-id="df76f-204">Le premier exemple fait appel à l’applet de commande `Get-Help`, le deuxième utilise la fonction `Help` et le troisième omet le paramètre **Name** quand la fonction `Help` est utilisée.</span><span class="sxs-lookup"><span data-stu-id="df76f-204">The first example uses the `Get-Help` cmdlet, the second uses the `Help` function, and the third omits the **Name** parameter when using the `Help` function.</span></span> <span data-ttu-id="df76f-205">**Name** est un paramètre positionnel qui est utilisé de façon positionnelle dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="df76f-205">**Name** is a positional parameter and it's being used positionally in that example.</span></span> <span data-ttu-id="df76f-206">Cela signifie que la valeur peut être spécifiée sans indiquer le nom du paramètre, du moment que la valeur proprement dite est spécifiée au bon endroit.</span><span class="sxs-lookup"><span data-stu-id="df76f-206">This means the value can be specified without specifying the parameter name, as long as the value itself is specified in the correct position.</span></span> <span data-ttu-id="df76f-207">Comment savoir à quel endroit spécifier la valeur ?</span><span class="sxs-lookup"><span data-stu-id="df76f-207">How did I know what position to specify the value in?</span></span> <span data-ttu-id="df76f-208">En lisant l’aide qui est illustrée dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="df76f-208">By reading the help as shown in the following example.</span></span>

```powershell
help Get-Help -Parameter Name
```

```Output
-Name <String>
    Gets help about the specified command or concept. Enter the name of a cmdlet, function,
    provider, script, or workflow, such as Get-Member, a conceptual article name, such as
    about_Objects, or an alias, such as ls. Wildcard characters are permitted in cmdlet and
    provider names, but you can't use wildcard characters to find the names of function help and
    script help articles.

    To get help for a script that isn't located in a path that's listed in the $env:Path
    environment variable, type the script's path and file name.

    If you enter the exact name of a help article, Get-Help displays the article contents.

    If you enter a word or word pattern that appears in several help article titles, Get-Help
    displays a list of the matching titles.

    If you enter a word that doesn't match any help article titles, Get-Help displays a list of
    articles that include that word in their contents.

    The names of conceptual articles, such as about_Objects, must be entered in English, even in
    non-English versions of PowerShell.

    Required?                    false
    Position?                    0
    Default value                None
    Accept pipeline input?       True (ByPropertyName)
    Accept wildcard characters?  true
```

<span data-ttu-id="df76f-209">Notez que dans l’exemple précédent, le paramètre **Parameter** a été utilisé avec la fonction Help pour retourner uniquement les informations de la rubrique d’aide se rapportant au paramètre **Name**.</span><span class="sxs-lookup"><span data-stu-id="df76f-209">Notice that in the previous example, the **Parameter** parameter was used with the Help function to only return information from the help topic for the **Name** parameter.</span></span> <span data-ttu-id="df76f-210">C’est bien plus simple que d’essayer de passer au crible une rubrique d’aide d’une centaine de pages.</span><span class="sxs-lookup"><span data-stu-id="df76f-210">This is much more concise than trying to manually sift through what sometimes seems like a hundred page help topic.</span></span>

<span data-ttu-id="df76f-211">Sur la base de ces résultats, vous pouvez voir que le paramètre **Name** est positionnel et qu’il doit être spécifié à la position zéro (première position) quand il est utilisé de façon positionnelle.</span><span class="sxs-lookup"><span data-stu-id="df76f-211">Based on those results, you can see that the **Name** parameter is positional and must be specified in position zero (the first position) when used positionally.</span></span> <span data-ttu-id="df76f-212">L’ordre dans lequel les paramètres sont spécifiés n’a pas d’importance si le nom du paramètre est spécifié.</span><span class="sxs-lookup"><span data-stu-id="df76f-212">The order that parameters are specified in doesn't matter if the parameter name is specified.</span></span>

<span data-ttu-id="df76f-213">Un autre point important à noter est que le paramètre **Name** attend une valeur sous la forme d’une chaîne unique, ce qui est indiqué par `<String>`.</span><span class="sxs-lookup"><span data-stu-id="df76f-213">One other important piece of information is that the **Name** parameter expects the datatype for its value to be a single string, which is denoted by `<String>`.</span></span> <span data-ttu-id="df76f-214">S’il acceptait plusieurs chaînes, le type de données indiqué serait `<String[]>`.</span><span class="sxs-lookup"><span data-stu-id="df76f-214">If it accepted multiple strings, the datatype would be listed as `<String[]>`.</span></span>

<span data-ttu-id="df76f-215">Parfois, il n’est pas utile d’afficher l’intégralité de la rubrique d’aide d’une commande.</span><span class="sxs-lookup"><span data-stu-id="df76f-215">Sometimes you simply don't want to display the entire help topic for a command.</span></span> <span data-ttu-id="df76f-216">Avec `Get-Help` ou `Help`, il est possible de spécifier plusieurs autres paramètres, en plus de **Full**.</span><span class="sxs-lookup"><span data-stu-id="df76f-216">There are a number of other parameters besides **Full** that can be specified with `Get-Help` or `Help`.</span></span> <span data-ttu-id="df76f-217">Essayez d’exécuter les commandes suivantes sur l’ordinateur de votre environnement lab Windows 10 :</span><span class="sxs-lookup"><span data-stu-id="df76f-217">Try running the following commands on your Windows 10 lab environment computer:</span></span>

```powershell
Get-Help -Name Get-Command -Full
Get-Help -Name Get-Command -Detailed
Get-Help -Name Get-Command -Examples
Get-Help -Name Get-Command -Online
Get-Help -Name Get-Command -Parameter Noun
Get-Help -Name Get-Command -ShowWindow
```

<span data-ttu-id="df76f-218">En général, j’utilise `help <command name>` avec le paramètre **Full** ou **Online**.</span><span class="sxs-lookup"><span data-stu-id="df76f-218">I typically use `help <command name>` with the **Full** or **Online** parameter.</span></span> <span data-ttu-id="df76f-219">Si je suis intéressé uniquement par les exemples, j’utilise le paramètre **Examples**  ; si je suis intéressé uniquement par un paramètre spécifique, j’utilise le paramètre **Parameter**.</span><span class="sxs-lookup"><span data-stu-id="df76f-219">If I'm only interested in the examples, I'll use the **Examples** parameter and if I'm only interested in a specific parameter, I'll use the **Parameter** parameter.</span></span> <span data-ttu-id="df76f-220">Le paramètre **ShowWindow** ouvre la rubrique d’aide dans une fenêtre de recherche distincte qui peut être affichée sur un autre écran, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="df76f-220">The **ShowWindow** parameter opens the help topic in a separate searchable window that can be placed on a different monitor if you have multiple monitors.</span></span> <span data-ttu-id="df76f-221">J’ai évité le paramètre **ShowWindow** , car un bogue connu l’empêche d’afficher l’intégralité de la rubrique d’aide.</span><span class="sxs-lookup"><span data-stu-id="df76f-221">I've avoided the **ShowWindow** parameter because there's a known bug where it doesn't display the entire help topic.</span></span>

<span data-ttu-id="df76f-222">Si vous souhaitez afficher l’aide dans une fenêtre distincte, il est préférable d’utiliser le paramètre **Online** ou **Full** et de canaliser les résultats vers `Out-GridView`, comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="df76f-222">If you want help in a separate window, my recommendation is to either use the **Online** parameter or use the **Full** parameter and pipe the results to `Out-GridView`, as shown in the following example.</span></span>

```powershell
help Get-Command -Full | Out-GridView
```

<span data-ttu-id="df76f-223">L’applet de commande `Out-GridView` et le paramètre **ShowWindow** de l’applet de commande `Get-Help` nécessitent un système d’exploitation doté d’une interface graphique utilisateur (GUI).</span><span class="sxs-lookup"><span data-stu-id="df76f-223">Both the `Out-GridView` cmdlet and the **ShowWindow** parameter of the `Get-Help` cmdlet require an operating system with a GUI (Graphical User Interface).</span></span> <span data-ttu-id="df76f-224">Si vous tentez de les utiliser sur un système Windows Server installé avec l’option d’installation Server Core (sans interface graphique), ils généreront un message d’erreur.</span><span class="sxs-lookup"><span data-stu-id="df76f-224">They will generate an error message if you attempt to use either of them on Windows Server that's been installed using the server core (no-GUI) installation option.</span></span>

<span data-ttu-id="df76f-225">Pour rechercher des commandes à l’aide de `Get-Help`, utilisez le caractère générique `*` (astérisque) avec le paramètre **Name**.</span><span class="sxs-lookup"><span data-stu-id="df76f-225">To use `Get-Help` to find commands, use the asterisk (`*`) wildcard character with the **Name** parameter.</span></span> <span data-ttu-id="df76f-226">Spécifiez la valeur du paramètre **Name** avec le terme que vous recherchez dans les noms de commandes, comme l’illustre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="df76f-226">Specify a term that you're searching for commands on as the value for the **Name** parameter as shown in the following example.</span></span>

```powershell
help *process*
```

```Output
Name                              Category  Module                    Synopsis
----                              --------  ------                    --------
Enter-PSHostProcess               Cmdlet    Microsoft.PowerShell.Core Connects to and ...
Exit-PSHostProcess                Cmdlet    Microsoft.PowerShell.Core Closes an intera...
Get-PSHostProcessInfo             Cmdlet    Microsoft.PowerShell.Core
Debug-Process                     Cmdlet    Microsoft.PowerShell.M... Debugs one or mo...
Get-Process                       Cmdlet    Microsoft.PowerShell.M... Gets the process...
Start-Process                     Cmdlet    Microsoft.PowerShell.M... Starts one or mo...
Stop-Process                      Cmdlet    Microsoft.PowerShell.M... Stops one or mor...
Wait-Process                      Cmdlet    Microsoft.PowerShell.M... Waits for the pr...
Get-AppvVirtualProcess            Function  AppvClient                ...
Start-AppvVirtualProcess          Function  AppvClient                ...
```

<span data-ttu-id="df76f-227">Dans l’exemple précédent, les caractères génériques `*` ne sont pas obligatoires et vous obtenez les mêmes résultats si vous les omettez.</span><span class="sxs-lookup"><span data-stu-id="df76f-227">In the previous example, the `*` wildcard characters are not required and omitting them produces the same result.</span></span> <span data-ttu-id="df76f-228">`Get-Help` ajoute automatiquement les caractères génériques en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="df76f-228">`Get-Help` automatically adds the wildcard characters behind the scenes.</span></span>

```powershell
help process
```

<span data-ttu-id="df76f-229">La commande précédente produit les mêmes résultats que si le caractère générique `*` est spécifié de part et d’autre de « process ».</span><span class="sxs-lookup"><span data-stu-id="df76f-229">The previous command produces the same results as specifying the `*` wildcard character on each end of process.</span></span>

<span data-ttu-id="df76f-230">Je préfère les ajouter, car c’est l’option qui fonctionne toujours et avec constance.</span><span class="sxs-lookup"><span data-stu-id="df76f-230">I prefer to add them since that's the option that always works consistently.</span></span> <span data-ttu-id="df76f-231">En revanche, ils sont nécessaires dans certains scénarios, mais pas dans d’autres.</span><span class="sxs-lookup"><span data-stu-id="df76f-231">Otherwise, they are required in certain scenarios and not others.</span></span> <span data-ttu-id="df76f-232">Dès lors que vous ajoutez un caractère générique au milieu de la valeur, ils ne sont plus ajoutés automatiquement en arrière-plan à la valeur que vous spécifiez.</span><span class="sxs-lookup"><span data-stu-id="df76f-232">As soon as you add a wildcard character in the middle of the value, they're no longer automatically added behind the scenes to the value you specified.</span></span>

```powershell
help pr*cess
```

<span data-ttu-id="df76f-233">Aucune valeur n’est retournée par cette commande, à moins que le caractère générique `*` soit ajouté au début, à la fin ou de part et d’autre de `pr*cess`.</span><span class="sxs-lookup"><span data-stu-id="df76f-233">No results are returned by that command unless the `*` wildcard character is added to the beginning, end, or both the beginning and end of `pr*cess`.</span></span>

<span data-ttu-id="df76f-234">Si la valeur que vous avez spécifiée commence par un tiret, une erreur est générée, car PowerShell l’interprète comme un nom de paramètre. Or, il n’existe pas de nom de paramètre pour l’applet de commande `Get-Help`.</span><span class="sxs-lookup"><span data-stu-id="df76f-234">If the value you specified begins with a dash, then an error is generated because PowerShell interprets it as a parameter name and no such parameter name exists for the `Get-Help` cmdlet.</span></span>

```powershell
help -process
```

<span data-ttu-id="df76f-235">Si vous essayez de rechercher des commandes qui se terminent par `-process`, il vous suffit d’ajouter le caractère générique `*` au début de la valeur.</span><span class="sxs-lookup"><span data-stu-id="df76f-235">If what you're attempting to look for are commands that end with `-process`, you only need to add the `*` wildcard character to the beginning of the value.</span></span>

```powershell
help *-process
```

<span data-ttu-id="df76f-236">Quand il s’agit de rechercher des commandes PowerShell avec `Get-Help`, soyez un peu plus vague dans vos recherches et moins précis.</span><span class="sxs-lookup"><span data-stu-id="df76f-236">When searching for PowerShell commands with `Get-Help`, you want to be a little more vague instead of being too specific with what you're searching for.</span></span>

<span data-ttu-id="df76f-237">Dans la recherche précédente qui portait sur le terme `process`, seules les commandes dont le nom contenait `process` ont été trouvées et aucun autre résultat n’a été retourné.</span><span class="sxs-lookup"><span data-stu-id="df76f-237">Searching for `process` earlier found only commands that contained `process` in the name of the command and returned only those results.</span></span> <span data-ttu-id="df76f-238">Avec `Get-Help`, le terme de recherche `processes` ne correspond à aucun nom de commande. De ce fait, la recherche porte sur chaque rubrique d’aide PowerShell de votre système et retourne toutes les correspondances trouvées.</span><span class="sxs-lookup"><span data-stu-id="df76f-238">When `Get-Help` is used to search for `processes`, it doesn't find any matches for command names, so it performs a search of every help topic in PowerShell on your system and returns any matches it finds.</span></span> <span data-ttu-id="df76f-239">Le nombre de résultats retournés est alors immense.</span><span class="sxs-lookup"><span data-stu-id="df76f-239">This causes it to return an enormous number of results.</span></span>

```powershell
Get-Help processes
```

```Output
Name                              Category  Module                    Synopsis
----                              --------  ------                    --------
Disconnect-PSSession              Cmdlet    Microsoft.PowerShell.Core Disconnects from...
Enter-PSHostProcess               Cmdlet    Microsoft.PowerShell.Core Connects to and ...
ForEach-Object                    Cmdlet    Microsoft.PowerShell.Core Performs an oper...
Get-PSSessionConfiguration        Cmdlet    Microsoft.PowerShell.Core Gets the registe...
New-PSTransportOption             Cmdlet    Microsoft.PowerShell.Core Creates an objec...
Out-Host                          Cmdlet    Microsoft.PowerShell.Core Sends output to ...
Where-Object                      Cmdlet    Microsoft.PowerShell.Core Selects objects ...
Clear-Variable                    Cmdlet    Microsoft.PowerShell.U... Deletes the valu...
Compare-Object                    Cmdlet    Microsoft.PowerShell.U... Compares two set...
Convert-String                    Cmdlet    Microsoft.PowerShell.U... Formats a string...
ConvertFrom-Csv                   Cmdlet    Microsoft.PowerShell.U... Converts object ...
ConvertTo-Html                    Cmdlet    Microsoft.PowerShell.U... Converts Microso...
ConvertTo-Xml                     Cmdlet    Microsoft.PowerShell.U... Creates an XML-b...
Debug-Runspace                    Cmdlet    Microsoft.PowerShell.U... Starts an intera...
Export-Csv                        Cmdlet    Microsoft.PowerShell.U... Converts objects...
Export-FormatData                 Cmdlet    Microsoft.PowerShell.U... Saves formatting...
Format-List                       Cmdlet    Microsoft.PowerShell.U... Formats the outp...
Format-Table                      Cmdlet    Microsoft.PowerShell.U... Formats the outp...
Get-Random                        Cmdlet    Microsoft.PowerShell.U... Gets a random nu...
Get-Unique                        Cmdlet    Microsoft.PowerShell.U... Returns unique i...
Group-Object                      Cmdlet    Microsoft.PowerShell.U... Groups objects t...
Import-Clixml                     Cmdlet    Microsoft.PowerShell.U... Imports a CLIXML...
Import-Csv                        Cmdlet    Microsoft.PowerShell.U... Creates table-li...
Measure-Object                    Cmdlet    Microsoft.PowerShell.U... Calculates the n...
Out-File                          Cmdlet    Microsoft.PowerShell.U... Sends output to ...
Out-GridView                      Cmdlet    Microsoft.PowerShell.U... Sends output to ...
Select-Object                     Cmdlet    Microsoft.PowerShell.U... Selects objects ...
Set-Variable                      Cmdlet    Microsoft.PowerShell.U... Sets the value o...
Sort-Object                       Cmdlet    Microsoft.PowerShell.U... Sorts objects by...
Tee-Object                        Cmdlet    Microsoft.PowerShell.U... Saves command ou...
Trace-Command                     Cmdlet    Microsoft.PowerShell.U... Configures and s...
Write-Output                      Cmdlet    Microsoft.PowerShell.U... Sends the specif...
Debug-Process                     Cmdlet    Microsoft.PowerShell.M... Debugs one or mo...
Get-Process                       Cmdlet    Microsoft.PowerShell.M... Gets the process...
Get-WmiObject                     Cmdlet    Microsoft.PowerShell.M... Gets instances o...
Start-Process                     Cmdlet    Microsoft.PowerShell.M... Starts one or mo...
Stop-Process                      Cmdlet    Microsoft.PowerShell.M... Stops one or mor...
Wait-Process                      Cmdlet    Microsoft.PowerShell.M... Waits for the pr...
Get-Counter                       Cmdlet    Microsoft.PowerShell.D... Gets performance...
Invoke-WSManAction                Cmdlet    Microsoft.WSMan.Manage... Invokes an actio...
Remove-WSManInstance              Cmdlet    Microsoft.WSMan.Manage... Deletes a manage...
Get-WSManInstance                 Cmdlet    Microsoft.WSMan.Manage... Displays managem...
New-WSManInstance                 Cmdlet    Microsoft.WSMan.Manage... Creates a new in...
Set-WSManInstance                 Cmdlet    Microsoft.WSMan.Manage... Modifies the man...
about_Arithmetic_Operators        HelpFile                            Describes the op...
about_Arrays                      HelpFile                            Describes arrays...
about_Debuggers                   HelpFile                            Describes the Wi...
about_Execution_Policies          HelpFile                            Describes the Wi...
about_ForEach-Parallel            HelpFile                            Describes the Fo...
about_Foreach                     HelpFile                            Describes a lang...
about_Functions                   HelpFile                            Describes how to...
about_Language_Keywords           HelpFile                            Describes the ke...
about_Methods                     HelpFile                            Describes how to...
about_Objects                     HelpFile                            Provides essenti...
about_Parallel                    HelpFile                            Describes the Pa...
about_Pipelines                   HelpFile                            Combining comman...
about_Preference_Variables        HelpFile                            Variables that c...
about_Remote                      HelpFile                            Describes how to...
about_Remote_Output               HelpFile                            Describes how to...
about_Sequence                    HelpFile                            Describes the Se...
about_Session_Configuration_Files HelpFile                            Describes sessio...
about_Variables                   HelpFile                            Describes how va...
about_Windows_PowerShell_5.0      HelpFile                            Describes new fe...
about_WQL                         HelpFile                            Describes WMI Qu...
about_WS-Management_Cmdlets       HelpFile                            Provides an over...
about_ForEach-Parallel            HelpFile                            Describes the Fo...
about_Parallel                    HelpFile                            Describes the Pa...
about_Sequence                    HelpFile                            Describes the Se...
```

<span data-ttu-id="df76f-240">La recherche avec `Help` a retourné 10 résultats pour le terme `process` et 68 résultats pour le terme `processes`.</span><span class="sxs-lookup"><span data-stu-id="df76f-240">Using `Help` to search for `process` returned 10 results and using it to search for `processes` returned 68 results.</span></span> <span data-ttu-id="df76f-241">Si un seul résultat est trouvé, la rubrique d’aide proprement dite s’affiche à la place de la liste de commandes.</span><span class="sxs-lookup"><span data-stu-id="df76f-241">If only one result is found, the help topic itself will be displayed instead of a list of commands.</span></span>

```powershell
get-help *hotfix*
```

```Output
NAME
    Get-HotFix

SYNOPSIS
    Gets the hotfixes that have been applied to the local and remote computers.


SYNTAX
    Get-HotFix [-ComputerName <String[]>] [-Credential <PSCredential>] [-Description
    <String[]>] [<CommonParameters>]

    Get-HotFix [[-Id] <String[]>] [-ComputerName <String[]>] [-Credential
    <PSCredential>] [<CommonParameters>]


DESCRIPTION
    The Get-Hotfix cmdlet gets hotfixes (also called updates) that have been installed
    on either the local computer (or on specified remote computers) by Windows Update,
    Microsoft Update, or Windows Server Update Services; the cmdlet also gets hotfixes
    or updates that have been installed manually by users.


RELATED LINKS
    Online Version: http://go.microsoft.com/fwlink/?LinkId=821586
    Win32_QuickFixEngineering http://go.microsoft.com/fwlink/?LinkID=145071
    Get-ComputerRestorePoint
    Add-Content

REMARKS
    To see the examples, type: "get-help Get-HotFix -examples".
    For more information, type: "get-help Get-HotFix -detailed".
    For technical information, type: "get-help Get-HotFix -full".
    For online help, type: "get-help Get-HotFix -online"
```

<span data-ttu-id="df76f-242">Maintenant, nous allons tordre le cou à une fausse idée selon laquelle `Help` dans PowerShell peut trouver uniquement les commandes associées à des rubriques d’aide.</span><span class="sxs-lookup"><span data-stu-id="df76f-242">Now to debunk the myth that `Help` in PowerShell can only find commands that have help topics.</span></span>

```powershell
help *more*
```

```Output
NAME
    more

SYNTAX
    more [[-paths] <string[]>]


ALIASES
    None


REMARKS
    None
```

<span data-ttu-id="df76f-243">À noter que dans l’exemple précédent, il n’existe pas de rubrique d’aide pour `more` alors que ce terme a été trouvé par le système `Help` dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="df76f-243">Notice in the previous example that `more` doesn't have a help topic, yet the `Help` system in PowerShell was able to find it.</span></span> <span data-ttu-id="df76f-244">Il a trouvé une seule correspondance et a retourné les informations de syntaxe de base qui s’affichent quand une commande n’a pas de rubrique d’aide.</span><span class="sxs-lookup"><span data-stu-id="df76f-244">It only found one match and returned the basic syntax information that you'll see when a command doesn't have a help topic.</span></span>

<span data-ttu-id="df76f-245">PowerShell contient de nombreuses rubriques d’aide conceptuelles (À propos de).</span><span class="sxs-lookup"><span data-stu-id="df76f-245">PowerShell contains numerous conceptual (About) help topics.</span></span> <span data-ttu-id="df76f-246">La commande suivante permet de retourner la liste de toutes les rubriques d’aide **À propos de** présentes sur votre système.</span><span class="sxs-lookup"><span data-stu-id="df76f-246">The following command can be used to return a list of all **About** help topics on your system.</span></span>

```powershell
help About_*
```

<span data-ttu-id="df76f-247">En limitant les résultats à une seule rubrique d’aide À propos de, ce n’est pas la liste qui est retournée mais bien la rubrique d’aide qui s’affiche.</span><span class="sxs-lookup"><span data-stu-id="df76f-247">Limiting the results to one single About help topic displays the actual help topic instead of returning a list.</span></span>

```powershell
help about_Updatable_Help
```

<span data-ttu-id="df76f-248">Le système d’aide de PowerShell doit être mis à jour pour que les rubriques d’aide **À propos de** soient présentes.</span><span class="sxs-lookup"><span data-stu-id="df76f-248">The help system in PowerShell has to be updated in order for the **About** help topics to be present.</span></span> <span data-ttu-id="df76f-249">Si, pour une raison ou une autre, la mise à jour initiale du système d’aide échoue sur votre ordinateur, les fichiers ne sont pas disponibles tant que l’applet de commande `Update-Help` n’est pas exécutée avec succès.</span><span class="sxs-lookup"><span data-stu-id="df76f-249">If for some reason the initial update of the help system failed on your computer, the files will not be available until the `Update-Help` cmdlet has been run successfully.</span></span>

## <a name="get-command"></a><span data-ttu-id="df76f-250">Get-Command</span><span class="sxs-lookup"><span data-stu-id="df76f-250">Get-Command</span></span>

<span data-ttu-id="df76f-251">`Get-Command` vise à vous aider à localiser les commandes.</span><span class="sxs-lookup"><span data-stu-id="df76f-251">`Get-Command` is designed to help you locate commands.</span></span> <span data-ttu-id="df76f-252">L’exécution de `Get-Command` sans aucun paramètre retourne la liste de toutes les commandes de votre système.</span><span class="sxs-lookup"><span data-stu-id="df76f-252">Running `Get-Command` without any parameters returns a list of all the commands on your system.</span></span> <span data-ttu-id="df76f-253">L’exemple suivant vous montre comment l’applet de commande `Get-Command` est utilisée pour identifier les commandes existantes qui fonctionnent avec des processus :</span><span class="sxs-lookup"><span data-stu-id="df76f-253">The following example demonstrates using the `Get-Command` cmdlet to determine what commands exist for working with processes:</span></span>

```powershell
Get-Command -Noun Process
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Debug-Process                                      3.1.0.0    Microsof...
Cmdlet          Get-Process                                        3.1.0.0    Microsof...
Cmdlet          Start-Process                                      3.1.0.0    Microsof...
Cmdlet          Stop-Process                                       3.1.0.0    Microsof...
Cmdlet          Wait-Process                                       3.1.0.0    Microsof...
```

<span data-ttu-id="df76f-254">Notez que dans l’exemple précédent où `Get-Command` est exécuté, le paramètre **Noun** est utilisé et `Process` est spécifié comme valeur du paramètre **Noun**.</span><span class="sxs-lookup"><span data-stu-id="df76f-254">Notice in the previous example where `Get-Command` was run, the **Noun** parameter is used and `Process` is specified as the value for the **Noun** parameter.</span></span> <span data-ttu-id="df76f-255">Et si vous n’aviez pas su utiliser l’applet de commande `Get-Command` ?</span><span class="sxs-lookup"><span data-stu-id="df76f-255">What if you didn't know how to use the `Get-Command` cmdlet?</span></span> <span data-ttu-id="df76f-256">Vous auriez pu utiliser `Get-Help` pour afficher la rubrique d’aide pour `Get-Command`.</span><span class="sxs-lookup"><span data-stu-id="df76f-256">You could use `Get-Help` to display the help topic for `Get-Command`.</span></span>

<span data-ttu-id="df76f-257">Les paramètres **Name** , **Noun** et **Verb** acceptent les caractères génériques.</span><span class="sxs-lookup"><span data-stu-id="df76f-257">The **Name** , **Noun** , and **Verb** parameters accept wildcards.</span></span> <span data-ttu-id="df76f-258">Dans l’exemple suivant, des caractères génériques sont utilisés avec le paramètre **Name**  :</span><span class="sxs-lookup"><span data-stu-id="df76f-258">The following example shows wildcards being used with the **Name** parameter:</span></span>

```Output
Get-Command -Name *service*
```

```powershell
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Function        Get-NetFirewallServiceFilter                       2.0.0.0    NetSecurity
Function        Set-NetFirewallServiceFilter                       2.0.0.0    NetSecurity
Cmdlet          Get-Service                                        3.1.0.0    Microsof...
Cmdlet          New-Service                                        3.1.0.0    Microsof...
Cmdlet          New-WebServiceProxy                                3.1.0.0    Microsof...
Cmdlet          Restart-Service                                    3.1.0.0    Microsof...
Cmdlet          Resume-Service                                     3.1.0.0    Microsof...
Cmdlet          Set-Service                                        3.1.0.0    Microsof...
Cmdlet          Start-Service                                      3.1.0.0    Microsof...
Cmdlet          Stop-Service                                       3.1.0.0    Microsof...
Cmdlet          Suspend-Service                                    3.1.0.0    Microsof...
Application     AgentService.exe                                   10.0.14... C:\Windo...
Application     SensorDataService.exe                              10.0.14... C:\Windo...
Application     services.exe                                       10.0.14... C:\Windo...
Application     services.msc                                       0.0.0.0    C:\Windo...
Application     TieringEngineService.exe                           10.0.14... C:\Windo...
```

<span data-ttu-id="df76f-259">Je ne suis pas très favorable à l’utilisation de caractères génériques avec le paramètre **Name** de `Get-Command`, car celui-ci retourne aussi les fichiers exécutables qui ne sont pas des commandes PowerShell natives.</span><span class="sxs-lookup"><span data-stu-id="df76f-259">I'm not a fan of using wildcards with the **Name** parameter of `Get-Command` since it also returns executable files that are not native PowerShell commands.</span></span>

<span data-ttu-id="df76f-260">Si vous envisagez d’utiliser des caractères génériques avec le paramètre **Name** , je vous recommande de limiter les résultats avec le paramètre **CommandType**.</span><span class="sxs-lookup"><span data-stu-id="df76f-260">If you are going to use wildcard characters with the **Name** parameter, I recommend limiting the results with the **CommandType** parameter.</span></span>

```powershell
Get-Command -Name *service* -CommandType Cmdlet, Function, Alias
```

<span data-ttu-id="df76f-261">Une meilleure option consiste à utiliser le paramètre **Verb** ou **Noun** ou les deux à la fois, car seules les commandes PowerShell comportent à la fois un verbe et un nom.</span><span class="sxs-lookup"><span data-stu-id="df76f-261">A better option is to use either the **Verb** or **Noun** parameter or both of them since only PowerShell commands have both verbs and nouns.</span></span>

<span data-ttu-id="df76f-262">Vous avez trouvé des erreurs dans une rubrique d’aide ?</span><span class="sxs-lookup"><span data-stu-id="df76f-262">Found something wrong with a help topic?</span></span> <span data-ttu-id="df76f-263">La bonne nouvelle c’est que les rubriques d’aide de PowerShell sont désormais en open source et disponibles dans le dépôt [PowerShell-Docs][] sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="df76f-263">The good news is the help topics for PowerShell have been open-sourced and available in the [PowerShell-Docs][] repository on GitHub.</span></span> <span data-ttu-id="df76f-264">Apportez votre contribution en corrigeant les informations incorrectes non seulement pour vous-même, mais aussi pour tous les autres utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="df76f-264">Pay it forward by not only fixing the incorrect information for yourself, but everyone else as well.</span></span> <span data-ttu-id="df76f-265">Il vous suffit de dupliquer (fork) le dépôt de documentation PowerShell sur GitHub, de mettre à jour la rubrique d’aide, puis d’envoyer une demande de tirage (pull request).</span><span class="sxs-lookup"><span data-stu-id="df76f-265">Simply fork the PowerShell documentation repository on GitHub, update the help topic, and submit a pull request.</span></span>
<span data-ttu-id="df76f-266">Une fois la demande de tirage acceptée, la documentation corrigée est mise à la disposition de tous.</span><span class="sxs-lookup"><span data-stu-id="df76f-266">Once the pull request is accepted, the corrected documentation is available for everyone.</span></span>

## <a name="updating-help"></a><span data-ttu-id="df76f-267">Mise à jour de l’aide</span><span class="sxs-lookup"><span data-stu-id="df76f-267">Updating Help</span></span>

<span data-ttu-id="df76f-268">La copie locale des rubriques d’aide PowerShell a été mise à jour précédemment la première fois que de l’aide sur une commande a été demandée.</span><span class="sxs-lookup"><span data-stu-id="df76f-268">The local copy of the PowerShell help topics was previously updated the first-time help on a command was requested.</span></span> <span data-ttu-id="df76f-269">Il est recommandé de mettre à jour régulièrement le système d’aide, car le contenu de l’aide peut de temps à autre faire l’objet de mises à jour.</span><span class="sxs-lookup"><span data-stu-id="df76f-269">It's recommended to periodically update the help system because there can be updates to the help content from time to time.</span></span> <span data-ttu-id="df76f-270">La mise à jour des rubriques d’aide s’effectue à l’aide de l’applet de commande `Update-Help`.</span><span class="sxs-lookup"><span data-stu-id="df76f-270">The `Update-Help` cmdlet is used to update the help topics.</span></span>
<span data-ttu-id="df76f-271">Elle nécessite par défaut un accès à Internet et vous devez exécuter PowerShell avec une élévation de privilèges en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="df76f-271">It requires internet access by default and for you to be running PowerShell elevated as an administrator.</span></span>

```powershell
Update-Help
```

```Output
Update-Help : Failed to update Help for the module(s) 'BitsTransfer' with UI culture(s)
{en-US} : The value of the HelpInfoUri key in the module manifest must resolve to a
container or root URL on a website where the help files are stored. The HelpInfoUri
'https://technet.microsoft.com/en-us/library/dd819413.aspx' does not resolve to a
container.
At line:1 char:1
+ Update-Help
+
    + CategoryInfo          : InvalidOperation: (:) [Update-Help], Exception
    + FullyQualifiedErrorId : InvalidHelpInfoUri,Microsoft.PowerShell.Commands.UpdateHel
   pCommand

Update-Help : Failed to update Help for the module(s) 'NetworkControllerDiagnostics,
StorageReplica' with UI culture(s) {en-US} : Unable to retrieve the HelpInfo XML file
for UI culture en-US. Make sure the HelpInfoUri property in the module manifest is valid
or check your network connection and then try the command again.
At line:1 char:1
+ Update-Help
+
    + CategoryInfo          : ResourceUnavailable: (:) [Update-Help], Exception
    + FullyQualifiedErrorId : UnableToRetrieveHelpInfoXml,Microsoft.PowerShell.Commands.
   UpdateHelpCommand
```

<span data-ttu-id="df76f-272">Des erreurs ont été retournées par deux modules, ce qui n’est pas rare.</span><span class="sxs-lookup"><span data-stu-id="df76f-272">A couple of the modules returned errors, which is not uncommon.</span></span> <span data-ttu-id="df76f-273">Si l’ordinateur n’a pas accès à Internet, vous pouvez utiliser l’applet de commande `Save-Help` sur un autre ordinateur connecté à Internet de façon à enregistrer dans un premier temps les informations d’aide mises à jour sur un partage de fichiers de votre réseau. Ensuite, spécifiez cet emplacement réseau pour les rubriques d’aide avec le paramètre **SourcePath** de `Update-Help`.</span><span class="sxs-lookup"><span data-stu-id="df76f-273">If the machine didn't have internet access, you could use the `Save-Help` cmdlet on another machine that does have internet access to first save the updated help information to a file share on your network and then use the **SourcePath** parameter of `Update-Help` to specify this network location for the help topics.</span></span>

<span data-ttu-id="df76f-274">Envisagez de configurer une tâche planifiée ou d’ajouter une logique à votre script de profil dans PowerShell pour mettre régulièrement à jour le contenu de l’aide sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="df76f-274">Consider setting up a scheduled task or adding some logic to your profile script in PowerShell to periodically update the help content on your computer.</span></span> <span data-ttu-id="df76f-275">Les scripts de profil seront abordés dans un prochain chapitre.</span><span class="sxs-lookup"><span data-stu-id="df76f-275">Profile scripts will be discussed in an upcoming chapter.</span></span>

## <a name="summary"></a><span data-ttu-id="df76f-276">Résumé</span><span class="sxs-lookup"><span data-stu-id="df76f-276">Summary</span></span>

<span data-ttu-id="df76f-277">Dans ce chapitre, vous avez appris à rechercher les commandes avec `Get-Help` et `Get-Command`.</span><span class="sxs-lookup"><span data-stu-id="df76f-277">In this chapter you've learned how to find commands with both `Get-Help` and `Get-Command`.</span></span> <span data-ttu-id="df76f-278">Vous avez appris à utiliser le système d’aide pour savoir comment utiliser les commandes une fois que vous les avez trouvées.</span><span class="sxs-lookup"><span data-stu-id="df76f-278">You've learned how to use the help system to figure out how to use commands once you find them.</span></span> <span data-ttu-id="df76f-279">Vous avez aussi découvert comment mettre à jour le contenu des rubriques d’aide quand des mises à jour sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="df76f-279">You've also learned how to update the content of the help topics when updates are available.</span></span>

<span data-ttu-id="df76f-280">Je vous lance le défi d’apprendre une commande PowerShell par jour.</span><span class="sxs-lookup"><span data-stu-id="df76f-280">My challenge to you is to learn a PowerShell command a day.</span></span>

```powershell
Get-Command | Get-Random | Get-Help -Full
```

## <a name="review"></a><span data-ttu-id="df76f-281">Révision</span><span class="sxs-lookup"><span data-stu-id="df76f-281">Review</span></span>

1. <span data-ttu-id="df76f-282">Le paramètre **DisplayName** de `Get-Service` est-il positionnel ?</span><span class="sxs-lookup"><span data-stu-id="df76f-282">Is the **DisplayName** parameter of `Get-Service` positional?</span></span>
1. <span data-ttu-id="df76f-283">Combien de jeux de paramètres compte l’applet de commande `Get-Process` ?</span><span class="sxs-lookup"><span data-stu-id="df76f-283">How many parameter sets does the `Get-Process` cmdlet have?</span></span>
1. <span data-ttu-id="df76f-284">Quelles sont les commandes PowerShell qui peuvent fonctionner avec les journaux des événements ?</span><span class="sxs-lookup"><span data-stu-id="df76f-284">What PowerShell commands exist for working with event logs?</span></span>
1. <span data-ttu-id="df76f-285">Quelle est la commande PowerShell qui permet de retourner la liste des processus PowerShell qui s’exécutent sur votre ordinateur ?</span><span class="sxs-lookup"><span data-stu-id="df76f-285">What is the PowerShell command for returning a list of PowerShell processes running on your computer?</span></span>
1. <span data-ttu-id="df76f-286">Comment mettre à jour le contenu de l’aide PowerShell qui est stocké sur votre ordinateur ?</span><span class="sxs-lookup"><span data-stu-id="df76f-286">How do you update the PowerShell help content that's stored on your computer?</span></span>

## <a name="recommended-reading"></a><span data-ttu-id="df76f-287">Lecture recommandée</span><span class="sxs-lookup"><span data-stu-id="df76f-287">Recommended Reading</span></span>

<span data-ttu-id="df76f-288">Si vous souhaitez en savoir plus sur les sujets abordés dans ce chapitre, je vous conseille de lire les rubriques d’aide PowerShell suivantes.</span><span class="sxs-lookup"><span data-stu-id="df76f-288">If you want to know more information about the topics covered in this chapter, I recommend reading the following PowerShell help topics.</span></span>

- <span data-ttu-id="df76f-289">[Get-Help][]</span><span class="sxs-lookup"><span data-stu-id="df76f-289">[Get-Help][]</span></span>
- <span data-ttu-id="df76f-290">[Get-Command][]</span><span class="sxs-lookup"><span data-stu-id="df76f-290">[Get-Command][]</span></span>
- <span data-ttu-id="df76f-291">[Update-Help][]</span><span class="sxs-lookup"><span data-stu-id="df76f-291">[Update-Help][]</span></span>
- <span data-ttu-id="df76f-292">[Save-Help][]</span><span class="sxs-lookup"><span data-stu-id="df76f-292">[Save-Help][]</span></span>
- <span data-ttu-id="df76f-293">[about_Updatable_Help][]</span><span class="sxs-lookup"><span data-stu-id="df76f-293">[about_Updatable_Help][]</span></span>
- <span data-ttu-id="df76f-294">[about_Command_Syntax][]</span><span class="sxs-lookup"><span data-stu-id="df76f-294">[about_Command_Syntax][]</span></span>

<span data-ttu-id="df76f-295">Dans le prochain chapitre, vous découvrirez l’applet de commande `Get-Member` ainsi que des objets, des propriétés et des méthodes.</span><span class="sxs-lookup"><span data-stu-id="df76f-295">In the next chapter, you'll learn about the `Get-Member` cmdlet as well as objects, properties, and methods.</span></span>

<!-- link references -->
[Get-Help]: /powershell/module/microsoft.powershell.core/get-help
[Get-Command]: /powershell/module/microsoft.powershell.core/get-command
[Update-Help]: /powershell/module/microsoft.powershell.core/update-help
[Save-Help]: /powershell/module/microsoft.powershell.core/save-help
[about_Updatable_Help]: /powershell/module/microsoft.powershell.core/about/about_updatable_help
[about_Command_Syntax]: /powershell/module/microsoft.powershell.core/about/about_command_syntax
[PowerShell-Docs]: https://github.com/powershell/powershell
[Annexe A]: appendix-a.md
[Appendix A]: appendix-a.md
