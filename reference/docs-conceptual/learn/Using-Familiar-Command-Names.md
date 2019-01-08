---
ms.date: 08/27/2018
keywords: powershell,applet de commande
title: Utilisation de noms de commande familiers
ms.assetid: 021e2424-c64e-4fa5-aa98-aa6405758d5d
ms.openlocfilehash: c5665f64fd832eb9c807f413a8e879f63db7f8c6
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402083"
---
# <a name="using-familiar-command-names"></a><span data-ttu-id="21d31-103">Utilisation de noms de commande familiers</span><span class="sxs-lookup"><span data-stu-id="21d31-103">Using familiar command names</span></span>

<span data-ttu-id="21d31-104">PowerShell prend en charge les alias pour faire référence aux commandes avec d’autres noms.</span><span class="sxs-lookup"><span data-stu-id="21d31-104">PowerShell supports aliases to refer to commands by alternate names.</span></span> <span data-ttu-id="21d31-105">Les alias permettent aux utilisateurs ayant l’expérience d’autres interpréteurs de commande d’utiliser des noms de commandes courants qu’ils connaissent déjà pour des opérations similaires dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="21d31-105">Aliasing allows users with experience in other shells to use common command names that they already know for similar operations in PowerShell.</span></span>

<span data-ttu-id="21d31-106">Créer un alias associe un nouveau nom à une autre commande.</span><span class="sxs-lookup"><span data-stu-id="21d31-106">Aliasing associates a new name with another command.</span></span> <span data-ttu-id="21d31-107">Par exemple, PowerShell dispose d’une fonction interne nommée `Clear-Host` qui efface la fenêtre de sortie.</span><span class="sxs-lookup"><span data-stu-id="21d31-107">For example, PowerShell has an internal function named `Clear-Host` that clears the output window.</span></span> <span data-ttu-id="21d31-108">Vous pouvez taper l’alias `cls` ou `clear` dans une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="21d31-108">You can type either the `cls` or `clear` alias at a command prompt.</span></span> <span data-ttu-id="21d31-109">PowerShell interprète ces alias et exécute la fonction `Clear-Host`.</span><span class="sxs-lookup"><span data-stu-id="21d31-109">PowerShell interprets these aliases and runs the `Clear-Host` function.</span></span>

<span data-ttu-id="21d31-110">Cette fonctionnalité aide les utilisateurs à apprendre à utiliser PowerShell.</span><span class="sxs-lookup"><span data-stu-id="21d31-110">This feature helps users to learn PowerShell.</span></span> <span data-ttu-id="21d31-111">Tout d’abord, la plupart des utilisateurs de **cmd.exe** et d’Unix ont un répertoire de commandes qu’ils connaissent déjà par leur nom.</span><span class="sxs-lookup"><span data-stu-id="21d31-111">First, most **cmd.exe** and Unix users have a large repertoire of commands that users already know by name.</span></span> <span data-ttu-id="21d31-112">Les équivalents PowerShell ne donneront peut-être pas des résultats identiques.</span><span class="sxs-lookup"><span data-stu-id="21d31-112">The PowerShell equivalents may not produce identical results.</span></span> <span data-ttu-id="21d31-113">Toutefois, les résultats sont assez proches pour que les utilisateurs puissent travailler sans connaître le nom de la commande PowerShell.</span><span class="sxs-lookup"><span data-stu-id="21d31-113">However, the results are close enough that users can do work without knowing the PowerShell command name.</span></span> <span data-ttu-id="21d31-114">La « mémoire des doigts » est une autre source principale de frustration lors de l’apprentissage d’un nouvel interpréteur de commande.</span><span class="sxs-lookup"><span data-stu-id="21d31-114">"Finger memory" is another major source of frustration when learning a new command shell.</span></span> <span data-ttu-id="21d31-115">Si vous avez utilisé **cmd.exe** pendant des années, vous risquez de taper instinctivement la commande `cls` pour effacer l’écran.</span><span class="sxs-lookup"><span data-stu-id="21d31-115">If you have used **cmd.exe** for years, you might reflexively type the `cls` command to clear the screen.</span></span> <span data-ttu-id="21d31-116">Sans l’alias de `Clear-Host`, vous recevez un message d’erreur et ne savez pas quoi faire pour effacer la sortie.</span><span class="sxs-lookup"><span data-stu-id="21d31-116">Without the alias for `Clear-Host`, you receive an error message and won't know what to do to clear the output.</span></span>

