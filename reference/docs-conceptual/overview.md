---
ms.date: 05/22/2020
keywords: powershell,applet de commande
title: Qu’est-ce que PowerShell ?
description: Cet article présente l’environnement de script PowerShell et ses fonctionnalités.
ms.openlocfilehash: 91fc580af9a3adf43a24c40b4aaf3f1843882705
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500774"
---
# <a name="what-is-powershell"></a><span data-ttu-id="75400-104">Qu’est-ce que PowerShell ?</span><span class="sxs-lookup"><span data-stu-id="75400-104">What is PowerShell?</span></span>

<span data-ttu-id="75400-105">PowerShell est une infrastructure multiplateforme pour la gestion de la configuration et de l’automatisation des tâches, composée d’un interpréteur de commandes (shell) de ligne de commande et d’un langage de script.</span><span class="sxs-lookup"><span data-stu-id="75400-105">PowerShell is a cross-platform task automation and configuration management framework, consisting of a command-line shell and scripting language.</span></span> <span data-ttu-id="75400-106">Contrairement à la plupart des interpréteurs de commandes qui acceptent et retournent du texte, PowerShell est construit sur le .NET Common Language Runtime (CLR), et accepte et retourne des objets .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="75400-106">Unlike most shells, which accept and return text, PowerShell is built on top of the .NET Common Language Runtime (CLR), and accepts and returns .NET objects.</span></span> <span data-ttu-id="75400-107">Ce changement fondamental apporte de nouveaux outils et méthodes pour l’automatisation.</span><span class="sxs-lookup"><span data-stu-id="75400-107">This fundamental change brings entirely new tools and methods for automation.</span></span>