<span data-ttu-id="21d31-117">La liste ci-dessous contient quelques-unes des commandes **Cmd.exe** et Unix courantes que vous pouvez utiliser dans PowerShell :</span><span class="sxs-lookup"><span data-stu-id="21d31-117">The following list shows a few of the common **cmd.exe** and Unix commands that you can use in PowerShell:</span></span>

|||||
|-|-|-|-|
|<span data-ttu-id="21d31-118">cat</span><span class="sxs-lookup"><span data-stu-id="21d31-118">cat</span></span>|<span data-ttu-id="21d31-119">dir</span><span class="sxs-lookup"><span data-stu-id="21d31-119">dir</span></span>|<span data-ttu-id="21d31-120">mount</span><span class="sxs-lookup"><span data-stu-id="21d31-120">mount</span></span>|<span data-ttu-id="21d31-121">rm</span><span class="sxs-lookup"><span data-stu-id="21d31-121">rm</span></span>|
|<span data-ttu-id="21d31-122">cd</span><span class="sxs-lookup"><span data-stu-id="21d31-122">cd</span></span>|<span data-ttu-id="21d31-123">echo</span><span class="sxs-lookup"><span data-stu-id="21d31-123">echo</span></span>|<span data-ttu-id="21d31-124">move</span><span class="sxs-lookup"><span data-stu-id="21d31-124">move</span></span>|<span data-ttu-id="21d31-125">rmdir</span><span class="sxs-lookup"><span data-stu-id="21d31-125">rmdir</span></span>|
|<span data-ttu-id="21d31-126">chdir</span><span class="sxs-lookup"><span data-stu-id="21d31-126">chdir</span></span>|<span data-ttu-id="21d31-127">erase</span><span class="sxs-lookup"><span data-stu-id="21d31-127">erase</span></span>|<span data-ttu-id="21d31-128">popd</span><span class="sxs-lookup"><span data-stu-id="21d31-128">popd</span></span>|<span data-ttu-id="21d31-129">sleep</span><span class="sxs-lookup"><span data-stu-id="21d31-129">sleep</span></span>|
|<span data-ttu-id="21d31-130">clear</span><span class="sxs-lookup"><span data-stu-id="21d31-130">clear</span></span>|<span data-ttu-id="21d31-131">h</span><span class="sxs-lookup"><span data-stu-id="21d31-131">h</span></span>|<span data-ttu-id="21d31-132">ps</span><span class="sxs-lookup"><span data-stu-id="21d31-132">ps</span></span>|<span data-ttu-id="21d31-133">sort</span><span class="sxs-lookup"><span data-stu-id="21d31-133">sort</span></span>|
|<span data-ttu-id="21d31-134">cls</span><span class="sxs-lookup"><span data-stu-id="21d31-134">cls</span></span>|<span data-ttu-id="21d31-135">history</span><span class="sxs-lookup"><span data-stu-id="21d31-135">history</span></span>|<span data-ttu-id="21d31-136">pushd</span><span class="sxs-lookup"><span data-stu-id="21d31-136">pushd</span></span>|<span data-ttu-id="21d31-137">tee</span><span class="sxs-lookup"><span data-stu-id="21d31-137">tee</span></span>|
|<span data-ttu-id="21d31-138">copy</span><span class="sxs-lookup"><span data-stu-id="21d31-138">copy</span></span>|<span data-ttu-id="21d31-139">kill</span><span class="sxs-lookup"><span data-stu-id="21d31-139">kill</span></span>|<span data-ttu-id="21d31-140">pwd</span><span class="sxs-lookup"><span data-stu-id="21d31-140">pwd</span></span>|<span data-ttu-id="21d31-141">type</span><span class="sxs-lookup"><span data-stu-id="21d31-141">type</span></span>|
|<span data-ttu-id="21d31-142">del</span><span class="sxs-lookup"><span data-stu-id="21d31-142">del</span></span>|<span data-ttu-id="21d31-143">lp</span><span class="sxs-lookup"><span data-stu-id="21d31-143">lp</span></span>|<span data-ttu-id="21d31-144">r</span><span class="sxs-lookup"><span data-stu-id="21d31-144">r</span></span>|<span data-ttu-id="21d31-145">write</span><span class="sxs-lookup"><span data-stu-id="21d31-145">write</span></span>|
|<span data-ttu-id="21d31-146">diff</span><span class="sxs-lookup"><span data-stu-id="21d31-146">diff</span></span>|<span data-ttu-id="21d31-147">ls</span><span class="sxs-lookup"><span data-stu-id="21d31-147">ls</span></span>|<span data-ttu-id="21d31-148">ren</span><span class="sxs-lookup"><span data-stu-id="21d31-148">ren</span></span>||

<span data-ttu-id="21d31-149">L’applet de commande `Get-Alias` affiche le nom réel de la commande PowerShell native associée à un alias.</span><span class="sxs-lookup"><span data-stu-id="21d31-149">The `Get-Alias` cmdlet shows you the real name of the native PowerShell command associated with an alias.</span></span>

```powershell
PS> Get-Alias cls
```

```Output
CommandType     Name                               Version    Source
-----------     ----                               -------    ------
Alias           cls -> Clear-Host
```

## <a name="interpreting-standard-aliases"></a><span data-ttu-id="21d31-150">Interprétation des alias standard</span><span class="sxs-lookup"><span data-stu-id="21d31-150">Interpreting standard aliases</span></span>

<span data-ttu-id="21d31-151">Les alias décrits plus haut ont été conçus de manière que leurs noms sont compatibles avec d’autres interpréteurs de commande.</span><span class="sxs-lookup"><span data-stu-id="21d31-151">The aliases we described previous were designed for name-compatibility with other command shells.</span></span>
<span data-ttu-id="21d31-152">La plupart des alias intégrés dans PowerShell sont conçues par souci de concision.</span><span class="sxs-lookup"><span data-stu-id="21d31-152">Most aliases built into PowerShell are designed for brevity.</span></span> <span data-ttu-id="21d31-153">Des noms plus courts sont plus faciles à taper, mais ils sont difficiles à lire si vous ne savez pas à quoi ils font référence.</span><span class="sxs-lookup"><span data-stu-id="21d31-153">Shorter names are easier to type, but are difficult to read if you don't know what they refer to.</span></span>

<span data-ttu-id="21d31-154">Les alias PowerShell sont une tentative de compromis entre la clarté et la concision.</span><span class="sxs-lookup"><span data-stu-id="21d31-154">PowerShell aliases try to compromise between clarity and brevity.</span></span> <span data-ttu-id="21d31-155">PowerShell utilise un ensemble standard d’alias pour les verbes et les noms courants.</span><span class="sxs-lookup"><span data-stu-id="21d31-155">PowerShell uses a standard set of aliases for common nouns and verbs.</span></span>

<span data-ttu-id="21d31-156">Exemples d’abréviations :</span><span class="sxs-lookup"><span data-stu-id="21d31-156">Example abbreviations:</span></span>

| <span data-ttu-id="21d31-157">Nom ou verbe</span><span class="sxs-lookup"><span data-stu-id="21d31-157">Noun or Verb</span></span> | <span data-ttu-id="21d31-158">Abréviation</span><span class="sxs-lookup"><span data-stu-id="21d31-158">Abbreviation</span></span> |
|--------------|--------------|
| <span data-ttu-id="21d31-159">Get</span><span class="sxs-lookup"><span data-stu-id="21d31-159">Get</span></span>          | <span data-ttu-id="21d31-160">g</span><span class="sxs-lookup"><span data-stu-id="21d31-160">g</span></span>            |
| <span data-ttu-id="21d31-161">Set</span><span class="sxs-lookup"><span data-stu-id="21d31-161">Set</span></span>          | <span data-ttu-id="21d31-162">s</span><span class="sxs-lookup"><span data-stu-id="21d31-162">s</span></span>            |
| <span data-ttu-id="21d31-163">Élément</span><span class="sxs-lookup"><span data-stu-id="21d31-163">Item</span></span>         | <span data-ttu-id="21d31-164">i</span><span class="sxs-lookup"><span data-stu-id="21d31-164">i</span></span>            |
| <span data-ttu-id="21d31-165">Emplacement</span><span class="sxs-lookup"><span data-stu-id="21d31-165">Location</span></span>     | <span data-ttu-id="21d31-166">l</span><span class="sxs-lookup"><span data-stu-id="21d31-166">l</span></span>            |
| <span data-ttu-id="21d31-167">Commande</span><span class="sxs-lookup"><span data-stu-id="21d31-167">Command</span></span>      | <span data-ttu-id="21d31-168">cm</span><span class="sxs-lookup"><span data-stu-id="21d31-168">cm</span></span>           |
| <span data-ttu-id="21d31-169">Alias</span><span class="sxs-lookup"><span data-stu-id="21d31-169">Alias</span></span>        | <span data-ttu-id="21d31-170">al</span><span class="sxs-lookup"><span data-stu-id="21d31-170">al</span></span>           |