<!-- removing images until we can get replacements
:::row:::
   :::column span="":::
      Windows
      [![PowerShell on Windows](media/overview/windows-desktop-660.gif)](media/overview/windows-desktop.gif#lightbox)
      [Install on Windows](install/installing-powershell-core-on-windows.md)
   :::column-end:::
   :::column span="":::
      Linux
      [![PowerShell on Linux](media/overview/linux-desktop-660.gif)](media/overview/linux-desktop.gif#lightbox)
      [Install on Linux](install/installing-powershell-core-on-linux.md)
   :::column-end:::
   :::column span="":::
      macOS
      [![PowerShell on macOS](media/overview/macos-desktop-660.gif)](media/overview/macos-desktop.gif#lightbox)
      [Install on macOS](install/installing-powershell-core-on-macos.md)
   :::column-end:::
:::row-end:::
-->

## <a name="output-is-object-based"></a><span data-ttu-id="75400-108">La sortie est basée sur les objets</span><span class="sxs-lookup"><span data-stu-id="75400-108">Output is object-based</span></span>

<span data-ttu-id="75400-109">Contrairement aux interfaces de ligne de commande traditionnelles, les applets de commande PowerShell sont conçues pour traiter des objets.</span><span class="sxs-lookup"><span data-stu-id="75400-109">Unlike traditional command-line interfaces, PowerShell cmdlets are designed to deal with objects.</span></span>
<span data-ttu-id="75400-110">Un objet est une information structurée qui va au-delà de la seule chaîne de caractères s’affichant à l’écran.</span><span class="sxs-lookup"><span data-stu-id="75400-110">An object is structured information that is more than just the string of characters appearing on the screen.</span></span> <span data-ttu-id="75400-111">Une sortie de commande comporte toujours des informations supplémentaires que vous pouvez utiliser si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="75400-111">Command output always carries extra information that you can use if you need it.</span></span>

<span data-ttu-id="75400-112">Si vous avez utilisé des outils de traitement de texte pour traiter des données dans le passé, vous constaterez qu’ils se comportent différemment lorsqu’ils sont utilisés dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="75400-112">If you've used text-processing tools to process data in the past, you'll find that they behave differently when used in PowerShell.</span></span> <span data-ttu-id="75400-113">Dans la plupart des cas, vous n’avez pas besoin d’outils de traitement texte pour extraire des informations spécifiques.</span><span class="sxs-lookup"><span data-stu-id="75400-113">In most cases, you don't need text-processing tools to extract specific information.</span></span> <span data-ttu-id="75400-114">Vous accédez directement à des portions de données à l’aide de la syntaxe d’objet PowerShell standard.</span><span class="sxs-lookup"><span data-stu-id="75400-114">You directly access portions of the data using standard PowerShell object syntax.</span></span>

## <a name="the-command-family-is-extensible"></a><span data-ttu-id="75400-115">La famille de commandes est extensible</span><span class="sxs-lookup"><span data-stu-id="75400-115">The command family is extensible</span></span>

<span data-ttu-id="75400-116">Les interfaces comme `cmd.exe` n’offrent aucun moyen d’étendre directement le jeu de commandes intégré.</span><span class="sxs-lookup"><span data-stu-id="75400-116">Interfaces such as `cmd.exe` don't provide a way for you to directly extend the built-in command set.</span></span> <span data-ttu-id="75400-117">Vous pouvez créer des outils en ligne de commande externes qui s’exécutent dans `cmd.exe`.</span><span class="sxs-lookup"><span data-stu-id="75400-117">You can create external command-line tools that run in `cmd.exe`.</span></span> <span data-ttu-id="75400-118">Mais ces outils externes ne proposent pas de services comme l’intégration de l’aide.</span><span class="sxs-lookup"><span data-stu-id="75400-118">But these external tools don't have services, such as Help integration.</span></span> <span data-ttu-id="75400-119">`cmd.exe` ne sait pas automatiquement que ces outils externes sont des commandes valides.</span><span class="sxs-lookup"><span data-stu-id="75400-119">`cmd.exe` doesn't automatically know that these external tools are valid commands.</span></span>

<span data-ttu-id="75400-120">Dans PowerShell, les commandes sont appelées des _cmdlets_ .</span><span class="sxs-lookup"><span data-stu-id="75400-120">The commands in PowerShell are known as _cmdlets_ .</span></span> <span data-ttu-id="75400-121">Vous pouvez utiliser chaque cmdlet séparément, mais leur puissance s’exprime pleinement quand vous les combinez pour effectuer des tâches complexes.</span><span class="sxs-lookup"><span data-stu-id="75400-121">You can use each cmdlet separately, but their power is realized when you combine them to perform complex tasks.</span></span> <span data-ttu-id="75400-122">Comme de nombreux interpréteurs de commandes, PowerShell permet d’accéder au système de fichiers sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="75400-122">Like many shells, PowerShell gives you access to the file system on the computer.</span></span> <span data-ttu-id="75400-123">Les _fournisseurs_ PowerShell permettent d’accéder à d’autres magasins de données, tels que le Registre et les magasins de certificats, aussi facilement qu’au système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="75400-123">PowerShell _providers_ enable you to access other data stores, such as the registry and the certificate stores, as easily as you access the file system.</span></span>

<span data-ttu-id="75400-124">Vous pouvez créer vos propres modules de fonction et de cmdlet à l’aide de code ou de scripts compilés.</span><span class="sxs-lookup"><span data-stu-id="75400-124">You can create your own cmdlet and function modules using compiled code or scripts.</span></span> <span data-ttu-id="75400-125">Les modules peuvent ajouter des cmdlets et des fournisseurs à l’interpréteur de commandes.</span><span class="sxs-lookup"><span data-stu-id="75400-125">Modules can add cmdlets and providers to the shell.</span></span> <span data-ttu-id="75400-126">PowerShell prend également en charge des scripts analogues à ceux de l’interpréteur de commande UNIX et aux fichiers de traitement `cmd.exe`.</span><span class="sxs-lookup"><span data-stu-id="75400-126">PowerShell also supports scripts that are analogous to UNIX shell scripts and `cmd.exe` batch files.</span></span>

## <a name="support-for-command-aliases"></a><span data-ttu-id="75400-127">Prise en charge des alias de commande</span><span class="sxs-lookup"><span data-stu-id="75400-127">Support for command aliases</span></span>

<span data-ttu-id="75400-128">PowerShell prend en charge les alias pour faire référence aux commandes avec d’autres noms.</span><span class="sxs-lookup"><span data-stu-id="75400-128">PowerShell supports aliases to refer to commands by alternate names.</span></span> <span data-ttu-id="75400-129">Les alias permettent aux utilisateurs ayant l’expérience d’autres interpréteurs de commande d’utiliser des noms de commandes courants qu’ils connaissent déjà pour des opérations similaires dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="75400-129">Aliasing allows users with experience in other shells to use common command names that they already know for similar operations in PowerShell.</span></span>

<span data-ttu-id="75400-130">Créer un alias associe un nouveau nom à une autre commande.</span><span class="sxs-lookup"><span data-stu-id="75400-130">Aliasing associates a new name with another command.</span></span> <span data-ttu-id="75400-131">Par exemple, PowerShell dispose d’une fonction interne nommée `Clear-Host` qui efface la fenêtre de sortie.</span><span class="sxs-lookup"><span data-stu-id="75400-131">For example, PowerShell has an internal function named `Clear-Host` that clears the output window.</span></span> <span data-ttu-id="75400-132">Vous pouvez taper l’alias `cls` ou `clear` dans une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="75400-132">You can type either the `cls` or `clear` alias at a command prompt.</span></span> <span data-ttu-id="75400-133">PowerShell interprète ces alias et exécute la fonction `Clear-Host`.</span><span class="sxs-lookup"><span data-stu-id="75400-133">PowerShell interprets these aliases and runs the `Clear-Host` function.</span></span>

<span data-ttu-id="75400-134">Cette fonctionnalité aide les utilisateurs à apprendre à utiliser PowerShell.</span><span class="sxs-lookup"><span data-stu-id="75400-134">This feature helps users to learn PowerShell.</span></span> <span data-ttu-id="75400-135">Tout d’abord, la plupart des utilisateurs de `cmd.exe` et d’Unix ont un répertoire de commandes qu’ils connaissent déjà par leur nom.</span><span class="sxs-lookup"><span data-stu-id="75400-135">First, most `cmd.exe` and Unix users have a large repertoire of commands that users already know by name.</span></span> <span data-ttu-id="75400-136">Les équivalents PowerShell ne donneront peut-être pas des résultats identiques.</span><span class="sxs-lookup"><span data-stu-id="75400-136">The PowerShell equivalents may not produce identical results.</span></span> <span data-ttu-id="75400-137">Toutefois, les résultats sont assez proches pour que les utilisateurs puissent travailler sans connaître le nom de la commande PowerShell.</span><span class="sxs-lookup"><span data-stu-id="75400-137">However, the results are close enough that users can do work without knowing the PowerShell command name.</span></span> <span data-ttu-id="75400-138">La « mémoire musculaire » est une autre source principale de frustration lors de l’apprentissage d’un nouvel interpréteur de commande.</span><span class="sxs-lookup"><span data-stu-id="75400-138">"Muscle memory" is another major source of frustration when learning a new command shell.</span></span> <span data-ttu-id="75400-139">Si vous avez utilisé `cmd.exe` pendant des années, vous risquez de taper instinctivement la commande `cls` pour effacer l’écran.</span><span class="sxs-lookup"><span data-stu-id="75400-139">If you have used `cmd.exe` for years, you might reflexively type the `cls` command to clear the screen.</span></span> <span data-ttu-id="75400-140">Sans l’alias de `Clear-Host`, vous recevez un message d’erreur et ne savez pas quoi faire pour effacer la sortie.</span><span class="sxs-lookup"><span data-stu-id="75400-140">Without the alias for `Clear-Host`, you receive an error message and won't know what to do to clear the output.</span></span>

## <a name="powershell-handles-console-input-and-display"></a><span data-ttu-id="75400-141">PowerShell gère l’entrée et l’affichage sur la console</span><span class="sxs-lookup"><span data-stu-id="75400-141">PowerShell handles console input and display</span></span>

<span data-ttu-id="75400-142">Lorsque vous tapez une commande, PowerShell traite toujours directement la saisie de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="75400-142">When you type a command, PowerShell always processes the command-line input directly.</span></span> <span data-ttu-id="75400-143">PowerShell met également en forme la sortie sur écran.</span><span class="sxs-lookup"><span data-stu-id="75400-143">PowerShell also formats the output that you see on the screen.</span></span> <span data-ttu-id="75400-144">Cette différence est importante, car elle réduit le travail requis de chaque cmdlet.</span><span class="sxs-lookup"><span data-stu-id="75400-144">This difference is significant because it reduces the work required of each cmdlet.</span></span> <span data-ttu-id="75400-145">Elle garantit que vous pouvez toujours procéder de la même façon avec chaque cmdlet.</span><span class="sxs-lookup"><span data-stu-id="75400-145">It ensures that you can always do things the same way with any cmdlet.</span></span> <span data-ttu-id="75400-146">Les développeurs de cmdlet n’ont besoin ni d’écrire du code pour analyser les arguments de ligne de commande, ni de mettre en forme la sortie.</span><span class="sxs-lookup"><span data-stu-id="75400-146">Cmdlet developers don't need to write code to parse the command-line arguments or format the output.</span></span>

<span data-ttu-id="75400-147">Les outils en ligne de commande traditionnels ont leurs propres modes de demande et d’affichage de l’aide.</span><span class="sxs-lookup"><span data-stu-id="75400-147">Traditional command-line tools have their own schemes for requesting and displaying Help.</span></span> <span data-ttu-id="75400-148">Certains outils en ligne de commande utilisent `/?` pour lancer l’affichage de l’aide. D’autres utilisent `-?`, `/H`, voire `//`.</span><span class="sxs-lookup"><span data-stu-id="75400-148">Some command-line tools use `/?` to trigger the Help display; others use `-?`, `/H`, or even `//`.</span></span> <span data-ttu-id="75400-149">Certains affichent l’aide dans une fenêtre d’interface graphique utilisateur, plutôt que dans l’affichage de la console.</span><span class="sxs-lookup"><span data-stu-id="75400-149">Some will display Help in a GUI window, rather than in the console display.</span></span> <span data-ttu-id="75400-150">Si vous utilisez un paramètre incorrect, l’outil peut ignorer ce que vous avez tapé et commencer à exécuter une tâche automatiquement.</span><span class="sxs-lookup"><span data-stu-id="75400-150">If you use the wrong parameter, the tool might ignore what you typed and begin executing a task automatically.</span></span>
<span data-ttu-id="75400-151">Étant donné que PowerShell analyse et traite automatiquement la ligne de commande, le paramètre `-?` signifie toujours « afficher l’aide de cette commande ».</span><span class="sxs-lookup"><span data-stu-id="75400-151">Since PowerShell automatically parses and processes the command line, the `-?` parameter always means "show me Help for this command".</span></span>

> [!NOTE]
> <span data-ttu-id="75400-152">Si vous exécutez une application graphique dans PowerShell, la fenêtre de l’application s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="75400-152">If you run a graphic application in PowerShell, the window for the application opens.</span></span>
> <span data-ttu-id="75400-153">PowerShell intervient uniquement lors du traitement de l’entrée de ligne de commande que vous saisissez ou lors du renvoi de la sortie de l’application à la fenêtre de la console.</span><span class="sxs-lookup"><span data-stu-id="75400-153">PowerShell intervenes only when processing the command-line input you supply or the application output returned to the console window.</span></span> <span data-ttu-id="75400-154">Cela n’affecte en rien le fonctionnement interne de l’application.</span><span class="sxs-lookup"><span data-stu-id="75400-154">It does not affect how the application works internally.</span></span>

## <a name="powershell-has-a-pipeline"></a><span data-ttu-id="75400-155">PowerShell a un pipeline</span><span class="sxs-lookup"><span data-stu-id="75400-155">PowerShell has a pipeline</span></span>

<span data-ttu-id="75400-156">Les pipelines constituent indubitablement le concept plus important utilisé dans les interfaces de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="75400-156">Pipelines are arguably the most valuable concept used in command-line interfaces.</span></span> <span data-ttu-id="75400-157">Lorsqu’ils sont utilisés correctement, les pipelines réduisent l’effort lié à l’utilisation de commandes complexes et facilitent la visualisation du flux de travail.</span><span class="sxs-lookup"><span data-stu-id="75400-157">When used properly, pipelines reduce the effort of using complex commands and make it easier to see the flow of work.</span></span> <span data-ttu-id="75400-158">Chaque commande dans un pipeline passe sa sortie, élément par élément, à la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="75400-158">Each command in a pipeline passes its output, item by item, to the next command.</span></span> <span data-ttu-id="75400-159">Les commandes n’ont pas à gérer plusieurs éléments à la fois.</span><span class="sxs-lookup"><span data-stu-id="75400-159">Commands don't have to handle more than one item at a time.</span></span> <span data-ttu-id="75400-160">Il en résulte une consommation réduite des ressources et la possibilité de recevoir la sortie immédiatement.</span><span class="sxs-lookup"><span data-stu-id="75400-160">The result is reduced resource consumption and the ability to get output immediately.</span></span>

<span data-ttu-id="75400-161">La notation utilisée pour les pipelines est similaire celle utilisée dans d’autres interpréteurs de commandes.</span><span class="sxs-lookup"><span data-stu-id="75400-161">The notation used for pipelines is similar to the notation used in other shells.</span></span> <span data-ttu-id="75400-162">À première vue, les différences des pipelines dans PowerShell peuvent ne pas être évidentes.</span><span class="sxs-lookup"><span data-stu-id="75400-162">At first glance, it may not be apparent how pipelines are different in PowerShell.</span></span> <span data-ttu-id="75400-163">Même si vous voyez du texte à l’écran, PowerShell canalise des objets, pas du texte, entre les commandes.</span><span class="sxs-lookup"><span data-stu-id="75400-163">Although you see text on the screen, PowerShell pipes objects, not text, between commands.</span></span>

<span data-ttu-id="75400-164">Par exemple, si vous utilisez la cmdlet `Out-Host` pour forcer un affichage page par page de la sortie d’une autre commande, la sortie ressemble exactement au texte normal affiché à l’écran, mais divisé en pages :</span><span class="sxs-lookup"><span data-stu-id="75400-164">For example, if you use the `Out-Host` cmdlet to force a page-by-page display of output from another command, the output looks just like the normal text displayed on the screen, broken up into pages:</span></span>

```powershell
Get-ChildItem | Out-Host -Paging
```

```Output
    Directory: /mnt/c/Git/PS-Docs/PowerShell-Docs/reference/7.0/Microsoft.PowerShell.Core

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d----          05/22/2020    08:30                About
-----          05/20/2020    14:36           9044 Add-History.md
-----          05/20/2020    14:36          12227 Clear-History.md
-----          05/20/2020    14:36           3566 Clear-Host.md
-----          05/20/2020    14:36          29087 Connect-PSSession.md
-----          05/20/2020    14:36           5705 Debug-Job.md
-----          05/20/2020    14:36           3515 Disable-ExperimentalFeature.md
-----          05/20/2020    14:36          25531 Disable-PSRemoting.md
-----          05/20/2020    14:36           7852 Disable-PSSessionConfiguration.md
-----          05/20/2020    14:36          25355 Disconnect-PSSession.md
-----          05/20/2020    14:36           3491 Enable-ExperimentalFeature.md
-----          05/20/2020    14:36          13310 Enable-PSRemoting.md
-----          05/20/2020    14:36           8401 Enable-PSSessionConfiguration.md
-----          05/20/2020    14:36           9531 Enter-PSHostProcess.md
...
<SPACE> next page; <CR> next line; Q quit
```

<span data-ttu-id="75400-165">La pagination réduit également l’utilisation du processeur, car le traitement transfère à la cmdlet `Out-Host` lorsqu’il a une page complète prête à afficher.</span><span class="sxs-lookup"><span data-stu-id="75400-165">Paging also reduces CPU utilization because processing transfers to the `Out-Host` cmdlet when it has a complete page ready to display.</span></span> <span data-ttu-id="75400-166">L’exécution des cmdlets qui la précèdent dans le pipeline est interrompue jusqu’à ce que la page suivante de la sortie soit disponible.</span><span class="sxs-lookup"><span data-stu-id="75400-166">The cmdlets that precede it in the pipeline pause execution until the next page of output is available.</span></span>

### <a name="objects-in-the-pipeline"></a><span data-ttu-id="75400-167">Objets dans le pipeline</span><span class="sxs-lookup"><span data-stu-id="75400-167">Objects in the pipeline</span></span>

<span data-ttu-id="75400-168">Lorsque vous exécutez une cmdlet dans PowerShell, vous voyez une sortie texte, car il est de nécessaire de représenter les objets sous forme de texte dans une fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="75400-168">When you run a cmdlet in PowerShell, you see text output because it is necessary to represent objects as text in a console window.</span></span> <span data-ttu-id="75400-169">La sortie texte peut ne pas afficher toutes les propriétés de l’objet en cours de sortie.</span><span class="sxs-lookup"><span data-stu-id="75400-169">The text output may not display all of the properties of the object being output.</span></span>

<span data-ttu-id="75400-170">Prenez, par exemple, la cmdlet `Get-Location`.</span><span class="sxs-lookup"><span data-stu-id="75400-170">For example, consider the `Get-Location` cmdlet.</span></span> <span data-ttu-id="75400-171">La sortie texte est un résumé des informations, non une représentation complète de l’objet retourné par `Get-Location`.</span><span class="sxs-lookup"><span data-stu-id="75400-171">The text output is a summary of information, not a complete representation of the object returned by `Get-Location`.</span></span> <span data-ttu-id="75400-172">Le titre dans la sortie est ajouté par le processus qui met en forme les données pour l’affichage à l’écran.</span><span class="sxs-lookup"><span data-stu-id="75400-172">The heading in the output is added by the process that formats the data for onscreen display.</span></span>

```powershell
Get-Location
```

```Output
Path
----
C:\
```

<span data-ttu-id="75400-173">Lorsque vous dirigez la sortie vers la cmdlet `Get-Member`, vous obtenez des informations sur l’objet retourné par `Get-Location`.</span><span class="sxs-lookup"><span data-stu-id="75400-173">Piping the output to the `Get-Member` cmdlet displays information about the object returned by `Get-Location`.</span></span>

```powershell
Get-Location | Get-Member
```

```Output
   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Equals       Method     bool Equals(System.Object obj)
GetHashCode  Method     int GetHashCode()
GetType      Method     type GetType()
ToString     Method     string ToString()
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   string Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {get;}
ProviderPath Property   string ProviderPath {get;}
```

<span data-ttu-id="75400-174">`Get-Location` retourne un objet **PathInfo** qui contient le chemin d’accès actuel et d’autres informations.</span><span class="sxs-lookup"><span data-stu-id="75400-174">`Get-Location` returns a **PathInfo** object that contains the current path and other information.</span></span>

## <a name="built-in-help-system"></a><span data-ttu-id="75400-175">Système d’aide intégré</span><span class="sxs-lookup"><span data-stu-id="75400-175">Built-in help system</span></span>

<span data-ttu-id="75400-176">À l’instar des pages `man` Unix, PowerShell inclut des articles d’aide détaillés qui expliquent les concepts et la syntaxe de commande de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="75400-176">Similar to Unix `man` pages, PowerShell includes detailed help articles that explain PowerShell concepts and command syntax.</span></span> <span data-ttu-id="75400-177">Utilisez la cmdlet [Get-Help][] pour afficher ces articles à l’invite de commandes ou affichez les versions les plus récemment mises à jour de ces articles dans la documentation PowerShell en ligne.</span><span class="sxs-lookup"><span data-stu-id="75400-177">Use the [Get-Help][] cmdlet to display these articles at the command prompt or view the most recently updated versions of these articles in the PowerShell documentation online.</span></span>

## <a name="next-steps"></a><span data-ttu-id="75400-178">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="75400-178">Next steps</span></span>

<span data-ttu-id="75400-179">Pour en savoir plus sur PowerShell, consultez la section **Découvrir PowerShell** de ce site.</span><span class="sxs-lookup"><span data-stu-id="75400-179">To learn more about PowerShell, see the **Learning PowerShell** section of this site.</span></span>

<!-- link references -->

[Get-Help]: /powershell/module/microsoft.powershell.core/Get-Help