<span data-ttu-id="21d31-171">Ces alias sont compréhensibles lorsque vous connaissez les noms abrégés.</span><span class="sxs-lookup"><span data-stu-id="21d31-171">These aliases are understandable when you know the shorthand names.</span></span>

| <span data-ttu-id="21d31-172">Nom de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="21d31-172">Cmdlet name</span></span>    | <span data-ttu-id="21d31-173">Alias</span><span class="sxs-lookup"><span data-stu-id="21d31-173">Alias</span></span> |
|----------------|-------|
| `Get-Item `    | <span data-ttu-id="21d31-174">gi</span><span class="sxs-lookup"><span data-stu-id="21d31-174">gi</span></span>    |
| `Set-Item`     | <span data-ttu-id="21d31-175">si</span><span class="sxs-lookup"><span data-stu-id="21d31-175">si</span></span>    |
| `Get-Location` | <span data-ttu-id="21d31-176">gl</span><span class="sxs-lookup"><span data-stu-id="21d31-176">gl</span></span>    |
| `Set-Location` | <span data-ttu-id="21d31-177">sl</span><span class="sxs-lookup"><span data-stu-id="21d31-177">sl</span></span>    |
| `Get-Command`  | <span data-ttu-id="21d31-178">gcm</span><span class="sxs-lookup"><span data-stu-id="21d31-178">gcm</span></span>   |
| `Get-Alias`    | <span data-ttu-id="21d31-179">gal</span><span class="sxs-lookup"><span data-stu-id="21d31-179">gal</span></span>   |

<span data-ttu-id="21d31-180">Une fois que vous êtes familiarisé avec les alias de PowerShell, il est facile de deviner à quoi l’alias **sal** fait référence`Set-Alias`.</span><span class="sxs-lookup"><span data-stu-id="21d31-180">Once you're familiar with PowerShell aliasing, it's easy to guess that the **sal** alias refers to `Set-Alias`.</span></span>

## <a name="creating-new-aliases"></a><span data-ttu-id="21d31-181">Création d’alias</span><span class="sxs-lookup"><span data-stu-id="21d31-181">Creating new aliases</span></span>

<span data-ttu-id="21d31-182">Vous pouvez créer vos propres alias à l’aide de l’applet de commande `Set-Alias`.</span><span class="sxs-lookup"><span data-stu-id="21d31-182">You can create your own aliases using the `Set-Alias` cmdlet.</span></span> <span data-ttu-id="21d31-183">Par exemple, les instructions suivantes créent les alias d’applet de commande standard décrits précédemment :</span><span class="sxs-lookup"><span data-stu-id="21d31-183">For example, the following statements create the standard cmdlet aliases previously discussed:</span></span>

```powershell
Set-Alias -Name gi -Value Get-Item
Set-Alias -Name si -Value Set-Item
Set-Alias -Name gl -Value Get-Location
Set-Alias -Name sl -Value Set-Location
Set-Alias -Name gcm -Value Get-Command
```

<span data-ttu-id="21d31-184">En interne, PowerShell utilise des commandes similaires pendant le démarrage, mais ces alias ne sont pas modifiables.</span><span class="sxs-lookup"><span data-stu-id="21d31-184">Internally, PowerShell uses similar commands during startup, but these aliases are not changeable.</span></span>
<span data-ttu-id="21d31-185">Si vous tentez d’exécuter l’une de ces commandes, vous obtenez un message d’erreur expliquant que l’alias ne peut pas être modifié.</span><span class="sxs-lookup"><span data-stu-id="21d31-185">If you try to execute one of these commands, you get an error explaining that the alias can't be modified.</span></span> <span data-ttu-id="21d31-186">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="21d31-186">For example:</span></span>

```
PS> Set-Alias -Name gi -Value Get-Item
Set-Alias : Alias is not writeable because alias gi is read-only or constant and cannot be written to.
At line:1 char:10
+ Set-Alias  <<<< -Name gi -Value Get-Item
```