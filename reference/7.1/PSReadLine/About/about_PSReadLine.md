---
description: PSReadLine fournit une expérience d’édition de ligne de commande améliorée dans la console PowerShell.
keywords: powershell
Locale: en-US
ms.date: 11/16/2020
online version: https://docs.microsoft.com/powershell/module/psreadline/about/about_psreadline?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: À propos de PSReadLine
ms.openlocfilehash: 6d52bb04118914a9ccca5d3442a9d1915c1c2818
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94692273"
---
# <a name="psreadline"></a><span data-ttu-id="41595-104">PSReadLine</span><span class="sxs-lookup"><span data-stu-id="41595-104">PSReadLine</span></span>

## <a name="about_psreadline"></a><span data-ttu-id="41595-105">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="41595-105">about_PSReadLine</span></span>

## <a name="short-description"></a><span data-ttu-id="41595-106">Description courte</span><span class="sxs-lookup"><span data-stu-id="41595-106">Short Description</span></span>

<span data-ttu-id="41595-107">PSReadLine fournit une expérience d’édition de ligne de commande améliorée dans la console PowerShell.</span><span class="sxs-lookup"><span data-stu-id="41595-107">PSReadLine provides an improved command-line editing experience in the PowerShell console.</span></span>

## <a name="long-description"></a><span data-ttu-id="41595-108">Description longue</span><span class="sxs-lookup"><span data-stu-id="41595-108">Long Description</span></span>

<span data-ttu-id="41595-109">PSReadLine 2,1 fournit une expérience d’édition de ligne de commande puissante pour la console PowerShell.</span><span class="sxs-lookup"><span data-stu-id="41595-109">PSReadLine 2.1 provides a powerful command-line editing experience for the PowerShell console.</span></span> <span data-ttu-id="41595-110">Elle offre les possibilités suivantes :</span><span class="sxs-lookup"><span data-stu-id="41595-110">It provides:</span></span>

- <span data-ttu-id="41595-111">Coloration de la syntaxe de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="41595-111">Syntax coloring of the command line</span></span>
- <span data-ttu-id="41595-112">Indication visuelle des erreurs de syntaxe</span><span class="sxs-lookup"><span data-stu-id="41595-112">A visual indication of syntax errors</span></span>
- <span data-ttu-id="41595-113">Une meilleure expérience multi-ligne (modification et historique)</span><span class="sxs-lookup"><span data-stu-id="41595-113">A better multi-line experience (both editing and history)</span></span>
- <span data-ttu-id="41595-114">Combinaisons de touches personnalisables</span><span class="sxs-lookup"><span data-stu-id="41595-114">Customizable key bindings</span></span>
- <span data-ttu-id="41595-115">Modes cmd et Emacs</span><span class="sxs-lookup"><span data-stu-id="41595-115">Cmd and Emacs modes</span></span>
- <span data-ttu-id="41595-116">Nombreuses options de configuration</span><span class="sxs-lookup"><span data-stu-id="41595-116">Many configuration options</span></span>
- <span data-ttu-id="41595-117">Saisie semi-automatique du style bash (facultatif en mode cmd, par défaut en mode emacs)</span><span class="sxs-lookup"><span data-stu-id="41595-117">Bash style completion (optional in Cmd mode, default in Emacs mode)</span></span>
- <span data-ttu-id="41595-118">Emacs-Yank/Kill-Ring</span><span class="sxs-lookup"><span data-stu-id="41595-118">Emacs yank/kill-ring</span></span>
- <span data-ttu-id="41595-119">Mouvement « mot » basé sur un jeton PowerShell et Kill</span><span class="sxs-lookup"><span data-stu-id="41595-119">PowerShell token based "word" movement and kill</span></span>
- <span data-ttu-id="41595-120">IntelliSense prédictif</span><span class="sxs-lookup"><span data-stu-id="41595-120">Predictive IntelliSense</span></span>

<span data-ttu-id="41595-121">PSReadLine nécessite PowerShell 3,0, ou une version plus récente, et l’hôte de la console.</span><span class="sxs-lookup"><span data-stu-id="41595-121">PSReadLine requires PowerShell 3.0, or newer, and the console host.</span></span> <span data-ttu-id="41595-122">Il ne fonctionne pas dans PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="41595-122">It does not work in PowerShell ISE.</span></span> <span data-ttu-id="41595-123">Elle fonctionne dans la console de Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="41595-123">It does work in the console of Visual Studio Code.</span></span>

<span data-ttu-id="41595-124">PSReadLine 2.1.0 est fourni avec PowerShell 7,1 et est pris en charge dans toutes les versions prises en charge de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="41595-124">PSReadLine 2.1.0 ships with PowerShell 7.1 and is supported in all supported versions of PowerShell.</span></span> <span data-ttu-id="41595-125">Vous pouvez l’installer à partir du PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="41595-125">It is available to install from the PowerShell Gallery.</span></span>
<span data-ttu-id="41595-126">Pour installer PSReadLine 2.1.0 dans une version prise en charge de PowerShell, exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="41595-126">To install PSReadLine 2.1.0 in a supported version of PowerShell run the following command.</span></span>

```powershell
Install-Module -Name PSReadLine -RequiredVersion 2.1.0
```

> [!NOTE]
> <span data-ttu-id="41595-127">À compter de PowerShell 7,0, PowerShell ignore le chargement automatique de PSReadLine sur Windows si un programme de lecture d’écran est détecté.</span><span class="sxs-lookup"><span data-stu-id="41595-127">Beginning with PowerShell 7.0, PowerShell skips auto-loading PSReadLine on Windows if a screen reader program is detected.</span></span> <span data-ttu-id="41595-128">Actuellement, PSReadLine ne fonctionne pas correctement avec les lecteurs d’écran.</span><span class="sxs-lookup"><span data-stu-id="41595-128">Currently, PSReadLine doesn't work well with the screen readers.</span></span> <span data-ttu-id="41595-129">Le rendu et la mise en forme par défaut de PowerShell 7,0 sur Windows fonctionnent correctement.</span><span class="sxs-lookup"><span data-stu-id="41595-129">The default rendering and formatting of PowerShell 7.0 on Windows works properly.</span></span> <span data-ttu-id="41595-130">Vous pouvez charger le module manuellement, si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="41595-130">You can manually load the module if necessary.</span></span>

## <a name="predictive-intellisense"></a><span data-ttu-id="41595-131">IntelliSense prédictif</span><span class="sxs-lookup"><span data-stu-id="41595-131">Predictive IntelliSense</span></span>

<span data-ttu-id="41595-132">La fonctionnalité IntelliSense prédictive est un ajout au concept de saisie semi-automatique via la touche Tab qui aide l’utilisateur à exécuter correctement les commandes.</span><span class="sxs-lookup"><span data-stu-id="41595-132">Predictive IntelliSense is an addition to the concept of tab completion that assists the user in successfully completing commands.</span></span> <span data-ttu-id="41595-133">Il permet aux utilisateurs de découvrir, de modifier et d’exécuter des commandes complètes basées sur des prédictions correspondantes à partir de l’historique de l’utilisateur et d’autres plug-ins spécifiques au domaine.</span><span class="sxs-lookup"><span data-stu-id="41595-133">It enables users to discover, edit, and execute full commands based on matching predictions from the user's history and additional domain specific plugins.</span></span>

### <a name="enable-predictive-intellisense"></a><span data-ttu-id="41595-134">Activer la fonctionnalité IntelliSense prédictive</span><span class="sxs-lookup"><span data-stu-id="41595-134">Enable Predictive IntelliSense</span></span>

<span data-ttu-id="41595-135">La fonctionnalité IntelliSense prédictive est désactivée par défaut.</span><span class="sxs-lookup"><span data-stu-id="41595-135">Predictive IntelliSense is disabled by default.</span></span> <span data-ttu-id="41595-136">Pour activer les prédictions, exécutez simplement la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="41595-136">To enable predictions, just run the following command:</span></span>

```powershell
Set-PSReadLineOption -PredictionSource History
```

<span data-ttu-id="41595-137">Le paramètre **PredictionSource** peut également accepter des plug-ins pour des exigences personnalisées et spécifiques à un domaine.</span><span class="sxs-lookup"><span data-stu-id="41595-137">The **PredictionSource** parameter can also accept plugins for domain specific and custom requirements.</span></span>

<span data-ttu-id="41595-138">Pour désactiver IntelliSense prédictif, il suffit d’exécuter :</span><span class="sxs-lookup"><span data-stu-id="41595-138">To disable Predictive IntelliSense, just run:</span></span>

```powershell
Set-PSReadLineOption -PredictionSource None
```

<span data-ttu-id="41595-139">Les fonctions suivantes sont disponibles dans la classe **[Microsoft. PowerShell. PSConsoleReadLine]**.</span><span class="sxs-lookup"><span data-stu-id="41595-139">The following functions are available in the class **[Microsoft.PowerShell.PSConsoleReadLine]**.</span></span>

## <a name="basic-editing-functions"></a><span data-ttu-id="41595-140">Fonctions d’édition de base</span><span class="sxs-lookup"><span data-stu-id="41595-140">Basic editing functions</span></span>

### <a name="abort"></a><span data-ttu-id="41595-141">Abandon</span><span class="sxs-lookup"><span data-stu-id="41595-141">Abort</span></span>

<span data-ttu-id="41595-142">Annuler l’action en cours, par exemple, recherche de l’historique incrémentiel.</span><span class="sxs-lookup"><span data-stu-id="41595-142">Abort current action, e.g. incremental history search.</span></span>

- <span data-ttu-id="41595-143">Emacs- `<Ctrl+g>`</span><span class="sxs-lookup"><span data-stu-id="41595-143">Emacs: `<Ctrl+g>`</span></span>

### <a name="acceptandgetnext"></a><span data-ttu-id="41595-144">AcceptAndGetNext</span><span class="sxs-lookup"><span data-stu-id="41595-144">AcceptAndGetNext</span></span>

<span data-ttu-id="41595-145">Tentative d’exécution de l’entrée en cours.</span><span class="sxs-lookup"><span data-stu-id="41595-145">Attempt to execute the current input.</span></span> <span data-ttu-id="41595-146">Si elle peut être exécutée (par exemple, AcceptLine), rappelez l’élément suivant de l’historique la prochaine fois que ReadLine est appelé.</span><span class="sxs-lookup"><span data-stu-id="41595-146">If it can be executed (like AcceptLine), then recall the next item from history the next time ReadLine is called.</span></span>

- <span data-ttu-id="41595-147">Emacs- `<Ctrl+o>`</span><span class="sxs-lookup"><span data-stu-id="41595-147">Emacs: `<Ctrl+o>`</span></span>

### <a name="acceptline"></a><span data-ttu-id="41595-148">AcceptLine</span><span class="sxs-lookup"><span data-stu-id="41595-148">AcceptLine</span></span>

<span data-ttu-id="41595-149">Tentative d’exécution de l’entrée en cours.</span><span class="sxs-lookup"><span data-stu-id="41595-149">Attempt to execute the current input.</span></span> <span data-ttu-id="41595-150">Si l’entrée actuelle est incomplète (par exemple, il manque une parenthèse fermante, un crochet ou un guillemet, l’invite de continuation est affichée sur la ligne suivante et PSReadLine attend que les clés modifient l’entrée actuelle.</span><span class="sxs-lookup"><span data-stu-id="41595-150">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="41595-151">Cmd `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="41595-151">Cmd: `<Enter>`</span></span>
- <span data-ttu-id="41595-152">Emacs- `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="41595-152">Emacs: `<Enter>`</span></span>
- <span data-ttu-id="41595-153">Mode d’insertion VI : `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="41595-153">Vi insert mode: `<Enter>`</span></span>

### <a name="addline"></a><span data-ttu-id="41595-154">AddLine</span><span class="sxs-lookup"><span data-stu-id="41595-154">AddLine</span></span>

<span data-ttu-id="41595-155">L’invite de continuation est affichée sur la ligne suivante et PSReadLine attend que les clés modifient l’entrée actuelle.</span><span class="sxs-lookup"><span data-stu-id="41595-155">The continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span> <span data-ttu-id="41595-156">Cela est utile pour entrer une entrée multiligne sous la forme d’une commande unique, même lorsqu’une seule ligne est complète en entrée.</span><span class="sxs-lookup"><span data-stu-id="41595-156">This is useful to enter multi-line input as a single command even when a single line is complete input by itself.</span></span>

- <span data-ttu-id="41595-157">Cmd `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="41595-157">Cmd: `<Shift+Enter>`</span></span>
- <span data-ttu-id="41595-158">Emacs- `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="41595-158">Emacs: `<Shift+Enter>`</span></span>
- <span data-ttu-id="41595-159">Mode d’insertion VI : `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="41595-159">Vi insert mode: `<Shift+Enter>`</span></span>
- <span data-ttu-id="41595-160">Mode de commande VI : `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="41595-160">Vi command mode: `<Shift+Enter>`</span></span>

### <a name="backwarddeletechar"></a><span data-ttu-id="41595-161">BackwardDeleteChar</span><span class="sxs-lookup"><span data-stu-id="41595-161">BackwardDeleteChar</span></span>

<span data-ttu-id="41595-162">Supprimez le caractère avant le curseur.</span><span class="sxs-lookup"><span data-stu-id="41595-162">Delete the character before the cursor.</span></span>

- <span data-ttu-id="41595-163">Cmd : `<Backspace>` , `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="41595-163">Cmd: `<Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="41595-164">Emacs : `<Backspace>` , `<Ctrl+Backspace>` , `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="41595-164">Emacs: `<Backspace>`, `<Ctrl+Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="41595-165">Mode d’insertion VI : `<Backspace>`</span><span class="sxs-lookup"><span data-stu-id="41595-165">Vi insert mode: `<Backspace>`</span></span>
- <span data-ttu-id="41595-166">Mode de commande VI : `<X>` , `<d,h>`</span><span class="sxs-lookup"><span data-stu-id="41595-166">Vi command mode: `<X>`, `<d,h>`</span></span>

### <a name="backwarddeleteline"></a><span data-ttu-id="41595-167">BackwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="41595-167">BackwardDeleteLine</span></span>

<span data-ttu-id="41595-168">Comme BackwardKillLine-supprime le texte du point jusqu’au début de la ligne, mais ne place pas le texte supprimé dans l’anneau d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="41595-168">Like BackwardKillLine - deletes text from the point to the start of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="41595-169">Cmd `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="41595-169">Cmd: `<Ctrl+Home>`</span></span>
- <span data-ttu-id="41595-170">Mode d’insertion VI : `<Ctrl+u>` , `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="41595-170">Vi insert mode: `<Ctrl+u>`, `<Ctrl+Home>`</span></span>
- <span data-ttu-id="41595-171">Mode de commande VI : `<Ctrl+u>` , `<Ctrl+Home>` , `<d,0>`</span><span class="sxs-lookup"><span data-stu-id="41595-171">Vi command mode: `<Ctrl+u>`, `<Ctrl+Home>`, `<d,0>`</span></span>

### <a name="backwarddeleteword"></a><span data-ttu-id="41595-172">BackwardDeleteWord</span><span class="sxs-lookup"><span data-stu-id="41595-172">BackwardDeleteWord</span></span>

<span data-ttu-id="41595-173">Supprime le mot précédent.</span><span class="sxs-lookup"><span data-stu-id="41595-173">Deletes the previous word.</span></span>

- <span data-ttu-id="41595-174">Mode de commande VI : `<Ctrl+w>` , `<d,b>`</span><span class="sxs-lookup"><span data-stu-id="41595-174">Vi command mode: `<Ctrl+w>`, `<d,b>`</span></span>

### <a name="backwardkillline"></a><span data-ttu-id="41595-175">BackwardKillLine</span><span class="sxs-lookup"><span data-stu-id="41595-175">BackwardKillLine</span></span>

<span data-ttu-id="41595-176">Effacez l’entrée à partir du début de l’entrée jusqu’au curseur.</span><span class="sxs-lookup"><span data-stu-id="41595-176">Clear the input from the start of the input to the cursor.</span></span> <span data-ttu-id="41595-177">Le texte effacé est placé dans le Kill-Ring.</span><span class="sxs-lookup"><span data-stu-id="41595-177">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="41595-178">Emacs- `<Ctrl+u>` , `<Ctrl+x,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="41595-178">Emacs: `<Ctrl+u>`, `<Ctrl+x,Backspace>`</span></span>

### <a name="backwardkillword"></a><span data-ttu-id="41595-179">BackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="41595-179">BackwardKillWord</span></span>

<span data-ttu-id="41595-180">Efface l’entrée du début du mot actuel jusqu’au curseur.</span><span class="sxs-lookup"><span data-stu-id="41595-180">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="41595-181">Si le curseur se trouve entre des mots, l’entrée est effacée du début du mot précédent au curseur.</span><span class="sxs-lookup"><span data-stu-id="41595-181">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="41595-182">Le texte effacé est placé dans le Kill-Ring.</span><span class="sxs-lookup"><span data-stu-id="41595-182">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="41595-183">Cmd : `<Ctrl+Backspace>` , `<Ctrl+w>`</span><span class="sxs-lookup"><span data-stu-id="41595-183">Cmd: `<Ctrl+Backspace>`, `<Ctrl+w>`</span></span>
- <span data-ttu-id="41595-184">Emacs- `<Alt+Backspace>` , `<Escape,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="41595-184">Emacs: `<Alt+Backspace>`, `<Escape,Backspace>`</span></span>
- <span data-ttu-id="41595-185">Mode d’insertion VI : `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="41595-185">Vi insert mode: `<Ctrl+Backspace>`</span></span>
- <span data-ttu-id="41595-186">Mode de commande VI : `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="41595-186">Vi command mode: `<Ctrl+Backspace>`</span></span>

### <a name="cancelline"></a><span data-ttu-id="41595-187">CancelLine</span><span class="sxs-lookup"><span data-stu-id="41595-187">CancelLine</span></span>

<span data-ttu-id="41595-188">Annule l’entrée actuelle, en laissant l’entrée à l’écran, mais retourne à l’hôte afin que l’invite soit de nouveau évaluée.</span><span class="sxs-lookup"><span data-stu-id="41595-188">Cancel the current input, leaving the input on the screen, but returns back to the host so the prompt is evaluated again.</span></span>

- <span data-ttu-id="41595-189">Mode d’insertion VI : `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="41595-189">Vi insert mode: `<Ctrl+c>`</span></span>
- <span data-ttu-id="41595-190">Mode de commande VI : `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="41595-190">Vi command mode: `<Ctrl+c>`</span></span>

### <a name="copy"></a><span data-ttu-id="41595-191">Copier</span><span class="sxs-lookup"><span data-stu-id="41595-191">Copy</span></span>

<span data-ttu-id="41595-192">Copier la région sélectionnée dans le presse-papiers du système.</span><span class="sxs-lookup"><span data-stu-id="41595-192">Copy selected region to the system clipboard.</span></span> <span data-ttu-id="41595-193">Si aucune région n’est sélectionnée, copiez la ligne entière.</span><span class="sxs-lookup"><span data-stu-id="41595-193">If no region is selected, copy the whole line.</span></span>

- <span data-ttu-id="41595-194">Cmd `<Ctrl+C>`</span><span class="sxs-lookup"><span data-stu-id="41595-194">Cmd: `<Ctrl+C>`</span></span>

### <a name="copyorcancelline"></a><span data-ttu-id="41595-195">CopyOrCancelLine</span><span class="sxs-lookup"><span data-stu-id="41595-195">CopyOrCancelLine</span></span>

<span data-ttu-id="41595-196">Si le texte est sélectionné, copiez-le dans le presse-papiers, sinon, annulez la ligne.</span><span class="sxs-lookup"><span data-stu-id="41595-196">If text is selected, copy to the clipboard, otherwise cancel the line.</span></span>

- <span data-ttu-id="41595-197">Cmd `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="41595-197">Cmd: `<Ctrl+c>`</span></span>
- <span data-ttu-id="41595-198">Emacs- `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="41595-198">Emacs: `<Ctrl+c>`</span></span>

### <a name="cut"></a><span data-ttu-id="41595-199">Couper</span><span class="sxs-lookup"><span data-stu-id="41595-199">Cut</span></span>

<span data-ttu-id="41595-200">Supprimer la zone sélectionnée en plaçant le texte supprimé dans le presse-papiers du système.</span><span class="sxs-lookup"><span data-stu-id="41595-200">Delete selected region placing deleted text in the system clipboard.</span></span>

- <span data-ttu-id="41595-201">Cmd `<Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="41595-201">Cmd: `<Ctrl+x>`</span></span>

### <a name="deletechar"></a><span data-ttu-id="41595-202">DeleteChar</span><span class="sxs-lookup"><span data-stu-id="41595-202">DeleteChar</span></span>

<span data-ttu-id="41595-203">Supprimez le caractère sous le curseur.</span><span class="sxs-lookup"><span data-stu-id="41595-203">Delete the character under the cursor.</span></span>

- <span data-ttu-id="41595-204">Cmd `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="41595-204">Cmd: `<Delete>`</span></span>
- <span data-ttu-id="41595-205">Emacs- `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="41595-205">Emacs: `<Delete>`</span></span>
- <span data-ttu-id="41595-206">Mode d’insertion VI : `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="41595-206">Vi insert mode: `<Delete>`</span></span>
- <span data-ttu-id="41595-207">Mode de commande VI : `<Delete>` , `<x>` , `<d,l>` , `<d,Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="41595-207">Vi command mode: `<Delete>`, `<x>`, `<d,l>`, `<d,Spacebar>`</span></span>

### <a name="deletecharorexit"></a><span data-ttu-id="41595-208">DeleteCharOrExit</span><span class="sxs-lookup"><span data-stu-id="41595-208">DeleteCharOrExit</span></span>

<span data-ttu-id="41595-209">Supprimez le caractère sous le curseur, ou si la ligne est vide, quittez le processus.</span><span class="sxs-lookup"><span data-stu-id="41595-209">Delete the character under the cursor, or if the line is empty, exit the process.</span></span>

- <span data-ttu-id="41595-210">Emacs- `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="41595-210">Emacs: `<Ctrl+d>`</span></span>

### <a name="deleteendofbuffer"></a><span data-ttu-id="41595-211">DeleteEndOfBuffer</span><span class="sxs-lookup"><span data-stu-id="41595-211">DeleteEndOfBuffer</span></span>

<span data-ttu-id="41595-212">Supprime à la fin de la mémoire tampon multiligne.</span><span class="sxs-lookup"><span data-stu-id="41595-212">Deletes to the end of the multiline buffer.</span></span>

- <span data-ttu-id="41595-213">Mode de commande VI : `<d,G>`</span><span class="sxs-lookup"><span data-stu-id="41595-213">Vi command mode: `<d,G>`</span></span>

### <a name="deleteendofword"></a><span data-ttu-id="41595-214">DeleteEndOfWord</span><span class="sxs-lookup"><span data-stu-id="41595-214">DeleteEndOfWord</span></span>

<span data-ttu-id="41595-215">Supprimer à la fin du mot.</span><span class="sxs-lookup"><span data-stu-id="41595-215">Delete to the end of the word.</span></span>

- <span data-ttu-id="41595-216">Mode de commande VI : `<d,e>`</span><span class="sxs-lookup"><span data-stu-id="41595-216">Vi command mode: `<d,e>`</span></span>

### <a name="deleteline"></a><span data-ttu-id="41595-217">DeleteLine</span><span class="sxs-lookup"><span data-stu-id="41595-217">DeleteLine</span></span>

<span data-ttu-id="41595-218">Supprime la ligne logique actuelle d’une mémoire tampon multiligne, ce qui permet d’annuler.</span><span class="sxs-lookup"><span data-stu-id="41595-218">Deletes the current logical line of a multiline buffer, enabling undo.</span></span>

- <span data-ttu-id="41595-219">Mode de commande VI : `<d,d>` , `<d,_>`</span><span class="sxs-lookup"><span data-stu-id="41595-219">Vi command mode: `<d,d>`, `<d,_>`</span></span>

### <a name="deletepreviouslines"></a><span data-ttu-id="41595-220">DeletePreviousLines</span><span class="sxs-lookup"><span data-stu-id="41595-220">DeletePreviousLines</span></span>

<span data-ttu-id="41595-221">Supprime les lignes logiques requises précédentes et la ligne logique actuelle dans une mémoire tampon multiligne.</span><span class="sxs-lookup"><span data-stu-id="41595-221">Deletes the previous requested logical lines and the current logical line in a multiline buffer.</span></span>

- <span data-ttu-id="41595-222">Mode de commande VI : `<d,k>`</span><span class="sxs-lookup"><span data-stu-id="41595-222">Vi command mode: `<d,k>`</span></span>

### <a name="deleterelativelines"></a><span data-ttu-id="41595-223">DeleteRelativeLines</span><span class="sxs-lookup"><span data-stu-id="41595-223">DeleteRelativeLines</span></span>

<span data-ttu-id="41595-224">Supprime du début de la mémoire tampon jusqu’à la ligne logique actuelle dans une mémoire tampon multiligne.</span><span class="sxs-lookup"><span data-stu-id="41595-224">Deletes from the beginning of the buffer to the current logical line in a multiline buffer.</span></span>

<span data-ttu-id="41595-225">Comme la plupart des commandes VI, la `<d,g,g>` commande peut être précédée d’un argument numérique qui spécifie un numéro de ligne absolu, qui, avec le numéro de ligne en cours, compose une plage de lignes à supprimer.</span><span class="sxs-lookup"><span data-stu-id="41595-225">As most Vi commands, the `<d,g,g>` command can be prepended with a numeric argument that specifies an absolute line number, which, together with the current line number, make up a range of lines to be deleted.</span></span>
<span data-ttu-id="41595-226">S’il n’est pas spécifié, l’argument numérique a la valeur par défaut 1, qui fait référence à la première ligne logique dans une mémoire tampon multiligne.</span><span class="sxs-lookup"><span data-stu-id="41595-226">If not specified, the numeric argument defaults to 1, which refers to the first logical line in a multiline buffer.</span></span>

<span data-ttu-id="41595-227">Le nombre réel de lignes à supprimer de la ligne multiligne est calculé comme étant la différence entre le numéro de ligne logique actuel et l’argument numérique spécifié, qui peut donc être négatif.</span><span class="sxs-lookup"><span data-stu-id="41595-227">The actual number of lines to be deleted from the multiline is computed as the difference between the current logical line number and the specified numeric argument, which can thus be negative.</span></span> <span data-ttu-id="41595-228">Par conséquent, la partie _relative_ du nom de la méthode.</span><span class="sxs-lookup"><span data-stu-id="41595-228">Hence the _relative_ part of method name.</span></span>

- <span data-ttu-id="41595-229">Mode de commande VI : `<d,g,g>`</span><span class="sxs-lookup"><span data-stu-id="41595-229">Vi command mode: `<d,g,g>`</span></span>

### <a name="deletenextlines"></a><span data-ttu-id="41595-230">DeleteNextLines</span><span class="sxs-lookup"><span data-stu-id="41595-230">DeleteNextLines</span></span>

<span data-ttu-id="41595-231">Supprime la ligne logique actuelle et les lignes logiques suivantes demandées dans une mémoire tampon multiligne.</span><span class="sxs-lookup"><span data-stu-id="41595-231">Deletes the current logical line and the next requested logical lines in a multiline buffer.</span></span>

- <span data-ttu-id="41595-232">Mode de commande VI : `<d,j>`</span><span class="sxs-lookup"><span data-stu-id="41595-232">Vi command mode: `<d,j>`</span></span>

### <a name="deletelinetofirstchar"></a><span data-ttu-id="41595-233">DeleteLineToFirstChar</span><span class="sxs-lookup"><span data-stu-id="41595-233">DeleteLineToFirstChar</span></span>

<span data-ttu-id="41595-234">Supprime le texte du curseur jusqu’au premier caractère non vide de la ligne.</span><span class="sxs-lookup"><span data-stu-id="41595-234">Deletes text from the cursor to the first non-blank character of the line.</span></span>

- <span data-ttu-id="41595-235">Mode de commande VI : `<d,^>`</span><span class="sxs-lookup"><span data-stu-id="41595-235">Vi command mode: `<d,^>`</span></span>

### <a name="deletetoend"></a><span data-ttu-id="41595-236">DeleteToEnd</span><span class="sxs-lookup"><span data-stu-id="41595-236">DeleteToEnd</span></span>

<span data-ttu-id="41595-237">Supprimer à la fin de la ligne.</span><span class="sxs-lookup"><span data-stu-id="41595-237">Delete to the end of the line.</span></span>

- <span data-ttu-id="41595-238">Mode de commande VI : `<D>` , `<d,$>`</span><span class="sxs-lookup"><span data-stu-id="41595-238">Vi command mode: `<D>`, `<d,$>`</span></span>

### <a name="deleteword"></a><span data-ttu-id="41595-239">DeleteWord</span><span class="sxs-lookup"><span data-stu-id="41595-239">DeleteWord</span></span>

<span data-ttu-id="41595-240">Supprimer le mot suivant.</span><span class="sxs-lookup"><span data-stu-id="41595-240">Delete the next word.</span></span>

- <span data-ttu-id="41595-241">Mode de commande VI : `<d,w>`</span><span class="sxs-lookup"><span data-stu-id="41595-241">Vi command mode: `<d,w>`</span></span>

### <a name="forwarddeleteline"></a><span data-ttu-id="41595-242">ForwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="41595-242">ForwardDeleteLine</span></span>

<span data-ttu-id="41595-243">Comme ForwardKillLine-supprime le texte du point jusqu’à la fin de la ligne, mais ne place pas le texte supprimé dans l’anneau Kill.</span><span class="sxs-lookup"><span data-stu-id="41595-243">Like ForwardKillLine - deletes text from the point to the end of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="41595-244">Cmd `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="41595-244">Cmd: `<Ctrl+End>`</span></span>
- <span data-ttu-id="41595-245">Mode d’insertion VI : `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="41595-245">Vi insert mode: `<Ctrl+End>`</span></span>
- <span data-ttu-id="41595-246">Mode de commande VI : `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="41595-246">Vi command mode: `<Ctrl+End>`</span></span>

### <a name="insertlineabove"></a><span data-ttu-id="41595-247">InsertLineAbove</span><span class="sxs-lookup"><span data-stu-id="41595-247">InsertLineAbove</span></span>

<span data-ttu-id="41595-248">Une nouvelle ligne vide est créée au-dessus de la ligne active, quel que soit l’endroit où se trouve le curseur sur la ligne active.</span><span class="sxs-lookup"><span data-stu-id="41595-248">A new empty line is created above the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="41595-249">Le curseur se déplace au début de la nouvelle ligne.</span><span class="sxs-lookup"><span data-stu-id="41595-249">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="41595-250">Cmd `<Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="41595-250">Cmd: `<Ctrl+Enter>`</span></span>

### <a name="insertlinebelow"></a><span data-ttu-id="41595-251">InsertLineBelow</span><span class="sxs-lookup"><span data-stu-id="41595-251">InsertLineBelow</span></span>

<span data-ttu-id="41595-252">Une nouvelle ligne vide est créée sous la ligne active, quel que soit l’endroit où se trouve le curseur sur la ligne active.</span><span class="sxs-lookup"><span data-stu-id="41595-252">A new empty line is created below the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="41595-253">Le curseur se déplace au début de la nouvelle ligne.</span><span class="sxs-lookup"><span data-stu-id="41595-253">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="41595-254">Cmd `<Shift+Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="41595-254">Cmd: `<Shift+Ctrl+Enter>`</span></span>

### <a name="invertcase"></a><span data-ttu-id="41595-255">InvertCase</span><span class="sxs-lookup"><span data-stu-id="41595-255">InvertCase</span></span>

<span data-ttu-id="41595-256">Inverser la casse du caractère actuel et passer au suivant.</span><span class="sxs-lookup"><span data-stu-id="41595-256">Invert the case of the current character and move to the next one.</span></span>

- <span data-ttu-id="41595-257">Mode de commande VI : `<~>`</span><span class="sxs-lookup"><span data-stu-id="41595-257">Vi command mode: `<~>`</span></span>

### <a name="killline"></a><span data-ttu-id="41595-258">KillLine</span><span class="sxs-lookup"><span data-stu-id="41595-258">KillLine</span></span>

<span data-ttu-id="41595-259">Effacez l’entrée du curseur jusqu’à la fin de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="41595-259">Clear the input from the cursor to the end of the input.</span></span> <span data-ttu-id="41595-260">Le texte effacé est placé dans le Kill-Ring.</span><span class="sxs-lookup"><span data-stu-id="41595-260">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="41595-261">Emacs- `<Ctrl+k>`</span><span class="sxs-lookup"><span data-stu-id="41595-261">Emacs: `<Ctrl+k>`</span></span>

### <a name="killregion"></a><span data-ttu-id="41595-262">KillRegion</span><span class="sxs-lookup"><span data-stu-id="41595-262">KillRegion</span></span>

<span data-ttu-id="41595-263">Supprimer le texte situé entre le curseur et la marque.</span><span class="sxs-lookup"><span data-stu-id="41595-263">Kill the text between the cursor and the mark.</span></span>

- <span data-ttu-id="41595-264">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="41595-264">Function is unbound.</span></span>

### <a name="killword"></a><span data-ttu-id="41595-265">KillWord</span><span class="sxs-lookup"><span data-stu-id="41595-265">KillWord</span></span>

<span data-ttu-id="41595-266">Efface l’entrée du curseur jusqu’à la fin du mot actuel.</span><span class="sxs-lookup"><span data-stu-id="41595-266">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="41595-267">Si le curseur se trouve entre des mots, l’entrée est effacée du curseur jusqu’à la fin du mot suivant.</span><span class="sxs-lookup"><span data-stu-id="41595-267">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="41595-268">Le texte effacé est placé dans le Kill-Ring.</span><span class="sxs-lookup"><span data-stu-id="41595-268">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="41595-269">Cmd : `<Alt+d>` , `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="41595-269">Cmd: `<Alt+d>`, `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="41595-270">Emacs- `<Alt+d>` , `<Escape,d>`</span><span class="sxs-lookup"><span data-stu-id="41595-270">Emacs: `<Alt+d>`, `<Escape,d>`</span></span>
- <span data-ttu-id="41595-271">Mode d’insertion VI : `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="41595-271">Vi insert mode: `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="41595-272">Mode de commande VI : `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="41595-272">Vi command mode: `<Ctrl+Delete>`</span></span>

### <a name="paste"></a><span data-ttu-id="41595-273">Coller</span><span class="sxs-lookup"><span data-stu-id="41595-273">Paste</span></span>

<span data-ttu-id="41595-274">Collez le texte à partir du presse-papiers du système.</span><span class="sxs-lookup"><span data-stu-id="41595-274">Paste text from the system clipboard.</span></span>

- <span data-ttu-id="41595-275">Cmd : `<Ctrl+v>` , `<Shift+Insert>`</span><span class="sxs-lookup"><span data-stu-id="41595-275">Cmd: `<Ctrl+v>`, `<Shift+Insert>`</span></span>
- <span data-ttu-id="41595-276">Mode d’insertion VI : `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="41595-276">Vi insert mode: `<Ctrl+v>`</span></span>
- <span data-ttu-id="41595-277">Mode de commande VI : `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="41595-277">Vi command mode: `<Ctrl+v>`</span></span>

> [!IMPORTANT]
> <span data-ttu-id="41595-278">Lors de l’utilisation de la fonction **Paste** , le contenu entier de la mémoire tampon du presse-papiers est collé dans la mémoire tampon d’entrée de PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="41595-278">When using the **Paste** function, the entire contents of the clipboard buffer is pasted into the input buffer of PSReadLine.</span></span> <span data-ttu-id="41595-279">La mémoire tampon d’entrée est ensuite transmise à l’analyseur PowerShell.</span><span class="sxs-lookup"><span data-stu-id="41595-279">The input buffer is then passed to the PowerShell parser.</span></span> <span data-ttu-id="41595-280">L’entrée collée à l’aide de la méthode de collage **avec le bouton droit** de la console de l’application de console est copiée dans la mémoire tampon d’entrée un caractère à la fois.</span><span class="sxs-lookup"><span data-stu-id="41595-280">Input pasted using the console application's **right-click** paste method is copied to the input buffer one character at a time.</span></span> <span data-ttu-id="41595-281">La mémoire tampon d’entrée est transmise à l’analyseur lorsqu’un caractère de saut de ligne est copié.</span><span class="sxs-lookup"><span data-stu-id="41595-281">The input buffer is passed to the parser when a newline character is copied.</span></span> <span data-ttu-id="41595-282">Par conséquent, l’entrée est analysée une ligne à la fois.</span><span class="sxs-lookup"><span data-stu-id="41595-282">Therefore, the input is parsed one line at a time.</span></span> <span data-ttu-id="41595-283">La différence entre les méthodes de collage entraîne un comportement d’exécution différent.</span><span class="sxs-lookup"><span data-stu-id="41595-283">The difference between paste methods results in different execution behavior.</span></span>

### <a name="pasteafter"></a><span data-ttu-id="41595-284">PasteAfter</span><span class="sxs-lookup"><span data-stu-id="41595-284">PasteAfter</span></span>

<span data-ttu-id="41595-285">Collez le presse-papiers après le curseur, en déplaçant le curseur à la fin du texte collé.</span><span class="sxs-lookup"><span data-stu-id="41595-285">Paste the clipboard after the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="41595-286">Mode de commande VI : `<p>`</span><span class="sxs-lookup"><span data-stu-id="41595-286">Vi command mode: `<p>`</span></span>

### <a name="pastebefore"></a><span data-ttu-id="41595-287">PasteBefore</span><span class="sxs-lookup"><span data-stu-id="41595-287">PasteBefore</span></span>

<span data-ttu-id="41595-288">Collez le presse-papiers avant le curseur, en déplaçant le curseur à la fin du texte collé.</span><span class="sxs-lookup"><span data-stu-id="41595-288">Paste the clipboard before the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="41595-289">Mode de commande VI : `<P>`</span><span class="sxs-lookup"><span data-stu-id="41595-289">Vi command mode: `<P>`</span></span>

### <a name="prependandaccept"></a><span data-ttu-id="41595-290">PrependAndAccept</span><span class="sxs-lookup"><span data-stu-id="41595-290">PrependAndAccept</span></span>

<span data-ttu-id="41595-291">Faites précéder un' # 'et acceptez la ligne.</span><span class="sxs-lookup"><span data-stu-id="41595-291">Prepend a '#' and accept the line.</span></span>

- <span data-ttu-id="41595-292">Mode de commande VI : `<#>`</span><span class="sxs-lookup"><span data-stu-id="41595-292">Vi command mode: `<#>`</span></span>

### <a name="redo"></a><span data-ttu-id="41595-293">Rétablir</span><span class="sxs-lookup"><span data-stu-id="41595-293">Redo</span></span>

<span data-ttu-id="41595-294">Annule une annulation.</span><span class="sxs-lookup"><span data-stu-id="41595-294">Undo an undo.</span></span>

- <span data-ttu-id="41595-295">Cmd `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="41595-295">Cmd: `<Ctrl+y>`</span></span>
- <span data-ttu-id="41595-296">Mode d’insertion VI : `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="41595-296">Vi insert mode: `<Ctrl+y>`</span></span>
- <span data-ttu-id="41595-297">Mode de commande VI : `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="41595-297">Vi command mode: `<Ctrl+y>`</span></span>

### <a name="repeatlastcommand"></a><span data-ttu-id="41595-298">RepeatLastCommand</span><span class="sxs-lookup"><span data-stu-id="41595-298">RepeatLastCommand</span></span>

<span data-ttu-id="41595-299">Répète la dernière modification de texte.</span><span class="sxs-lookup"><span data-stu-id="41595-299">Repeat the last text modification.</span></span>

- <span data-ttu-id="41595-300">Mode de commande VI : `<.>`</span><span class="sxs-lookup"><span data-stu-id="41595-300">Vi command mode: `<.>`</span></span>

### <a name="revertline"></a><span data-ttu-id="41595-301">RevertLine</span><span class="sxs-lookup"><span data-stu-id="41595-301">RevertLine</span></span>

<span data-ttu-id="41595-302">Rétablit toutes les entrées de l’entrée actuelle.</span><span class="sxs-lookup"><span data-stu-id="41595-302">Reverts all of the input to the current input.</span></span>

- <span data-ttu-id="41595-303">Cmd `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="41595-303">Cmd: `<Escape>`</span></span>
- <span data-ttu-id="41595-304">Emacs- `<Alt+r>` , `<Escape,r>`</span><span class="sxs-lookup"><span data-stu-id="41595-304">Emacs: `<Alt+r>`, `<Escape,r>`</span></span>

### <a name="shellbackwardkillword"></a><span data-ttu-id="41595-305">ShellBackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="41595-305">ShellBackwardKillWord</span></span>

<span data-ttu-id="41595-306">Efface l’entrée du début du mot actuel jusqu’au curseur.</span><span class="sxs-lookup"><span data-stu-id="41595-306">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="41595-307">Si le curseur se trouve entre des mots, l’entrée est effacée du début du mot précédent au curseur.</span><span class="sxs-lookup"><span data-stu-id="41595-307">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="41595-308">Le texte effacé est placé dans le Kill-Ring.</span><span class="sxs-lookup"><span data-stu-id="41595-308">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="41595-309">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="41595-309">Function is unbound.</span></span>

### <a name="shellkillword"></a><span data-ttu-id="41595-310">ShellKillWord</span><span class="sxs-lookup"><span data-stu-id="41595-310">ShellKillWord</span></span>

<span data-ttu-id="41595-311">Efface l’entrée du curseur jusqu’à la fin du mot actuel.</span><span class="sxs-lookup"><span data-stu-id="41595-311">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="41595-312">Si le curseur se trouve entre des mots, l’entrée est effacée du curseur jusqu’à la fin du mot suivant.</span><span class="sxs-lookup"><span data-stu-id="41595-312">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="41595-313">Le texte effacé est placé dans le Kill-Ring.</span><span class="sxs-lookup"><span data-stu-id="41595-313">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="41595-314">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="41595-314">Function is unbound.</span></span>

### <a name="swapcharacters"></a><span data-ttu-id="41595-315">SwapCharacters</span><span class="sxs-lookup"><span data-stu-id="41595-315">SwapCharacters</span></span>

<span data-ttu-id="41595-316">Permuter le caractère actuel et celui qui le précèdent.</span><span class="sxs-lookup"><span data-stu-id="41595-316">Swap the current character and the one before it.</span></span>

- <span data-ttu-id="41595-317">Emacs- `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="41595-317">Emacs: `<Ctrl+t>`</span></span>
- <span data-ttu-id="41595-318">Mode d’insertion VI : `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="41595-318">Vi insert mode: `<Ctrl+t>`</span></span>
- <span data-ttu-id="41595-319">Mode de commande VI : `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="41595-319">Vi command mode: `<Ctrl+t>`</span></span>

### <a name="undo"></a><span data-ttu-id="41595-320">Annuler</span><span class="sxs-lookup"><span data-stu-id="41595-320">Undo</span></span>

<span data-ttu-id="41595-321">Annuler une modification précédente.</span><span class="sxs-lookup"><span data-stu-id="41595-321">Undo a previous edit.</span></span>

- <span data-ttu-id="41595-322">Cmd `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="41595-322">Cmd: `<Ctrl+z>`</span></span>
- <span data-ttu-id="41595-323">Emacs- `<Ctrl+_>` , `<Ctrl+x,Ctrl+u>`</span><span class="sxs-lookup"><span data-stu-id="41595-323">Emacs: `<Ctrl+_>`, `<Ctrl+x,Ctrl+u>`</span></span>
- <span data-ttu-id="41595-324">Mode d’insertion VI : `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="41595-324">Vi insert mode: `<Ctrl+z>`</span></span>
- <span data-ttu-id="41595-325">Mode de commande VI : `<Ctrl+z>` , `<u>`</span><span class="sxs-lookup"><span data-stu-id="41595-325">Vi command mode: `<Ctrl+z>`, `<u>`</span></span>

### <a name="undoall"></a><span data-ttu-id="41595-326">UndoAll</span><span class="sxs-lookup"><span data-stu-id="41595-326">UndoAll</span></span>

<span data-ttu-id="41595-327">Annule toutes les modifications précédentes pour la ligne.</span><span class="sxs-lookup"><span data-stu-id="41595-327">Undo all previous edits for line.</span></span>

- <span data-ttu-id="41595-328">Mode de commande VI : `<U>`</span><span class="sxs-lookup"><span data-stu-id="41595-328">Vi command mode: `<U>`</span></span>

### <a name="unixwordrubout"></a><span data-ttu-id="41595-329">UnixWordRubout</span><span class="sxs-lookup"><span data-stu-id="41595-329">UnixWordRubout</span></span>

<span data-ttu-id="41595-330">Efface l’entrée du début du mot actuel jusqu’au curseur.</span><span class="sxs-lookup"><span data-stu-id="41595-330">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="41595-331">Si le curseur se trouve entre des mots, l’entrée est effacée du début du mot précédent au curseur.</span><span class="sxs-lookup"><span data-stu-id="41595-331">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="41595-332">Le texte effacé est placé dans le Kill-Ring.</span><span class="sxs-lookup"><span data-stu-id="41595-332">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="41595-333">Emacs- `<Ctrl+w>`</span><span class="sxs-lookup"><span data-stu-id="41595-333">Emacs: `<Ctrl+w>`</span></span>

### <a name="validateandacceptline"></a><span data-ttu-id="41595-334">ValidateAndAcceptLine</span><span class="sxs-lookup"><span data-stu-id="41595-334">ValidateAndAcceptLine</span></span>

<span data-ttu-id="41595-335">Tentative d’exécution de l’entrée en cours.</span><span class="sxs-lookup"><span data-stu-id="41595-335">Attempt to execute the current input.</span></span> <span data-ttu-id="41595-336">Si l’entrée actuelle est incomplète (par exemple, il manque une parenthèse fermante, un crochet ou un guillemet, l’invite de continuation est affichée sur la ligne suivante et PSReadLine attend que les clés modifient l’entrée actuelle.</span><span class="sxs-lookup"><span data-stu-id="41595-336">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="41595-337">Emacs- `<Ctrl+m>`</span><span class="sxs-lookup"><span data-stu-id="41595-337">Emacs: `<Ctrl+m>`</span></span>

### <a name="viacceptline"></a><span data-ttu-id="41595-338">ViAcceptLine</span><span class="sxs-lookup"><span data-stu-id="41595-338">ViAcceptLine</span></span>

<span data-ttu-id="41595-339">Acceptez la ligne et passez en mode insertion.</span><span class="sxs-lookup"><span data-stu-id="41595-339">Accept the line and switch to Insert mode.</span></span>

- <span data-ttu-id="41595-340">Mode de commande VI : `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="41595-340">Vi command mode: `<Enter>`</span></span>

### <a name="viacceptlineorexit"></a><span data-ttu-id="41595-341">ViAcceptLineOrExit</span><span class="sxs-lookup"><span data-stu-id="41595-341">ViAcceptLineOrExit</span></span>

<span data-ttu-id="41595-342">Comme DeleteCharOrExit en mode emacs, mais accepte la ligne au lieu de supprimer un caractère.</span><span class="sxs-lookup"><span data-stu-id="41595-342">Like DeleteCharOrExit in Emacs mode, but accepts the line instead of deleting a character.</span></span>

- <span data-ttu-id="41595-343">Mode d’insertion VI : `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="41595-343">Vi insert mode: `<Ctrl+d>`</span></span>
- <span data-ttu-id="41595-344">Mode de commande VI : `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="41595-344">Vi command mode: `<Ctrl+d>`</span></span>

### <a name="viappendline"></a><span data-ttu-id="41595-345">ViAppendLine</span><span class="sxs-lookup"><span data-stu-id="41595-345">ViAppendLine</span></span>

<span data-ttu-id="41595-346">Une nouvelle ligne est insérée au-dessous de la ligne active.</span><span class="sxs-lookup"><span data-stu-id="41595-346">A new line is inserted below the current line.</span></span>

- <span data-ttu-id="41595-347">Mode de commande VI : `<o>`</span><span class="sxs-lookup"><span data-stu-id="41595-347">Vi command mode: `<o>`</span></span>

### <a name="vibackwarddeleteglob"></a><span data-ttu-id="41595-348">ViBackwardDeleteGlob</span><span class="sxs-lookup"><span data-stu-id="41595-348">ViBackwardDeleteGlob</span></span>

<span data-ttu-id="41595-349">Supprime le mot précédent, en utilisant uniquement un espace blanc comme délimiteur de mot.</span><span class="sxs-lookup"><span data-stu-id="41595-349">Deletes the previous word, using only white space as the word delimiter.</span></span>

- <span data-ttu-id="41595-350">Mode de commande VI : `<d,B>`</span><span class="sxs-lookup"><span data-stu-id="41595-350">Vi command mode: `<d,B>`</span></span>

### <a name="vibackwardglob"></a><span data-ttu-id="41595-351">ViBackwardGlob</span><span class="sxs-lookup"><span data-stu-id="41595-351">ViBackwardGlob</span></span>

<span data-ttu-id="41595-352">Déplace le curseur au début du mot précédent, en utilisant uniquement des espaces blancs comme délimiteurs.</span><span class="sxs-lookup"><span data-stu-id="41595-352">Moves the cursor back to the beginning of the previous word, using only white space as delimiters.</span></span>

- <span data-ttu-id="41595-353">Mode de commande VI : `<B>`</span><span class="sxs-lookup"><span data-stu-id="41595-353">Vi command mode: `<B>`</span></span>

### <a name="videletebrace"></a><span data-ttu-id="41595-354">ViDeleteBrace</span><span class="sxs-lookup"><span data-stu-id="41595-354">ViDeleteBrace</span></span>

<span data-ttu-id="41595-355">Recherchez l’accolade correspondante, la parenthèse ou le crochet, et supprimez tout le contenu dans, y compris l’accolade.</span><span class="sxs-lookup"><span data-stu-id="41595-355">Find the matching brace, parenthesis, or square bracket and delete all contents within, including the brace.</span></span>

- <span data-ttu-id="41595-356">Mode de commande VI : `<d,%>`</span><span class="sxs-lookup"><span data-stu-id="41595-356">Vi command mode: `<d,%>`</span></span>

### <a name="videleteendofglob"></a><span data-ttu-id="41595-357">ViDeleteEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="41595-357">ViDeleteEndOfGlob</span></span>

<span data-ttu-id="41595-358">Supprimer à la fin du mot.</span><span class="sxs-lookup"><span data-stu-id="41595-358">Delete to the end of the word.</span></span>

- <span data-ttu-id="41595-359">Mode de commande VI : `<d,E>`</span><span class="sxs-lookup"><span data-stu-id="41595-359">Vi command mode: `<d,E>`</span></span>

### <a name="videleteglob"></a><span data-ttu-id="41595-360">ViDeleteGlob</span><span class="sxs-lookup"><span data-stu-id="41595-360">ViDeleteGlob</span></span>

<span data-ttu-id="41595-361">Supprime la glob suivante (mot blanc délimité par des espaces).</span><span class="sxs-lookup"><span data-stu-id="41595-361">Delete the next glob (white space delimited word).</span></span>

- <span data-ttu-id="41595-362">Mode de commande VI : `<d,W>`</span><span class="sxs-lookup"><span data-stu-id="41595-362">Vi command mode: `<d,W>`</span></span>

### <a name="videletetobeforechar"></a><span data-ttu-id="41595-363">ViDeleteToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="41595-363">ViDeleteToBeforeChar</span></span>

<span data-ttu-id="41595-364">Supprime jusqu’au caractère donné.</span><span class="sxs-lookup"><span data-stu-id="41595-364">Deletes until given character.</span></span>

- <span data-ttu-id="41595-365">Mode de commande VI : `<d,t>`</span><span class="sxs-lookup"><span data-stu-id="41595-365">Vi command mode: `<d,t>`</span></span>

### <a name="videletetobeforecharbackward"></a><span data-ttu-id="41595-366">ViDeleteToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="41595-366">ViDeleteToBeforeCharBackward</span></span>

<span data-ttu-id="41595-367">Supprime jusqu’au caractère donné.</span><span class="sxs-lookup"><span data-stu-id="41595-367">Deletes until given character.</span></span>

- <span data-ttu-id="41595-368">Mode de commande VI : `<d,T>`</span><span class="sxs-lookup"><span data-stu-id="41595-368">Vi command mode: `<d,T>`</span></span>

### <a name="videletetochar"></a><span data-ttu-id="41595-369">ViDeleteToChar</span><span class="sxs-lookup"><span data-stu-id="41595-369">ViDeleteToChar</span></span>

<span data-ttu-id="41595-370">Supprime jusqu’au caractère donné.</span><span class="sxs-lookup"><span data-stu-id="41595-370">Deletes until given character.</span></span>

- <span data-ttu-id="41595-371">Mode de commande VI : `<d,f>`</span><span class="sxs-lookup"><span data-stu-id="41595-371">Vi command mode: `<d,f>`</span></span>

### <a name="videletetocharbackward"></a><span data-ttu-id="41595-372">ViDeleteToCharBackward</span><span class="sxs-lookup"><span data-stu-id="41595-372">ViDeleteToCharBackward</span></span>

<span data-ttu-id="41595-373">Supprime vers l’arrière jusqu’au caractère donné.</span><span class="sxs-lookup"><span data-stu-id="41595-373">Deletes backwards until given character.</span></span>

- <span data-ttu-id="41595-374">Mode de commande VI : `<d,F>`</span><span class="sxs-lookup"><span data-stu-id="41595-374">Vi command mode: `<d,F>`</span></span>

### <a name="viinsertatbegining"></a><span data-ttu-id="41595-375">ViInsertAtBegining</span><span class="sxs-lookup"><span data-stu-id="41595-375">ViInsertAtBegining</span></span>

<span data-ttu-id="41595-376">Basculez en mode insertion et positionnez le curseur au début de la ligne.</span><span class="sxs-lookup"><span data-stu-id="41595-376">Switch to Insert mode and position the cursor at the beginning of the line.</span></span>

- <span data-ttu-id="41595-377">Mode de commande VI : `<I>`</span><span class="sxs-lookup"><span data-stu-id="41595-377">Vi command mode: `<I>`</span></span>

### <a name="viinsertatend"></a><span data-ttu-id="41595-378">ViInsertAtEnd</span><span class="sxs-lookup"><span data-stu-id="41595-378">ViInsertAtEnd</span></span>

<span data-ttu-id="41595-379">Basculez en mode insertion et positionnez le curseur à la fin de la ligne.</span><span class="sxs-lookup"><span data-stu-id="41595-379">Switch to Insert mode and position the cursor at the end of the line.</span></span>

- <span data-ttu-id="41595-380">Mode de commande VI : `<A>`</span><span class="sxs-lookup"><span data-stu-id="41595-380">Vi command mode: `<A>`</span></span>

### <a name="viinsertline"></a><span data-ttu-id="41595-381">ViInsertLine</span><span class="sxs-lookup"><span data-stu-id="41595-381">ViInsertLine</span></span>

<span data-ttu-id="41595-382">Une nouvelle ligne est insérée au-dessus de la ligne active.</span><span class="sxs-lookup"><span data-stu-id="41595-382">A new line is inserted above the current line.</span></span>

- <span data-ttu-id="41595-383">Mode de commande VI : `<O>`</span><span class="sxs-lookup"><span data-stu-id="41595-383">Vi command mode: `<O>`</span></span>

### <a name="viinsertwithappend"></a><span data-ttu-id="41595-384">ViInsertWithAppend</span><span class="sxs-lookup"><span data-stu-id="41595-384">ViInsertWithAppend</span></span>

<span data-ttu-id="41595-385">Ajouter à partir de la position de la ligne active.</span><span class="sxs-lookup"><span data-stu-id="41595-385">Append from the current line position.</span></span>

- <span data-ttu-id="41595-386">Mode de commande VI : `<a>`</span><span class="sxs-lookup"><span data-stu-id="41595-386">Vi command mode: `<a>`</span></span>

### <a name="viinsertwithdelete"></a><span data-ttu-id="41595-387">ViInsertWithDelete</span><span class="sxs-lookup"><span data-stu-id="41595-387">ViInsertWithDelete</span></span>

<span data-ttu-id="41595-388">Supprimez le caractère actuel et basculez en mode insertion.</span><span class="sxs-lookup"><span data-stu-id="41595-388">Delete the current character and switch to Insert mode.</span></span>

- <span data-ttu-id="41595-389">Mode de commande VI : `<s>`</span><span class="sxs-lookup"><span data-stu-id="41595-389">Vi command mode: `<s>`</span></span>

### <a name="vijoinlines"></a><span data-ttu-id="41595-390">ViJoinLines</span><span class="sxs-lookup"><span data-stu-id="41595-390">ViJoinLines</span></span>

<span data-ttu-id="41595-391">Joint la ligne active et la ligne suivante.</span><span class="sxs-lookup"><span data-stu-id="41595-391">Joins the current line and the next line.</span></span>

- <span data-ttu-id="41595-392">Mode de commande VI : `<J>`</span><span class="sxs-lookup"><span data-stu-id="41595-392">Vi command mode: `<J>`</span></span>

### <a name="vireplaceline"></a><span data-ttu-id="41595-393">ViReplaceLine</span><span class="sxs-lookup"><span data-stu-id="41595-393">ViReplaceLine</span></span>

<span data-ttu-id="41595-394">Effacez l’intégralité de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="41595-394">Erase the entire command line.</span></span>

- <span data-ttu-id="41595-395">Mode de commande VI : `<S>` , `<c,c>`</span><span class="sxs-lookup"><span data-stu-id="41595-395">Vi command mode: `<S>`, `<c,c>`</span></span>

### <a name="vireplacetobeforechar"></a><span data-ttu-id="41595-396">ViReplaceToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="41595-396">ViReplaceToBeforeChar</span></span>

<span data-ttu-id="41595-397">Remplace jusqu’au caractère donné.</span><span class="sxs-lookup"><span data-stu-id="41595-397">Replaces until given character.</span></span>

- <span data-ttu-id="41595-398">Mode de commande VI : `<c,t>`</span><span class="sxs-lookup"><span data-stu-id="41595-398">Vi command mode: `<c,t>`</span></span>

### <a name="vireplacetobeforecharbackward"></a><span data-ttu-id="41595-399">ViReplaceToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="41595-399">ViReplaceToBeforeCharBackward</span></span>

<span data-ttu-id="41595-400">Remplace jusqu’au caractère donné.</span><span class="sxs-lookup"><span data-stu-id="41595-400">Replaces until given character.</span></span>

- <span data-ttu-id="41595-401">Mode de commande VI : `<c,T>`</span><span class="sxs-lookup"><span data-stu-id="41595-401">Vi command mode: `<c,T>`</span></span>

### <a name="vireplacetochar"></a><span data-ttu-id="41595-402">ViReplaceToChar</span><span class="sxs-lookup"><span data-stu-id="41595-402">ViReplaceToChar</span></span>

<span data-ttu-id="41595-403">Supprime jusqu’au caractère donné.</span><span class="sxs-lookup"><span data-stu-id="41595-403">Deletes until given character.</span></span>

- <span data-ttu-id="41595-404">Mode de commande VI : `<c,f>`</span><span class="sxs-lookup"><span data-stu-id="41595-404">Vi command mode: `<c,f>`</span></span>

### <a name="vireplacetocharbackward"></a><span data-ttu-id="41595-405">ViReplaceToCharBackward</span><span class="sxs-lookup"><span data-stu-id="41595-405">ViReplaceToCharBackward</span></span>

<span data-ttu-id="41595-406">Remplace jusqu’au caractère donné.</span><span class="sxs-lookup"><span data-stu-id="41595-406">Replaces until given character.</span></span>

- <span data-ttu-id="41595-407">Mode de commande VI : `<c,F>`</span><span class="sxs-lookup"><span data-stu-id="41595-407">Vi command mode: `<c,F>`</span></span>

### <a name="viyankbeginningofline"></a><span data-ttu-id="41595-408">ViYankBeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="41595-408">ViYankBeginningOfLine</span></span>

<span data-ttu-id="41595-409">Yank entre le début de la mémoire tampon et le curseur.</span><span class="sxs-lookup"><span data-stu-id="41595-409">Yank from the beginning of the buffer to the cursor.</span></span>

- <span data-ttu-id="41595-410">Mode de commande VI : `<y,0>`</span><span class="sxs-lookup"><span data-stu-id="41595-410">Vi command mode: `<y,0>`</span></span>

### <a name="viyankendofglob"></a><span data-ttu-id="41595-411">ViYankEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="41595-411">ViYankEndOfGlob</span></span>

<span data-ttu-id="41595-412">Yank du curseur jusqu’à la fin du ou des mots.</span><span class="sxs-lookup"><span data-stu-id="41595-412">Yank from the cursor to the end of the WORD(s).</span></span>

- <span data-ttu-id="41595-413">Mode de commande VI : `<y,E>`</span><span class="sxs-lookup"><span data-stu-id="41595-413">Vi command mode: `<y,E>`</span></span>

### <a name="viyankendofword"></a><span data-ttu-id="41595-414">ViYankEndOfWord</span><span class="sxs-lookup"><span data-stu-id="41595-414">ViYankEndOfWord</span></span>

<span data-ttu-id="41595-415">Yank du curseur jusqu’à la fin du ou des mots.</span><span class="sxs-lookup"><span data-stu-id="41595-415">Yank from the cursor to the end of the word(s).</span></span>

- <span data-ttu-id="41595-416">Mode de commande VI : `<y,e>`</span><span class="sxs-lookup"><span data-stu-id="41595-416">Vi command mode: `<y,e>`</span></span>

### <a name="viyankleft"></a><span data-ttu-id="41595-417">ViYankLeft</span><span class="sxs-lookup"><span data-stu-id="41595-417">ViYankLeft</span></span>

<span data-ttu-id="41595-418">Yank caractère (s) à gauche du curseur.</span><span class="sxs-lookup"><span data-stu-id="41595-418">Yank character(s) to the left of the cursor.</span></span>

- <span data-ttu-id="41595-419">Mode de commande VI : `<y,h>`</span><span class="sxs-lookup"><span data-stu-id="41595-419">Vi command mode: `<y,h>`</span></span>

### <a name="viyankline"></a><span data-ttu-id="41595-420">ViYankLine</span><span class="sxs-lookup"><span data-stu-id="41595-420">ViYankLine</span></span>

<span data-ttu-id="41595-421">Yank la mémoire tampon entière.</span><span class="sxs-lookup"><span data-stu-id="41595-421">Yank the entire buffer.</span></span>

- <span data-ttu-id="41595-422">Mode de commande VI : `<y,y>`</span><span class="sxs-lookup"><span data-stu-id="41595-422">Vi command mode: `<y,y>`</span></span>

### <a name="viyanknextglob"></a><span data-ttu-id="41595-423">ViYankNextGlob</span><span class="sxs-lookup"><span data-stu-id="41595-423">ViYankNextGlob</span></span>

<span data-ttu-id="41595-424">Yank à partir d’un curseur jusqu’au début du ou des mots suivants.</span><span class="sxs-lookup"><span data-stu-id="41595-424">Yank from cursor to the start of the next WORD(s).</span></span>

- <span data-ttu-id="41595-425">Mode de commande VI : `<y,W>`</span><span class="sxs-lookup"><span data-stu-id="41595-425">Vi command mode: `<y,W>`</span></span>

### <a name="viyanknextword"></a><span data-ttu-id="41595-426">ViYankNextWord</span><span class="sxs-lookup"><span data-stu-id="41595-426">ViYankNextWord</span></span>

<span data-ttu-id="41595-427">Yank le ou les mots après le curseur.</span><span class="sxs-lookup"><span data-stu-id="41595-427">Yank the word(s) after the cursor.</span></span>

- <span data-ttu-id="41595-428">Mode de commande VI : `<y,w>`</span><span class="sxs-lookup"><span data-stu-id="41595-428">Vi command mode: `<y,w>`</span></span>

### <a name="viyankpercent"></a><span data-ttu-id="41595-429">ViYankPercent</span><span class="sxs-lookup"><span data-stu-id="41595-429">ViYankPercent</span></span>

<span data-ttu-id="41595-430">Yank à/à partir de l’accolade correspondante.</span><span class="sxs-lookup"><span data-stu-id="41595-430">Yank to/from matching brace.</span></span>

- <span data-ttu-id="41595-431">Mode de commande VI : `<y,%>`</span><span class="sxs-lookup"><span data-stu-id="41595-431">Vi command mode: `<y,%>`</span></span>

### <a name="viyankpreviousglob"></a><span data-ttu-id="41595-432">ViYankPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="41595-432">ViYankPreviousGlob</span></span>

<span data-ttu-id="41595-433">Yank entre le début du ou des mots et le curseur.</span><span class="sxs-lookup"><span data-stu-id="41595-433">Yank from beginning of the WORD(s) to cursor.</span></span>

- <span data-ttu-id="41595-434">Mode de commande VI : `<y,B>`</span><span class="sxs-lookup"><span data-stu-id="41595-434">Vi command mode: `<y,B>`</span></span>

### <a name="viyankpreviousword"></a><span data-ttu-id="41595-435">ViYankPreviousWord</span><span class="sxs-lookup"><span data-stu-id="41595-435">ViYankPreviousWord</span></span>

<span data-ttu-id="41595-436">Yank le ou les mots avant le curseur.</span><span class="sxs-lookup"><span data-stu-id="41595-436">Yank the word(s) before the cursor.</span></span>

- <span data-ttu-id="41595-437">Mode de commande VI : `<y,b>`</span><span class="sxs-lookup"><span data-stu-id="41595-437">Vi command mode: `<y,b>`</span></span>

### <a name="viyankright"></a><span data-ttu-id="41595-438">ViYankRight</span><span class="sxs-lookup"><span data-stu-id="41595-438">ViYankRight</span></span>

<span data-ttu-id="41595-439">Yank caractère (s) situé sous et à droite du curseur.</span><span class="sxs-lookup"><span data-stu-id="41595-439">Yank character(s) under and to the right of the cursor.</span></span>

- <span data-ttu-id="41595-440">Mode de commande VI : `<y,l>` , `<y,Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="41595-440">Vi command mode: `<y,l>`, `<y,Spacebar>`</span></span>

### <a name="viyanktoendofline"></a><span data-ttu-id="41595-441">ViYankToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="41595-441">ViYankToEndOfLine</span></span>

<span data-ttu-id="41595-442">Yank du curseur jusqu’à la fin de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="41595-442">Yank from the cursor to the end of the buffer.</span></span>

- <span data-ttu-id="41595-443">Mode de commande VI : `<y,$>`</span><span class="sxs-lookup"><span data-stu-id="41595-443">Vi command mode: `<y,$>`</span></span>

### <a name="viyanktofirstchar"></a><span data-ttu-id="41595-444">ViYankToFirstChar</span><span class="sxs-lookup"><span data-stu-id="41595-444">ViYankToFirstChar</span></span>

<span data-ttu-id="41595-445">Yank du premier caractère autre qu’un espace blanc au curseur.</span><span class="sxs-lookup"><span data-stu-id="41595-445">Yank from the first non-whitespace character to the cursor.</span></span>

- <span data-ttu-id="41595-446">Mode de commande VI : `<y,^>`</span><span class="sxs-lookup"><span data-stu-id="41595-446">Vi command mode: `<y,^>`</span></span>

### <a name="yank"></a><span data-ttu-id="41595-447">Yank</span><span class="sxs-lookup"><span data-stu-id="41595-447">Yank</span></span>

<span data-ttu-id="41595-448">Ajoutez le texte le plus récemment supprimé à l’entrée.</span><span class="sxs-lookup"><span data-stu-id="41595-448">Add the most recently killed text to the input.</span></span>

- <span data-ttu-id="41595-449">Emacs- `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="41595-449">Emacs: `<Ctrl+y>`</span></span>

### <a name="yanklastarg"></a><span data-ttu-id="41595-450">YankLastArg</span><span class="sxs-lookup"><span data-stu-id="41595-450">YankLastArg</span></span>

<span data-ttu-id="41595-451">Yank le dernier argument de la ligne d’historique précédente.</span><span class="sxs-lookup"><span data-stu-id="41595-451">Yank the last argument from the previous history line.</span></span> <span data-ttu-id="41595-452">Avec un argument, la première fois qu’il est appelé, se comporte comme YankNthArg.</span><span class="sxs-lookup"><span data-stu-id="41595-452">With an argument, the first time it is invoked, behaves just like YankNthArg.</span></span> <span data-ttu-id="41595-453">Si elle est appelée plusieurs fois, elle itère au sein de l’historique et ARG définit la direction (négatif inverse la direction).</span><span class="sxs-lookup"><span data-stu-id="41595-453">If invoked multiple times, instead it iterates through history and arg sets the direction (negative reverses the direction.)</span></span>

- <span data-ttu-id="41595-454">Cmd `<Alt+.>`</span><span class="sxs-lookup"><span data-stu-id="41595-454">Cmd: `<Alt+.>`</span></span>
- <span data-ttu-id="41595-455">Emacs : `<Alt+.>` , `<Alt+_>` , `<Escape,.>` , `<Escape,_>`</span><span class="sxs-lookup"><span data-stu-id="41595-455">Emacs: `<Alt+.>`, `<Alt+_>`, `<Escape,.>`, `<Escape,_>`</span></span>

### <a name="yankntharg"></a><span data-ttu-id="41595-456">YankNthArg</span><span class="sxs-lookup"><span data-stu-id="41595-456">YankNthArg</span></span>

<span data-ttu-id="41595-457">Yank le premier argument (après la commande) à partir de la ligne précédente de l’historique.</span><span class="sxs-lookup"><span data-stu-id="41595-457">Yank the first argument (after the command) from the previous history line.</span></span>
<span data-ttu-id="41595-458">Avec un argument, Yank le nième argument (à partir de 0), si l’argument est négatif, commencez par le dernier argument.</span><span class="sxs-lookup"><span data-stu-id="41595-458">With an argument, yank the nth argument (starting from 0), if the argument is negative, start from the last argument.</span></span>

- <span data-ttu-id="41595-459">Emacs- `<Ctrl+Alt+y>` , `<Escape,Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="41595-459">Emacs: `<Ctrl+Alt+y>`, `<Escape,Ctrl+y>`</span></span>

### <a name="yankpop"></a><span data-ttu-id="41595-460">YankPop</span><span class="sxs-lookup"><span data-stu-id="41595-460">YankPop</span></span>

<span data-ttu-id="41595-461">Si l’opération précédente était Yank ou YankPop, remplacez le texte précédemment extrait par le texte supprimé suivant de l’instruction KILL-Ring.</span><span class="sxs-lookup"><span data-stu-id="41595-461">If the previous operation was Yank or YankPop, replace the previously yanked text with the next killed text from the kill-ring.</span></span>

- <span data-ttu-id="41595-462">Emacs- `<Alt+y>` , `<Escape,y>`</span><span class="sxs-lookup"><span data-stu-id="41595-462">Emacs: `<Alt+y>`, `<Escape,y>`</span></span>

## <a name="cursor-movement-functions"></a><span data-ttu-id="41595-463">Fonctions de déplacement de curseur</span><span class="sxs-lookup"><span data-stu-id="41595-463">Cursor movement functions</span></span>

### <a name="backwardchar"></a><span data-ttu-id="41595-464">BackwardChar</span><span class="sxs-lookup"><span data-stu-id="41595-464">BackwardChar</span></span>

<span data-ttu-id="41595-465">Déplacer le curseur d’un caractère vers la gauche.</span><span class="sxs-lookup"><span data-stu-id="41595-465">Move the cursor one character to the left.</span></span> <span data-ttu-id="41595-466">Cela peut déplacer le curseur vers la ligne précédente de l’entrée multiligne.</span><span class="sxs-lookup"><span data-stu-id="41595-466">This may move the cursor to the previous line of multi-line input.</span></span>

- <span data-ttu-id="41595-467">Cmd `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="41595-467">Cmd: `<LeftArrow>`</span></span>
- <span data-ttu-id="41595-468">Emacs- `<LeftArrow>` , `<Ctrl+b>`</span><span class="sxs-lookup"><span data-stu-id="41595-468">Emacs: `<LeftArrow>`, `<Ctrl+b>`</span></span>

### <a name="backwardword"></a><span data-ttu-id="41595-469">BackwardWord</span><span class="sxs-lookup"><span data-stu-id="41595-469">BackwardWord</span></span>

<span data-ttu-id="41595-470">Ramener le curseur au début du mot actuel, ou si entre les mots, le début du mot précédent.</span><span class="sxs-lookup"><span data-stu-id="41595-470">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="41595-471">Les limites de mots sont définies par un jeu de caractères configurable.</span><span class="sxs-lookup"><span data-stu-id="41595-471">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="41595-472">Cmd `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="41595-472">Cmd: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="41595-473">Emacs- `<Alt+b>` , `<Escape,b>`</span><span class="sxs-lookup"><span data-stu-id="41595-473">Emacs: `<Alt+b>`, `<Escape,b>`</span></span>
- <span data-ttu-id="41595-474">Mode d’insertion VI : `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="41595-474">Vi insert mode: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="41595-475">Mode de commande VI : `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="41595-475">Vi command mode: `<Ctrl+LeftArrow>`</span></span>

### <a name="beginningofline"></a><span data-ttu-id="41595-476">BeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="41595-476">BeginningOfLine</span></span>

<span data-ttu-id="41595-477">Si l’entrée comporte plusieurs lignes, se déplacer au début de la ligne active ou, le cas échéant, au début de la ligne, se déplacer au début de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="41595-477">If the input has multiple lines, move to the start of the current line, or if already at the start of the line, move to the start of the input.</span></span> <span data-ttu-id="41595-478">Si l’entrée comporte une seule ligne, accédez au début de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="41595-478">If the input has a single line, move to the start of the input.</span></span>

- <span data-ttu-id="41595-479">Cmd `<Home>`</span><span class="sxs-lookup"><span data-stu-id="41595-479">Cmd: `<Home>`</span></span>
- <span data-ttu-id="41595-480">Emacs- `<Home>` , `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="41595-480">Emacs: `<Home>`, `<Ctrl+a>`</span></span>
- <span data-ttu-id="41595-481">Mode d’insertion VI : `<Home>`</span><span class="sxs-lookup"><span data-stu-id="41595-481">Vi insert mode: `<Home>`</span></span>
- <span data-ttu-id="41595-482">Mode de commande VI : `<Home>`</span><span class="sxs-lookup"><span data-stu-id="41595-482">Vi command mode: `<Home>`</span></span>

### <a name="endofline"></a><span data-ttu-id="41595-483">EndOfLine</span><span class="sxs-lookup"><span data-stu-id="41595-483">EndOfLine</span></span>

<span data-ttu-id="41595-484">Si l’entrée comporte plusieurs lignes, passez à la fin de la ligne active ou, si elle se trouve déjà à la fin de la ligne, à la fin de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="41595-484">If the input has multiple lines, move to the end of the current line, or if already at the end of the line, move to the end of the input.</span></span> <span data-ttu-id="41595-485">Si l’entrée comporte une seule ligne, passez à la fin de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="41595-485">If the input has a single line, move to the end of the input.</span></span>

- <span data-ttu-id="41595-486">Cmd `<End>`</span><span class="sxs-lookup"><span data-stu-id="41595-486">Cmd: `<End>`</span></span>
- <span data-ttu-id="41595-487">Emacs- `<End>` , `<Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="41595-487">Emacs: `<End>`, `<Ctrl+e>`</span></span>
- <span data-ttu-id="41595-488">Mode d’insertion VI : `<End>`</span><span class="sxs-lookup"><span data-stu-id="41595-488">Vi insert mode: `<End>`</span></span>

### <a name="forwardchar"></a><span data-ttu-id="41595-489">ForwardChar</span><span class="sxs-lookup"><span data-stu-id="41595-489">ForwardChar</span></span>

<span data-ttu-id="41595-490">Déplacer le curseur d’un caractère vers la droite.</span><span class="sxs-lookup"><span data-stu-id="41595-490">Move the cursor one character to the right.</span></span> <span data-ttu-id="41595-491">Cela peut déplacer le curseur à la ligne suivante de l’entrée multiligne.</span><span class="sxs-lookup"><span data-stu-id="41595-491">This may move the cursor to the next line of multi-line input.</span></span>

- <span data-ttu-id="41595-492">Cmd `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="41595-492">Cmd: `<RightArrow>`</span></span>
- <span data-ttu-id="41595-493">Emacs- `<RightArrow>` , `<Ctrl+f>`</span><span class="sxs-lookup"><span data-stu-id="41595-493">Emacs: `<RightArrow>`, `<Ctrl+f>`</span></span>

### <a name="forwardword"></a><span data-ttu-id="41595-494">ForwardWord</span><span class="sxs-lookup"><span data-stu-id="41595-494">ForwardWord</span></span>

<span data-ttu-id="41595-495">Déplacer le curseur vers l’avant jusqu’à la fin du mot actuel, ou si entre les mots, à la fin du mot suivant.</span><span class="sxs-lookup"><span data-stu-id="41595-495">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="41595-496">Les limites de mots sont définies par un jeu de caractères configurable.</span><span class="sxs-lookup"><span data-stu-id="41595-496">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="41595-497">Emacs- `<Alt+f>` , `<Escape,f>`</span><span class="sxs-lookup"><span data-stu-id="41595-497">Emacs: `<Alt+f>`, `<Escape,f>`</span></span>

### <a name="gotobrace"></a><span data-ttu-id="41595-498">GotoBrace</span><span class="sxs-lookup"><span data-stu-id="41595-498">GotoBrace</span></span>

<span data-ttu-id="41595-499">Atteindre l’accolade correspondante, les parenthèses ou les crochets.</span><span class="sxs-lookup"><span data-stu-id="41595-499">Go to the matching brace, parenthesis, or square bracket.</span></span>

- <span data-ttu-id="41595-500">Cmd `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="41595-500">Cmd: `<Ctrl+]>`</span></span>
- <span data-ttu-id="41595-501">Mode d’insertion VI : `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="41595-501">Vi insert mode: `<Ctrl+]>`</span></span>
- <span data-ttu-id="41595-502">Mode de commande VI : `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="41595-502">Vi command mode: `<Ctrl+]>`</span></span>

### <a name="gotocolumn"></a><span data-ttu-id="41595-503">GotoColumn</span><span class="sxs-lookup"><span data-stu-id="41595-503">GotoColumn</span></span>

<span data-ttu-id="41595-504">Accédez à la colonne indiquée par arg.</span><span class="sxs-lookup"><span data-stu-id="41595-504">Move to the column indicated by arg.</span></span>

- <span data-ttu-id="41595-505">Mode de commande VI : `<|>`</span><span class="sxs-lookup"><span data-stu-id="41595-505">Vi command mode: `<|>`</span></span>

### <a name="gotofirstnonblankofline"></a><span data-ttu-id="41595-506">GotoFirstNonBlankOfLine</span><span class="sxs-lookup"><span data-stu-id="41595-506">GotoFirstNonBlankOfLine</span></span>

<span data-ttu-id="41595-507">Placez le curseur sur le premier caractère non vide de la ligne.</span><span class="sxs-lookup"><span data-stu-id="41595-507">Move the cursor to the first non-blank character in the line.</span></span>

- <span data-ttu-id="41595-508">Mode de commande VI : `<^>` , `<_>`</span><span class="sxs-lookup"><span data-stu-id="41595-508">Vi command mode: `<^>`, `<_>`</span></span>

### <a name="movetoendofline"></a><span data-ttu-id="41595-509">MoveToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="41595-509">MoveToEndOfLine</span></span>

<span data-ttu-id="41595-510">Placez le curseur à la fin de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="41595-510">Move the cursor to the end of the input.</span></span>

- <span data-ttu-id="41595-511">Mode de commande VI : `<End>` , `<$>`</span><span class="sxs-lookup"><span data-stu-id="41595-511">Vi command mode: `<End>`, `<$>`</span></span>

### <a name="nextline"></a><span data-ttu-id="41595-512">NextLine</span><span class="sxs-lookup"><span data-stu-id="41595-512">NextLine</span></span>

<span data-ttu-id="41595-513">Déplacer le curseur sur la ligne suivante.</span><span class="sxs-lookup"><span data-stu-id="41595-513">Move the cursor to the next line.</span></span>

- <span data-ttu-id="41595-514">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="41595-514">Function is unbound.</span></span>

### <a name="nextword"></a><span data-ttu-id="41595-515">NextWord</span><span class="sxs-lookup"><span data-stu-id="41595-515">NextWord</span></span>

<span data-ttu-id="41595-516">Déplacer le curseur vers l’avant jusqu’au début du mot suivant.</span><span class="sxs-lookup"><span data-stu-id="41595-516">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="41595-517">Les limites de mots sont définies par un jeu de caractères configurable.</span><span class="sxs-lookup"><span data-stu-id="41595-517">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="41595-518">Cmd `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="41595-518">Cmd: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="41595-519">Mode d’insertion VI : `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="41595-519">Vi insert mode: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="41595-520">Mode de commande VI : `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="41595-520">Vi command mode: `<Ctrl+RightArrow>`</span></span>

### <a name="nextwordend"></a><span data-ttu-id="41595-521">NextWordEnd</span><span class="sxs-lookup"><span data-stu-id="41595-521">NextWordEnd</span></span>

<span data-ttu-id="41595-522">Déplacer le curseur vers l’avant jusqu’à la fin du mot actuel, ou si entre les mots, à la fin du mot suivant.</span><span class="sxs-lookup"><span data-stu-id="41595-522">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="41595-523">Les limites de mots sont définies par un jeu de caractères configurable.</span><span class="sxs-lookup"><span data-stu-id="41595-523">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="41595-524">Mode de commande VI : `<e>`</span><span class="sxs-lookup"><span data-stu-id="41595-524">Vi command mode: `<e>`</span></span>

### <a name="previousline"></a><span data-ttu-id="41595-525">PreviousLine</span><span class="sxs-lookup"><span data-stu-id="41595-525">PreviousLine</span></span>

<span data-ttu-id="41595-526">Placez le curseur sur la ligne précédente.</span><span class="sxs-lookup"><span data-stu-id="41595-526">Move the cursor to the previous line.</span></span>

- <span data-ttu-id="41595-527">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="41595-527">Function is unbound.</span></span>

### <a name="shellbackwardword"></a><span data-ttu-id="41595-528">ShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="41595-528">ShellBackwardWord</span></span>

<span data-ttu-id="41595-529">Ramener le curseur au début du mot actuel, ou si entre les mots, le début du mot précédent.</span><span class="sxs-lookup"><span data-stu-id="41595-529">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="41595-530">Les limites de mots sont définies par les jetons PowerShell.</span><span class="sxs-lookup"><span data-stu-id="41595-530">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="41595-531">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="41595-531">Function is unbound.</span></span>

### <a name="shellforwardword"></a><span data-ttu-id="41595-532">ShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="41595-532">ShellForwardWord</span></span>

<span data-ttu-id="41595-533">Déplacer le curseur vers l’avant jusqu’au début du mot suivant.</span><span class="sxs-lookup"><span data-stu-id="41595-533">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="41595-534">Les limites de mots sont définies par les jetons PowerShell.</span><span class="sxs-lookup"><span data-stu-id="41595-534">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="41595-535">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="41595-535">Function is unbound.</span></span>

### <a name="shellnextword"></a><span data-ttu-id="41595-536">ShellNextWord</span><span class="sxs-lookup"><span data-stu-id="41595-536">ShellNextWord</span></span>

<span data-ttu-id="41595-537">Déplacer le curseur vers l’avant jusqu’à la fin du mot actuel, ou si entre les mots, à la fin du mot suivant.</span><span class="sxs-lookup"><span data-stu-id="41595-537">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="41595-538">Les limites de mots sont définies par les jetons PowerShell.</span><span class="sxs-lookup"><span data-stu-id="41595-538">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="41595-539">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="41595-539">Function is unbound.</span></span>

### <a name="vibackwardchar"></a><span data-ttu-id="41595-540">ViBackwardChar</span><span class="sxs-lookup"><span data-stu-id="41595-540">ViBackwardChar</span></span>

<span data-ttu-id="41595-541">Déplacer le curseur d’un caractère vers la gauche en mode d’édition VI.</span><span class="sxs-lookup"><span data-stu-id="41595-541">Move the cursor one character to the left in the Vi edit mode.</span></span> <span data-ttu-id="41595-542">Cela peut déplacer le curseur vers la ligne précédente de l’entrée multiligne.</span><span class="sxs-lookup"><span data-stu-id="41595-542">This may move the cursor to the previous line of multi-line input.</span></span>

- <span data-ttu-id="41595-543">Mode d’insertion VI : `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="41595-543">Vi insert mode: `<LeftArrow>`</span></span>
- <span data-ttu-id="41595-544">Mode de commande VI : `<LeftArrow>` , `<Backspace>` , `<h>`</span><span class="sxs-lookup"><span data-stu-id="41595-544">Vi command mode: `<LeftArrow>`, `<Backspace>`, `<h>`</span></span>

### <a name="vibackwardword"></a><span data-ttu-id="41595-545">ViBackwardWord</span><span class="sxs-lookup"><span data-stu-id="41595-545">ViBackwardWord</span></span>

<span data-ttu-id="41595-546">Ramener le curseur au début du mot actuel, ou si entre les mots, le début du mot précédent.</span><span class="sxs-lookup"><span data-stu-id="41595-546">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="41595-547">Les limites de mots sont définies par un jeu de caractères configurable.</span><span class="sxs-lookup"><span data-stu-id="41595-547">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="41595-548">Mode de commande VI : `<b>`</span><span class="sxs-lookup"><span data-stu-id="41595-548">Vi command mode: `<b>`</span></span>

### <a name="viforwardchar"></a><span data-ttu-id="41595-549">ViForwardChar</span><span class="sxs-lookup"><span data-stu-id="41595-549">ViForwardChar</span></span>

<span data-ttu-id="41595-550">Déplacer le curseur d’un caractère vers la droite en mode d’édition VI.</span><span class="sxs-lookup"><span data-stu-id="41595-550">Move the cursor one character to the right in the Vi edit mode.</span></span> <span data-ttu-id="41595-551">Cela peut déplacer le curseur à la ligne suivante de l’entrée multiligne.</span><span class="sxs-lookup"><span data-stu-id="41595-551">This may move the cursor to the next line of multi-line input.</span></span>

- <span data-ttu-id="41595-552">Mode d’insertion VI : `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="41595-552">Vi insert mode: `<RightArrow>`</span></span>
- <span data-ttu-id="41595-553">Mode de commande VI : `<RightArrow>` , `<Spacebar>` , `<l>`</span><span class="sxs-lookup"><span data-stu-id="41595-553">Vi command mode: `<RightArrow>`, `<Spacebar>`, `<l>`</span></span>

### <a name="viendofglob"></a><span data-ttu-id="41595-554">ViEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="41595-554">ViEndOfGlob</span></span>

<span data-ttu-id="41595-555">Déplace le curseur à la fin du mot, en utilisant uniquement des espaces blancs comme délimiteurs.</span><span class="sxs-lookup"><span data-stu-id="41595-555">Moves the cursor to the end of the word, using only white space as delimiters.</span></span>

- <span data-ttu-id="41595-556">Mode de commande VI : `<E>`</span><span class="sxs-lookup"><span data-stu-id="41595-556">Vi command mode: `<E>`</span></span>

### <a name="viendofpreviousglob"></a><span data-ttu-id="41595-557">ViEndOfPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="41595-557">ViEndOfPreviousGlob</span></span>

<span data-ttu-id="41595-558">Passe à la fin du mot précédent, en utilisant uniquement un espace blanc comme délimiteur de mot.</span><span class="sxs-lookup"><span data-stu-id="41595-558">Moves to the end of the previous word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="41595-559">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="41595-559">Function is unbound.</span></span>

### <a name="vigotobrace"></a><span data-ttu-id="41595-560">ViGotoBrace</span><span class="sxs-lookup"><span data-stu-id="41595-560">ViGotoBrace</span></span>

<span data-ttu-id="41595-561">Semblable à GotoBrace, mais est basé sur un caractère et non sur un jeton.</span><span class="sxs-lookup"><span data-stu-id="41595-561">Similar to GotoBrace, but is character based instead of token based.</span></span>

- <span data-ttu-id="41595-562">Mode de commande VI : `<%>`</span><span class="sxs-lookup"><span data-stu-id="41595-562">Vi command mode: `<%>`</span></span>

### <a name="vinextglob"></a><span data-ttu-id="41595-563">ViNextGlob</span><span class="sxs-lookup"><span data-stu-id="41595-563">ViNextGlob</span></span>

<span data-ttu-id="41595-564">Passe au mot suivant, en utilisant uniquement un espace blanc comme délimiteur de mot.</span><span class="sxs-lookup"><span data-stu-id="41595-564">Moves to the next word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="41595-565">Mode de commande VI : `<W>`</span><span class="sxs-lookup"><span data-stu-id="41595-565">Vi command mode: `<W>`</span></span>

### <a name="vinextword"></a><span data-ttu-id="41595-566">ViNextWord</span><span class="sxs-lookup"><span data-stu-id="41595-566">ViNextWord</span></span>

<span data-ttu-id="41595-567">Déplacer le curseur vers l’avant jusqu’au début du mot suivant.</span><span class="sxs-lookup"><span data-stu-id="41595-567">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="41595-568">Les limites de mots sont définies par un jeu de caractères configurable.</span><span class="sxs-lookup"><span data-stu-id="41595-568">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="41595-569">Mode de commande VI : `<w>`</span><span class="sxs-lookup"><span data-stu-id="41595-569">Vi command mode: `<w>`</span></span>

## <a name="history-functions"></a><span data-ttu-id="41595-570">Fonctions d’historique</span><span class="sxs-lookup"><span data-stu-id="41595-570">History functions</span></span>

### <a name="beginningofhistory"></a><span data-ttu-id="41595-571">BeginningOfHistory</span><span class="sxs-lookup"><span data-stu-id="41595-571">BeginningOfHistory</span></span>

<span data-ttu-id="41595-572">Accéder au premier élément de l’historique.</span><span class="sxs-lookup"><span data-stu-id="41595-572">Move to the first item in the history.</span></span>

- <span data-ttu-id="41595-573">Emacs- `<Alt+<>`</span><span class="sxs-lookup"><span data-stu-id="41595-573">Emacs: `<Alt+<>`</span></span>

### <a name="clearhistory"></a><span data-ttu-id="41595-574">ClearHistory</span><span class="sxs-lookup"><span data-stu-id="41595-574">ClearHistory</span></span>

<span data-ttu-id="41595-575">Efface l’historique dans PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="41595-575">Clears history in PSReadLine.</span></span> <span data-ttu-id="41595-576">Cela n’affecte pas l’historique PowerShell.</span><span class="sxs-lookup"><span data-stu-id="41595-576">This does not affect PowerShell history.</span></span>

- <span data-ttu-id="41595-577">Cmd `<Alt+F7>`</span><span class="sxs-lookup"><span data-stu-id="41595-577">Cmd: `<Alt+F7>`</span></span>

### <a name="endofhistory"></a><span data-ttu-id="41595-578">EndOfHistory</span><span class="sxs-lookup"><span data-stu-id="41595-578">EndOfHistory</span></span>

<span data-ttu-id="41595-579">Accéder au dernier élément (l’entrée en cours) dans l’historique.</span><span class="sxs-lookup"><span data-stu-id="41595-579">Move to the last item (the current input) in the history.</span></span>

- <span data-ttu-id="41595-580">Emacs- `<Alt+>>`</span><span class="sxs-lookup"><span data-stu-id="41595-580">Emacs: `<Alt+>>`</span></span>

### <a name="forwardsearchhistory"></a><span data-ttu-id="41595-581">ForwardSearchHistory</span><span class="sxs-lookup"><span data-stu-id="41595-581">ForwardSearchHistory</span></span>

<span data-ttu-id="41595-582">Effectuer une recherche incrémentielle par progression dans l’historique.</span><span class="sxs-lookup"><span data-stu-id="41595-582">Perform an incremental forward search through history.</span></span>

- <span data-ttu-id="41595-583">Cmd `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="41595-583">Cmd: `<Ctrl+s>`</span></span>
- <span data-ttu-id="41595-584">Emacs- `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="41595-584">Emacs: `<Ctrl+s>`</span></span>

### <a name="historysearchbackward"></a><span data-ttu-id="41595-585">HistorySearchBackward</span><span class="sxs-lookup"><span data-stu-id="41595-585">HistorySearchBackward</span></span>

<span data-ttu-id="41595-586">Remplacez l’entrée actuelle par l’élément « Previous » de l’historique PSReadLine qui correspond aux caractères entre le début et l’entrée et le curseur.</span><span class="sxs-lookup"><span data-stu-id="41595-586">Replace the current input with the 'previous' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="41595-587">Cmd `<F8>`</span><span class="sxs-lookup"><span data-stu-id="41595-587">Cmd: `<F8>`</span></span>

### <a name="historysearchforward"></a><span data-ttu-id="41595-588">HistorySearchForward</span><span class="sxs-lookup"><span data-stu-id="41595-588">HistorySearchForward</span></span>

<span data-ttu-id="41595-589">Remplacez l’entrée actuelle par l’élément « Next » de l’historique PSReadLine qui correspond aux caractères entre le début et l’entrée et le curseur.</span><span class="sxs-lookup"><span data-stu-id="41595-589">Replace the current input with the 'next' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="41595-590">Cmd `<Shift+F8>`</span><span class="sxs-lookup"><span data-stu-id="41595-590">Cmd: `<Shift+F8>`</span></span>

### <a name="nexthistory"></a><span data-ttu-id="41595-591">NextHistory</span><span class="sxs-lookup"><span data-stu-id="41595-591">NextHistory</span></span>

<span data-ttu-id="41595-592">Remplacez l’entrée actuelle par l’élément « Next » de l’historique PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="41595-592">Replace the current input with the 'next' item from PSReadLine history.</span></span>

- <span data-ttu-id="41595-593">Cmd `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="41595-593">Cmd: `<DownArrow>`</span></span>
- <span data-ttu-id="41595-594">Emacs- `<DownArrow>` , `<Ctrl+n>`</span><span class="sxs-lookup"><span data-stu-id="41595-594">Emacs: `<DownArrow>`, `<Ctrl+n>`</span></span>
- <span data-ttu-id="41595-595">Mode d’insertion VI : `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="41595-595">Vi insert mode: `<DownArrow>`</span></span>
- <span data-ttu-id="41595-596">Mode de commande VI : `<DownArrow>` , `<j>` , `<+>`</span><span class="sxs-lookup"><span data-stu-id="41595-596">Vi command mode: `<DownArrow>`, `<j>`, `<+>`</span></span>

### <a name="previoushistory"></a><span data-ttu-id="41595-597">PreviousHistory</span><span class="sxs-lookup"><span data-stu-id="41595-597">PreviousHistory</span></span>

<span data-ttu-id="41595-598">Remplacez l’entrée actuelle par l’élément « Previous » de l’historique PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="41595-598">Replace the current input with the 'previous' item from PSReadLine history.</span></span>

- <span data-ttu-id="41595-599">Cmd `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="41595-599">Cmd: `<UpArrow>`</span></span>
- <span data-ttu-id="41595-600">Emacs- `<UpArrow>` , `<Ctrl+p>`</span><span class="sxs-lookup"><span data-stu-id="41595-600">Emacs: `<UpArrow>`, `<Ctrl+p>`</span></span>
- <span data-ttu-id="41595-601">Mode d’insertion VI : `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="41595-601">Vi insert mode: `<UpArrow>`</span></span>
- <span data-ttu-id="41595-602">Mode de commande VI : `<UpArrow>` , `<k>` , `<->`</span><span class="sxs-lookup"><span data-stu-id="41595-602">Vi command mode: `<UpArrow>`, `<k>`, `<->`</span></span>

### <a name="reversesearchhistory"></a><span data-ttu-id="41595-603">ReverseSearchHistory</span><span class="sxs-lookup"><span data-stu-id="41595-603">ReverseSearchHistory</span></span>

<span data-ttu-id="41595-604">Effectuer une recherche incrémentielle incrémentielle dans l’historique.</span><span class="sxs-lookup"><span data-stu-id="41595-604">Perform an incremental backward search through history.</span></span>

- <span data-ttu-id="41595-605">Cmd `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="41595-605">Cmd: `<Ctrl+r>`</span></span>
- <span data-ttu-id="41595-606">Emacs- `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="41595-606">Emacs: `<Ctrl+r>`</span></span>

### <a name="visearchhistorybackward"></a><span data-ttu-id="41595-607">ViSearchHistoryBackward</span><span class="sxs-lookup"><span data-stu-id="41595-607">ViSearchHistoryBackward</span></span>

<span data-ttu-id="41595-608">Demande une chaîne de recherche et lance la recherche sur AcceptLine.</span><span class="sxs-lookup"><span data-stu-id="41595-608">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="41595-609">Mode d’insertion VI : `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="41595-609">Vi insert mode: `<Ctrl+r>`</span></span>
- <span data-ttu-id="41595-610">Mode de commande VI : `</>` , `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="41595-610">Vi command mode: `</>`, `<Ctrl+r>`</span></span>

## <a name="completion-functions"></a><span data-ttu-id="41595-611">Fonctions d’achèvement</span><span class="sxs-lookup"><span data-stu-id="41595-611">Completion functions</span></span>

### <a name="complete"></a><span data-ttu-id="41595-612">Terminé</span><span class="sxs-lookup"><span data-stu-id="41595-612">Complete</span></span>

<span data-ttu-id="41595-613">Tentative d’exécution de l’opération sur le texte entourant le curseur.</span><span class="sxs-lookup"><span data-stu-id="41595-613">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="41595-614">S’il existe plusieurs saisies semi-automatiques possibles, le plus long préfixe non ambigu est utilisé pour la finalisation.</span><span class="sxs-lookup"><span data-stu-id="41595-614">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="41595-615">Si vous essayez de terminer la saisie semi-automatique la plus longue, une liste des saisies semi-automatiques possibles s’affiche.</span><span class="sxs-lookup"><span data-stu-id="41595-615">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="41595-616">Emacs- `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="41595-616">Emacs: `<Tab>`</span></span>

### <a name="menucomplete"></a><span data-ttu-id="41595-617">MenuComplete</span><span class="sxs-lookup"><span data-stu-id="41595-617">MenuComplete</span></span>

<span data-ttu-id="41595-618">Tentative d’exécution de l’opération sur le texte entourant le curseur.</span><span class="sxs-lookup"><span data-stu-id="41595-618">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="41595-619">S’il existe plusieurs saisies semi-automatiques possibles, le plus long préfixe non ambigu est utilisé pour la finalisation.</span><span class="sxs-lookup"><span data-stu-id="41595-619">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="41595-620">Si vous essayez de terminer la saisie semi-automatique la plus longue, une liste des saisies semi-automatiques possibles s’affiche.</span><span class="sxs-lookup"><span data-stu-id="41595-620">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="41595-621">Cmd : `<Ctrl+@>` , `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="41595-621">Cmd: `<Ctrl+@>`, `<Ctrl+Spacebar>`</span></span>
- <span data-ttu-id="41595-622">Emacs- `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="41595-622">Emacs: `<Ctrl+Spacebar>`</span></span>

### <a name="possiblecompletions"></a><span data-ttu-id="41595-623">PossibleCompletions</span><span class="sxs-lookup"><span data-stu-id="41595-623">PossibleCompletions</span></span>

<span data-ttu-id="41595-624">Affiche la liste des saisies semi-automatiques possibles.</span><span class="sxs-lookup"><span data-stu-id="41595-624">Display the list of possible completions.</span></span>

- <span data-ttu-id="41595-625">Emacs- `<Alt+=>`</span><span class="sxs-lookup"><span data-stu-id="41595-625">Emacs: `<Alt+=>`</span></span>
- <span data-ttu-id="41595-626">Mode d’insertion VI : `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="41595-626">Vi insert mode: `<Ctrl+Spacebar>`</span></span>
- <span data-ttu-id="41595-627">Mode de commande VI : `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="41595-627">Vi command mode: `<Ctrl+Spacebar>`</span></span>

### <a name="tabcompletenext"></a><span data-ttu-id="41595-628">TabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="41595-628">TabCompleteNext</span></span>

<span data-ttu-id="41595-629">Tente de terminer le texte entourant le curseur avec la prochaine saisie semi-automatique disponible.</span><span class="sxs-lookup"><span data-stu-id="41595-629">Attempt to complete the text surrounding the cursor with the next available completion.</span></span>

- <span data-ttu-id="41595-630">Cmd `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="41595-630">Cmd: `<Tab>`</span></span>
- <span data-ttu-id="41595-631">Mode de commande VI : `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="41595-631">Vi command mode: `<Tab>`</span></span>

### <a name="tabcompleteprevious"></a><span data-ttu-id="41595-632">TabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="41595-632">TabCompletePrevious</span></span>

<span data-ttu-id="41595-633">Tente de terminer le texte entourant le curseur avec l’achèvement disponible précédent.</span><span class="sxs-lookup"><span data-stu-id="41595-633">Attempt to complete the text surrounding the cursor with the previous available completion.</span></span>

- <span data-ttu-id="41595-634">Cmd `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="41595-634">Cmd: `<Shift+Tab>`</span></span>
- <span data-ttu-id="41595-635">Mode de commande VI : `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="41595-635">Vi command mode: `<Shift+Tab>`</span></span>

### <a name="vitabcompletenext"></a><span data-ttu-id="41595-636">ViTabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="41595-636">ViTabCompleteNext</span></span>

<span data-ttu-id="41595-637">Met fin au groupe d’édition actuel, si nécessaire, et appelle TabCompleteNext.</span><span class="sxs-lookup"><span data-stu-id="41595-637">Ends the current edit group, if needed, and invokes TabCompleteNext.</span></span>

- <span data-ttu-id="41595-638">Mode d’insertion VI : `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="41595-638">Vi insert mode: `<Tab>`</span></span>

### <a name="vitabcompleteprevious"></a><span data-ttu-id="41595-639">ViTabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="41595-639">ViTabCompletePrevious</span></span>

<span data-ttu-id="41595-640">Met fin au groupe d’édition actuel, si nécessaire, et appelle TabCompletePrevious.</span><span class="sxs-lookup"><span data-stu-id="41595-640">Ends the current edit group, if needed, and invokes TabCompletePrevious.</span></span>

- <span data-ttu-id="41595-641">Mode d’insertion VI : `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="41595-641">Vi insert mode: `<Shift+Tab>`</span></span>

## <a name="miscellaneous-functions"></a><span data-ttu-id="41595-642">Fonctions diverses</span><span class="sxs-lookup"><span data-stu-id="41595-642">Miscellaneous functions</span></span>

### <a name="acceptnextsuggestionword"></a><span data-ttu-id="41595-643">AcceptNextSuggestionWord</span><span class="sxs-lookup"><span data-stu-id="41595-643">AcceptNextSuggestionWord</span></span>

<span data-ttu-id="41595-644">Accepter le mot suivant de la suggestion inline ou sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="41595-644">Accept the next word of the inline or selected suggestion.</span></span>

- <span data-ttu-id="41595-645">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="41595-645">Function is unbound.</span></span>

### <a name="acceptsuggestion"></a><span data-ttu-id="41595-646">AcceptSuggestion</span><span class="sxs-lookup"><span data-stu-id="41595-646">AcceptSuggestion</span></span>

<span data-ttu-id="41595-647">Acceptez la suggestion en ligne ou la suggestion sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="41595-647">Accept the current inline or selected suggestion.</span></span>

- <span data-ttu-id="41595-648">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="41595-648">Function is unbound.</span></span>

### <a name="capturescreen"></a><span data-ttu-id="41595-649">CaptureScreen</span><span class="sxs-lookup"><span data-stu-id="41595-649">CaptureScreen</span></span>

<span data-ttu-id="41595-650">Démarrer la capture d’écran interactive-flèches haut et bas sélectionnez lignes, entrez copie le texte sélectionné dans le presse-papiers en tant que texte et html.</span><span class="sxs-lookup"><span data-stu-id="41595-650">Start interactive screen capture - up/down arrows select lines, enter copies selected text to clipboard as text and html.</span></span>

- <span data-ttu-id="41595-651">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="41595-651">Function is unbound.</span></span>

### <a name="clearscreen"></a><span data-ttu-id="41595-652">ClearScreen</span><span class="sxs-lookup"><span data-stu-id="41595-652">ClearScreen</span></span>

<span data-ttu-id="41595-653">Effacez l’écran et dessinez la ligne active en haut de l’écran.</span><span class="sxs-lookup"><span data-stu-id="41595-653">Clear the screen and draw the current line at the top of the screen.</span></span>

- <span data-ttu-id="41595-654">Cmd `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="41595-654">Cmd: `<Ctrl+l>`</span></span>
- <span data-ttu-id="41595-655">Emacs- `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="41595-655">Emacs: `<Ctrl+l>`</span></span>
- <span data-ttu-id="41595-656">Mode d’insertion VI : `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="41595-656">Vi insert mode: `<Ctrl+l>`</span></span>
- <span data-ttu-id="41595-657">Mode de commande VI : `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="41595-657">Vi command mode: `<Ctrl+l>`</span></span>

### <a name="digitargument"></a><span data-ttu-id="41595-658">DigitArgument</span><span class="sxs-lookup"><span data-stu-id="41595-658">DigitArgument</span></span>

<span data-ttu-id="41595-659">Démarrez un nouvel argument digit à passer à d’autres fonctions.</span><span class="sxs-lookup"><span data-stu-id="41595-659">Start a new digit argument to pass to other functions.</span></span>

- <span data-ttu-id="41595-660">Cmd : `<Alt+0>` ,,,,, `<Alt+1>` `<Alt+2>` `<Alt+3>` `<Alt+4>` `<Alt+5>` , `<Alt+6>` , `<Alt+7>` , `<Alt+8>` , `<Alt+9>` , `<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="41595-660">Cmd: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="41595-661">Emacs-,,,,,,,,, `<Alt+0>` `<Alt+1>` `<Alt+2>` `<Alt+3>` `<Alt+4>` `<Alt+5>` `<Alt+6>` `<Alt+7>` `<Alt+8>` , `<Alt+9>` , `<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="41595-661">Emacs: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="41595-662">Mode de commande VI : `<0>` , `<1>` ,, `<2>` `<3>` , `<4>` , `<5>` , `<6>` , `<7>` , `<8>` , `<9>`</span><span class="sxs-lookup"><span data-stu-id="41595-662">Vi command mode: `<0>`, `<1>`, `<2>`, `<3>`, `<4>`, `<5>`, `<6>`, `<7>`, `<8>`, `<9>`</span></span>

### <a name="invokeprompt"></a><span data-ttu-id="41595-663">InvokePrompt</span><span class="sxs-lookup"><span data-stu-id="41595-663">InvokePrompt</span></span>

<span data-ttu-id="41595-664">Efface l’invite en cours et appelle la fonction prompt pour réafficher l’invite.</span><span class="sxs-lookup"><span data-stu-id="41595-664">Erases the current prompt and calls the prompt function to redisplay the prompt.</span></span> <span data-ttu-id="41595-665">Utile pour les gestionnaires de clés personnalisés qui changent d’État, par exemple modifier le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="41595-665">Useful for custom key handlers that change state, e.g. change the current directory.</span></span>

- <span data-ttu-id="41595-666">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="41595-666">Function is unbound.</span></span>

### <a name="scrolldisplaydown"></a><span data-ttu-id="41595-667">ScrollDisplayDown</span><span class="sxs-lookup"><span data-stu-id="41595-667">ScrollDisplayDown</span></span>

<span data-ttu-id="41595-668">Faites défiler l’écran vers le volet d’affichage.</span><span class="sxs-lookup"><span data-stu-id="41595-668">Scroll the display down one screen.</span></span>

- <span data-ttu-id="41595-669">Cmd `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="41595-669">Cmd: `<PageDown>`</span></span>
- <span data-ttu-id="41595-670">Emacs- `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="41595-670">Emacs: `<PageDown>`</span></span>

### <a name="scrolldisplaydownline"></a><span data-ttu-id="41595-671">ScrollDisplayDownLine</span><span class="sxs-lookup"><span data-stu-id="41595-671">ScrollDisplayDownLine</span></span>

<span data-ttu-id="41595-672">Faites défiler l’affichage d’une ligne vers le dessous.</span><span class="sxs-lookup"><span data-stu-id="41595-672">Scroll the display down one line.</span></span>

- <span data-ttu-id="41595-673">Cmd `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="41595-673">Cmd: `<Ctrl+PageDown>`</span></span>
- <span data-ttu-id="41595-674">Emacs- `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="41595-674">Emacs: `<Ctrl+PageDown>`</span></span>

### <a name="scrolldisplaytocursor"></a><span data-ttu-id="41595-675">ScrollDisplayToCursor</span><span class="sxs-lookup"><span data-stu-id="41595-675">ScrollDisplayToCursor</span></span>

<span data-ttu-id="41595-676">Faites défiler l’affichage jusqu’au curseur.</span><span class="sxs-lookup"><span data-stu-id="41595-676">Scroll the display to the cursor.</span></span>

- <span data-ttu-id="41595-677">Emacs- `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="41595-677">Emacs: `<Ctrl+End>`</span></span>

### <a name="scrolldisplaytop"></a><span data-ttu-id="41595-678">ScrollDisplayTop</span><span class="sxs-lookup"><span data-stu-id="41595-678">ScrollDisplayTop</span></span>

<span data-ttu-id="41595-679">Faites défiler l’affichage vers le haut.</span><span class="sxs-lookup"><span data-stu-id="41595-679">Scroll the display to the top.</span></span>

- <span data-ttu-id="41595-680">Emacs- `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="41595-680">Emacs: `<Ctrl+Home>`</span></span>

### <a name="scrolldisplayup"></a><span data-ttu-id="41595-681">ScrollDisplayUp</span><span class="sxs-lookup"><span data-stu-id="41595-681">ScrollDisplayUp</span></span>

<span data-ttu-id="41595-682">Faites défiler l’écran afficher vers le haut.</span><span class="sxs-lookup"><span data-stu-id="41595-682">Scroll the display up one screen.</span></span>

- <span data-ttu-id="41595-683">Cmd `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="41595-683">Cmd: `<PageUp>`</span></span>
- <span data-ttu-id="41595-684">Emacs- `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="41595-684">Emacs: `<PageUp>`</span></span>

### <a name="scrolldisplayupline"></a><span data-ttu-id="41595-685">ScrollDisplayUpLine</span><span class="sxs-lookup"><span data-stu-id="41595-685">ScrollDisplayUpLine</span></span>

<span data-ttu-id="41595-686">Faites défiler l’affichage d’une ligne vers le haut.</span><span class="sxs-lookup"><span data-stu-id="41595-686">Scroll the display up one line.</span></span>

- <span data-ttu-id="41595-687">Cmd `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="41595-687">Cmd: `<Ctrl+PageUp>`</span></span>
- <span data-ttu-id="41595-688">Emacs- `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="41595-688">Emacs: `<Ctrl+PageUp>`</span></span>

### <a name="selfinsert"></a><span data-ttu-id="41595-689">SelfInsert</span><span class="sxs-lookup"><span data-stu-id="41595-689">SelfInsert</span></span>

<span data-ttu-id="41595-690">Insérez la clé.</span><span class="sxs-lookup"><span data-stu-id="41595-690">Insert the key.</span></span>

- <span data-ttu-id="41595-691">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="41595-691">Function is unbound.</span></span>

### <a name="showkeybindings"></a><span data-ttu-id="41595-692">ShowKeyBindings</span><span class="sxs-lookup"><span data-stu-id="41595-692">ShowKeyBindings</span></span>

<span data-ttu-id="41595-693">Affiche toutes les clés liées.</span><span class="sxs-lookup"><span data-stu-id="41595-693">Show all bound keys.</span></span>

- <span data-ttu-id="41595-694">Cmd `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="41595-694">Cmd: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="41595-695">Emacs- `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="41595-695">Emacs: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="41595-696">Mode d’insertion VI : `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="41595-696">Vi insert mode: `<Ctrl+Alt+?>`</span></span>

### <a name="vicommandmode"></a><span data-ttu-id="41595-697">ViCommandMode</span><span class="sxs-lookup"><span data-stu-id="41595-697">ViCommandMode</span></span>

<span data-ttu-id="41595-698">Basculez le mode d’opération actuel de Vi-Insert à VI-Command.</span><span class="sxs-lookup"><span data-stu-id="41595-698">Switch the current operating mode from Vi-Insert to Vi-Command.</span></span>

- <span data-ttu-id="41595-699">Mode d’insertion VI : `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="41595-699">Vi insert mode: `<Escape>`</span></span>

### <a name="vidigitargumentinchord"></a><span data-ttu-id="41595-700">ViDigitArgumentInChord</span><span class="sxs-lookup"><span data-stu-id="41595-700">ViDigitArgumentInChord</span></span>

<span data-ttu-id="41595-701">Démarrez un nouvel argument digit à passer à d’autres fonctions dans l’un des cordes de VI.</span><span class="sxs-lookup"><span data-stu-id="41595-701">Start a new digit argument to pass to other functions while in one of vi's chords.</span></span>

- <span data-ttu-id="41595-702">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="41595-702">Function is unbound.</span></span>

### <a name="vieditvisually"></a><span data-ttu-id="41595-703">ViEditVisually</span><span class="sxs-lookup"><span data-stu-id="41595-703">ViEditVisually</span></span>

<span data-ttu-id="41595-704">Modifiez la ligne de commande dans un éditeur de texte spécifié par $env : EDITOR ou $env : VISUAL.</span><span class="sxs-lookup"><span data-stu-id="41595-704">Edit the command line in a text editor specified by $env:EDITOR or $env:VISUAL.</span></span>

- <span data-ttu-id="41595-705">Emacs- `<Ctrl+x,Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="41595-705">Emacs: `<Ctrl+x,Ctrl+e>`</span></span>
- <span data-ttu-id="41595-706">Mode de commande VI : `<v>`</span><span class="sxs-lookup"><span data-stu-id="41595-706">Vi command mode: `<v>`</span></span>

### <a name="viexit"></a><span data-ttu-id="41595-707">ViExit</span><span class="sxs-lookup"><span data-stu-id="41595-707">ViExit</span></span>

<span data-ttu-id="41595-708">Quitte l’interpréteur de commandes.</span><span class="sxs-lookup"><span data-stu-id="41595-708">Exits the shell.</span></span>

- <span data-ttu-id="41595-709">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="41595-709">Function is unbound.</span></span>

### <a name="viinsertmode"></a><span data-ttu-id="41595-710">ViInsertMode</span><span class="sxs-lookup"><span data-stu-id="41595-710">ViInsertMode</span></span>

<span data-ttu-id="41595-711">Basculez en mode insertion.</span><span class="sxs-lookup"><span data-stu-id="41595-711">Switch to Insert mode.</span></span>

- <span data-ttu-id="41595-712">Mode de commande VI : `<i>`</span><span class="sxs-lookup"><span data-stu-id="41595-712">Vi command mode: `<i>`</span></span>

### <a name="whatiskey"></a><span data-ttu-id="41595-713">WhatIsKey</span><span class="sxs-lookup"><span data-stu-id="41595-713">WhatIsKey</span></span>

<span data-ttu-id="41595-714">Lisez une clé et dites-moi à quoi la clé est liée.</span><span class="sxs-lookup"><span data-stu-id="41595-714">Read a key and tell me what the key is bound to.</span></span>

- <span data-ttu-id="41595-715">Cmd `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="41595-715">Cmd: `<Alt+?>`</span></span>
- <span data-ttu-id="41595-716">Emacs- `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="41595-716">Emacs: `<Alt+?>`</span></span>

## <a name="selection-functions"></a><span data-ttu-id="41595-717">Fonctions de sélection</span><span class="sxs-lookup"><span data-stu-id="41595-717">Selection functions</span></span>

### <a name="exchangepointandmark"></a><span data-ttu-id="41595-718">ExchangePointAndMark</span><span class="sxs-lookup"><span data-stu-id="41595-718">ExchangePointAndMark</span></span>

<span data-ttu-id="41595-719">Le curseur est placé à l’emplacement de la marque et la marque est déplacée vers l’emplacement du curseur.</span><span class="sxs-lookup"><span data-stu-id="41595-719">The cursor is placed at the location of the mark and the mark is moved to the location of the cursor.</span></span>

- <span data-ttu-id="41595-720">Emacs- `<Ctrl+x,Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="41595-720">Emacs: `<Ctrl+x,Ctrl+x>`</span></span>

### <a name="selectall"></a><span data-ttu-id="41595-721">SelectAll</span><span class="sxs-lookup"><span data-stu-id="41595-721">SelectAll</span></span>

<span data-ttu-id="41595-722">Sélectionnez la ligne entière.</span><span class="sxs-lookup"><span data-stu-id="41595-722">Select the entire line.</span></span>

- <span data-ttu-id="41595-723">Cmd `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="41595-723">Cmd: `<Ctrl+a>`</span></span>

### <a name="selectbackwardchar"></a><span data-ttu-id="41595-724">SelectBackwardChar</span><span class="sxs-lookup"><span data-stu-id="41595-724">SelectBackwardChar</span></span>

<span data-ttu-id="41595-725">Ajustez la sélection actuelle pour inclure le caractère précédent.</span><span class="sxs-lookup"><span data-stu-id="41595-725">Adjust the current selection to include the previous character.</span></span>

- <span data-ttu-id="41595-726">Cmd `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="41595-726">Cmd: `<Shift+LeftArrow>`</span></span>
- <span data-ttu-id="41595-727">Emacs- `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="41595-727">Emacs: `<Shift+LeftArrow>`</span></span>

### <a name="selectbackwardsline"></a><span data-ttu-id="41595-728">SelectBackwardsLine</span><span class="sxs-lookup"><span data-stu-id="41595-728">SelectBackwardsLine</span></span>

<span data-ttu-id="41595-729">Ajustez la sélection actuelle à inclure à partir du curseur jusqu’au début de la ligne.</span><span class="sxs-lookup"><span data-stu-id="41595-729">Adjust the current selection to include from the cursor to the start of the line.</span></span>

- <span data-ttu-id="41595-730">Cmd `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="41595-730">Cmd: `<Shift+Home>`</span></span>
- <span data-ttu-id="41595-731">Emacs- `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="41595-731">Emacs: `<Shift+Home>`</span></span>

### <a name="selectbackwardword"></a><span data-ttu-id="41595-732">SelectBackwardWord</span><span class="sxs-lookup"><span data-stu-id="41595-732">SelectBackwardWord</span></span>

<span data-ttu-id="41595-733">Ajustez la sélection actuelle pour inclure le mot précédent.</span><span class="sxs-lookup"><span data-stu-id="41595-733">Adjust the current selection to include the previous word.</span></span>

- <span data-ttu-id="41595-734">Cmd `<Shift+Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="41595-734">Cmd: `<Shift+Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="41595-735">Emacs- `<Alt+B>`</span><span class="sxs-lookup"><span data-stu-id="41595-735">Emacs: `<Alt+B>`</span></span>

### <a name="selectforwardchar"></a><span data-ttu-id="41595-736">SelectForwardChar</span><span class="sxs-lookup"><span data-stu-id="41595-736">SelectForwardChar</span></span>

<span data-ttu-id="41595-737">Ajustez la sélection actuelle pour inclure le caractère suivant.</span><span class="sxs-lookup"><span data-stu-id="41595-737">Adjust the current selection to include the next character.</span></span>

- <span data-ttu-id="41595-738">Cmd `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="41595-738">Cmd: `<Shift+RightArrow>`</span></span>
- <span data-ttu-id="41595-739">Emacs- `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="41595-739">Emacs: `<Shift+RightArrow>`</span></span>

### <a name="selectforwardword"></a><span data-ttu-id="41595-740">SelectForwardWord</span><span class="sxs-lookup"><span data-stu-id="41595-740">SelectForwardWord</span></span>

<span data-ttu-id="41595-741">Ajustez la sélection actuelle pour inclure le mot suivant à l’aide de ForwardWord.</span><span class="sxs-lookup"><span data-stu-id="41595-741">Adjust the current selection to include the next word using ForwardWord.</span></span>

- <span data-ttu-id="41595-742">Emacs- `<Alt+F>`</span><span class="sxs-lookup"><span data-stu-id="41595-742">Emacs: `<Alt+F>`</span></span>

### <a name="selectline"></a><span data-ttu-id="41595-743">SelectLine</span><span class="sxs-lookup"><span data-stu-id="41595-743">SelectLine</span></span>

<span data-ttu-id="41595-744">Ajustez la sélection actuelle à inclure à partir du curseur jusqu’à la fin de la ligne.</span><span class="sxs-lookup"><span data-stu-id="41595-744">Adjust the current selection to include from the cursor to the end of the line.</span></span>

- <span data-ttu-id="41595-745">Cmd `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="41595-745">Cmd: `<Shift+End>`</span></span>
- <span data-ttu-id="41595-746">Emacs- `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="41595-746">Emacs: `<Shift+End>`</span></span>

### <a name="selectnextword"></a><span data-ttu-id="41595-747">SelectNextWord</span><span class="sxs-lookup"><span data-stu-id="41595-747">SelectNextWord</span></span>

<span data-ttu-id="41595-748">Ajustez la sélection actuelle pour inclure le mot suivant.</span><span class="sxs-lookup"><span data-stu-id="41595-748">Adjust the current selection to include the next word.</span></span>

- <span data-ttu-id="41595-749">Cmd `<Shift+Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="41595-749">Cmd: `<Shift+Ctrl+RightArrow>`</span></span>

### <a name="selectshellbackwardword"></a><span data-ttu-id="41595-750">SelectShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="41595-750">SelectShellBackwardWord</span></span>

<span data-ttu-id="41595-751">Ajustez la sélection actuelle pour inclure le mot précédent à l’aide de ShellBackwardWord.</span><span class="sxs-lookup"><span data-stu-id="41595-751">Adjust the current selection to include the previous word using ShellBackwardWord.</span></span>

- <span data-ttu-id="41595-752">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="41595-752">Function is unbound.</span></span>

### <a name="selectshellforwardword"></a><span data-ttu-id="41595-753">SelectShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="41595-753">SelectShellForwardWord</span></span>

<span data-ttu-id="41595-754">Ajustez la sélection actuelle pour inclure le mot suivant à l’aide de ShellForwardWord.</span><span class="sxs-lookup"><span data-stu-id="41595-754">Adjust the current selection to include the next word using ShellForwardWord.</span></span>

- <span data-ttu-id="41595-755">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="41595-755">Function is unbound.</span></span>

### <a name="selectshellnextword"></a><span data-ttu-id="41595-756">SelectShellNextWord</span><span class="sxs-lookup"><span data-stu-id="41595-756">SelectShellNextWord</span></span>

<span data-ttu-id="41595-757">Ajustez la sélection actuelle pour inclure le mot suivant à l’aide de ShellNextWord.</span><span class="sxs-lookup"><span data-stu-id="41595-757">Adjust the current selection to include the next word using ShellNextWord.</span></span>

- <span data-ttu-id="41595-758">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="41595-758">Function is unbound.</span></span>

### <a name="setmark"></a><span data-ttu-id="41595-759">SetMark</span><span class="sxs-lookup"><span data-stu-id="41595-759">SetMark</span></span>

<span data-ttu-id="41595-760">Marquez l’emplacement actuel du curseur pour une utilisation dans une commande d’édition suivante.</span><span class="sxs-lookup"><span data-stu-id="41595-760">Mark the current location of the cursor for use in a subsequent editing command.</span></span>

- <span data-ttu-id="41595-761">Emacs- `<Ctrl+@>`</span><span class="sxs-lookup"><span data-stu-id="41595-761">Emacs: `<Ctrl+@>`</span></span>

## <a name="predictive-intellisense-functions"></a><span data-ttu-id="41595-762">Fonctions IntelliSense prédictives</span><span class="sxs-lookup"><span data-stu-id="41595-762">Predictive IntelliSense functions</span></span>

> [!NOTE]
> <span data-ttu-id="41595-763">La fonctionnalité IntelliSense prédictive doit être activée pour utiliser ces fonctions.</span><span class="sxs-lookup"><span data-stu-id="41595-763">Predictive IntelliSense needs to be enabled to use these functions.</span></span>

### <a name="acceptnextwordsuggestion"></a><span data-ttu-id="41595-764">AcceptNextWordSuggestion</span><span class="sxs-lookup"><span data-stu-id="41595-764">AcceptNextWordSuggestion</span></span>

<span data-ttu-id="41595-765">Accepte le mot suivant de la suggestion en ligne de la fonctionnalité IntelliSense prédictive.</span><span class="sxs-lookup"><span data-stu-id="41595-765">Accepts the next word of the inline suggestion from Predictive IntelliSense.</span></span>
<span data-ttu-id="41595-766">Cette fonction peut être liée à l’aide de <kbd>CTRL</kbd> + <kbd>F</kbd> en exécutant la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="41595-766">This function can be bound with <kbd>Ctrl</kbd>+<kbd>F</kbd> by running the following command.</span></span>

```powershell
Set-PSReadLineKeyHandler -Chord "Ctrl+f" -Function ForwardWord
```

### <a name="acceptsuggestion"></a><span data-ttu-id="41595-767">AcceptSuggestion</span><span class="sxs-lookup"><span data-stu-id="41595-767">AcceptSuggestion</span></span>

<span data-ttu-id="41595-768">Accepte la suggestion en ligne actuelle de la fonctionnalité IntelliSense prédictive en appuyant sur <kbd>flèche droite</kbd> lorsque le curseur se trouve à la fin de la ligne active.</span><span class="sxs-lookup"><span data-stu-id="41595-768">Accepts the current inline suggestion from Predictive IntelliSense by pressing <kbd>RightArrow</kbd> when the cursor is at the end of the current line.</span></span>

## <a name="search-functions"></a><span data-ttu-id="41595-769">Fonctions de recherche</span><span class="sxs-lookup"><span data-stu-id="41595-769">Search functions</span></span>

### <a name="charactersearch"></a><span data-ttu-id="41595-770">CharacterSearch</span><span class="sxs-lookup"><span data-stu-id="41595-770">CharacterSearch</span></span>

<span data-ttu-id="41595-771">Lisez un caractère et recherchez l’occurrence suivante de ce caractère.</span><span class="sxs-lookup"><span data-stu-id="41595-771">Read a character and search forward for the next occurrence of that character.</span></span>
<span data-ttu-id="41595-772">Si un argument est spécifié, effectuez une recherche vers l’avant (ou vers l’arrière si négatif) pour la nième occurrence.</span><span class="sxs-lookup"><span data-stu-id="41595-772">If an argument is specified, search forward (or backward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="41595-773">Cmd `<F3>`</span><span class="sxs-lookup"><span data-stu-id="41595-773">Cmd: `<F3>`</span></span>
- <span data-ttu-id="41595-774">Emacs- `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="41595-774">Emacs: `<Ctrl+]>`</span></span>
- <span data-ttu-id="41595-775">Mode d’insertion VI : `<F3>`</span><span class="sxs-lookup"><span data-stu-id="41595-775">Vi insert mode: `<F3>`</span></span>
- <span data-ttu-id="41595-776">Mode de commande VI : `<F3>`</span><span class="sxs-lookup"><span data-stu-id="41595-776">Vi command mode: `<F3>`</span></span>

### <a name="charactersearchbackward"></a><span data-ttu-id="41595-777">CharacterSearchBackward</span><span class="sxs-lookup"><span data-stu-id="41595-777">CharacterSearchBackward</span></span>

<span data-ttu-id="41595-778">Lisez un caractère et recherchez l’occurrence suivante de ce caractère.</span><span class="sxs-lookup"><span data-stu-id="41595-778">Read a character and search backward for the next occurrence of that character.</span></span> <span data-ttu-id="41595-779">Si un argument est spécifié, effectuez une recherche vers l’arrière (ou vers l’avant si négatif) pour la nième occurrence.</span><span class="sxs-lookup"><span data-stu-id="41595-779">If an argument is specified, search backward (or forward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="41595-780">Cmd `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="41595-780">Cmd: `<Shift+F3>`</span></span>
- <span data-ttu-id="41595-781">Emacs- `<Ctrl+Alt+]>`</span><span class="sxs-lookup"><span data-stu-id="41595-781">Emacs: `<Ctrl+Alt+]>`</span></span>
- <span data-ttu-id="41595-782">Mode d’insertion VI : `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="41595-782">Vi insert mode: `<Shift+F3>`</span></span>
- <span data-ttu-id="41595-783">Mode de commande VI : `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="41595-783">Vi command mode: `<Shift+F3>`</span></span>

### <a name="repeatlastcharsearch"></a><span data-ttu-id="41595-784">RepeatLastCharSearch</span><span class="sxs-lookup"><span data-stu-id="41595-784">RepeatLastCharSearch</span></span>

<span data-ttu-id="41595-785">Répète la dernière recherche de caractères enregistrée.</span><span class="sxs-lookup"><span data-stu-id="41595-785">Repeat the last recorded character search.</span></span>

- <span data-ttu-id="41595-786">Mode de commande VI : `<;>`</span><span class="sxs-lookup"><span data-stu-id="41595-786">Vi command mode: `<;>`</span></span>

### <a name="repeatlastcharsearchbackwards"></a><span data-ttu-id="41595-787">RepeatLastCharSearchBackwards</span><span class="sxs-lookup"><span data-stu-id="41595-787">RepeatLastCharSearchBackwards</span></span>

<span data-ttu-id="41595-788">Répète la dernière recherche de caractères enregistrée, mais dans la direction opposée.</span><span class="sxs-lookup"><span data-stu-id="41595-788">Repeat the last recorded character search, but in the opposite direction.</span></span>

- <span data-ttu-id="41595-789">Mode de commande VI : `<,>`</span><span class="sxs-lookup"><span data-stu-id="41595-789">Vi command mode: `<,>`</span></span>

### <a name="repeatsearch"></a><span data-ttu-id="41595-790">RepeatSearch</span><span class="sxs-lookup"><span data-stu-id="41595-790">RepeatSearch</span></span>

<span data-ttu-id="41595-791">Répétez la dernière recherche dans la même direction que précédemment.</span><span class="sxs-lookup"><span data-stu-id="41595-791">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="41595-792">Mode de commande VI : `<n>`</span><span class="sxs-lookup"><span data-stu-id="41595-792">Vi command mode: `<n>`</span></span>

### <a name="repeatsearchbackward"></a><span data-ttu-id="41595-793">RepeatSearchBackward</span><span class="sxs-lookup"><span data-stu-id="41595-793">RepeatSearchBackward</span></span>

<span data-ttu-id="41595-794">Répétez la dernière recherche dans la même direction que précédemment.</span><span class="sxs-lookup"><span data-stu-id="41595-794">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="41595-795">Mode de commande VI : `<N>`</span><span class="sxs-lookup"><span data-stu-id="41595-795">Vi command mode: `<N>`</span></span>

### <a name="searchchar"></a><span data-ttu-id="41595-796">SearchChar</span><span class="sxs-lookup"><span data-stu-id="41595-796">SearchChar</span></span>

<span data-ttu-id="41595-797">Lisez le caractère suivant, puis recherchez-le, à l’avenir, puis annulez un caractère.</span><span class="sxs-lookup"><span data-stu-id="41595-797">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="41595-798">Il s’agit de la fonctionnalité’t'.</span><span class="sxs-lookup"><span data-stu-id="41595-798">This is for 't' functionality.</span></span>

- <span data-ttu-id="41595-799">Mode de commande VI : `<f>`</span><span class="sxs-lookup"><span data-stu-id="41595-799">Vi command mode: `<f>`</span></span>

### <a name="searchcharbackward"></a><span data-ttu-id="41595-800">SearchCharBackward</span><span class="sxs-lookup"><span data-stu-id="41595-800">SearchCharBackward</span></span>

<span data-ttu-id="41595-801">Lisez le caractère suivant, puis recherchez-le, en accédant à l’arrière, puis en annulant un caractère.</span><span class="sxs-lookup"><span data-stu-id="41595-801">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="41595-802">Il s’agit de la fonctionnalité’t'.</span><span class="sxs-lookup"><span data-stu-id="41595-802">This is for 'T' functionality.</span></span>

- <span data-ttu-id="41595-803">Mode de commande VI : `<F>`</span><span class="sxs-lookup"><span data-stu-id="41595-803">Vi command mode: `<F>`</span></span>

### <a name="searchcharbackwardwithbackoff"></a><span data-ttu-id="41595-804">SearchCharBackwardWithBackoff</span><span class="sxs-lookup"><span data-stu-id="41595-804">SearchCharBackwardWithBackoff</span></span>

<span data-ttu-id="41595-805">Lisez le caractère suivant, puis recherchez-le, en accédant à l’arrière, puis en annulant un caractère.</span><span class="sxs-lookup"><span data-stu-id="41595-805">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="41595-806">Il s’agit de la fonctionnalité’t'.</span><span class="sxs-lookup"><span data-stu-id="41595-806">This is for 'T' functionality.</span></span>

- <span data-ttu-id="41595-807">Mode de commande VI : `<T>`</span><span class="sxs-lookup"><span data-stu-id="41595-807">Vi command mode: `<T>`</span></span>

### <a name="searchcharwithbackoff"></a><span data-ttu-id="41595-808">SearchCharWithBackoff</span><span class="sxs-lookup"><span data-stu-id="41595-808">SearchCharWithBackoff</span></span>

<span data-ttu-id="41595-809">Lisez le caractère suivant, puis recherchez-le, à l’avenir, puis annulez un caractère.</span><span class="sxs-lookup"><span data-stu-id="41595-809">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="41595-810">Il s’agit de la fonctionnalité’t'.</span><span class="sxs-lookup"><span data-stu-id="41595-810">This is for 't' functionality.</span></span>

- <span data-ttu-id="41595-811">Mode de commande VI : `<t>`</span><span class="sxs-lookup"><span data-stu-id="41595-811">Vi command mode: `<t>`</span></span>

### <a name="searchforward"></a><span data-ttu-id="41595-812">SearchForward</span><span class="sxs-lookup"><span data-stu-id="41595-812">SearchForward</span></span>

<span data-ttu-id="41595-813">Demande une chaîne de recherche et lance la recherche sur AcceptLine.</span><span class="sxs-lookup"><span data-stu-id="41595-813">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="41595-814">Mode d’insertion VI : `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="41595-814">Vi insert mode: `<Ctrl+s>`</span></span>
- <span data-ttu-id="41595-815">Mode de commande VI : `<?>` , `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="41595-815">Vi command mode: `<?>`, `<Ctrl+s>`</span></span>

## <a name="custom-key-bindings"></a><span data-ttu-id="41595-816">Combinaisons de touches personnalisées</span><span class="sxs-lookup"><span data-stu-id="41595-816">Custom Key Bindings</span></span>

<span data-ttu-id="41595-817">PSReadLine prend en charge les combinaisons de touches personnalisées à l’aide de l’applet de commande `Set-PSReadLineKeyHandler` .</span><span class="sxs-lookup"><span data-stu-id="41595-817">PSReadLine supports custom key bindings using the cmdlet `Set-PSReadLineKeyHandler`.</span></span> <span data-ttu-id="41595-818">La plupart des combinaisons de touches personnalisées appellent l’une des fonctions ci-dessus, par exemple</span><span class="sxs-lookup"><span data-stu-id="41595-818">Most custom key bindings call one of the above functions, for example</span></span>

```powershell
Set-PSReadLineKeyHandler -Key UpArrow -Function HistorySearchBackward
```

<span data-ttu-id="41595-819">Vous pouvez lier un ScriptBlock à une clé.</span><span class="sxs-lookup"><span data-stu-id="41595-819">You can bind a ScriptBlock to a key.</span></span> <span data-ttu-id="41595-820">Le ScriptBlock peut faire à peu près tout ce que vous voulez.</span><span class="sxs-lookup"><span data-stu-id="41595-820">The ScriptBlock can do pretty much anything you want.</span></span> <span data-ttu-id="41595-821">Voici quelques exemples utiles :</span><span class="sxs-lookup"><span data-stu-id="41595-821">Some useful examples include</span></span>

- <span data-ttu-id="41595-822">modifier la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="41595-822">edit the command line</span></span>
- <span data-ttu-id="41595-823">ouverture d’une nouvelle fenêtre (par exemple, aide)</span><span class="sxs-lookup"><span data-stu-id="41595-823">opening a new window (e.g. help)</span></span>
- <span data-ttu-id="41595-824">modifier les répertoires sans modifier la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="41595-824">change directories without changing the command line</span></span>

<span data-ttu-id="41595-825">Le ScriptBlock reçoit deux arguments :</span><span class="sxs-lookup"><span data-stu-id="41595-825">The ScriptBlock receives two arguments:</span></span>

- <span data-ttu-id="41595-826">`$key` -Objet **[ConsoleKeyInfo]** qui est la clé qui a déclenché la liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="41595-826">`$key` - A **[ConsoleKeyInfo]** object that is the key that triggered the custom binding.</span></span> <span data-ttu-id="41595-827">Si vous liez le même ScriptBlock à plusieurs clés et que vous devez effectuer des actions différentes en fonction de la clé, vous pouvez vérifier $key.</span><span class="sxs-lookup"><span data-stu-id="41595-827">If you bind the same ScriptBlock to multiple keys and need to perform different actions depending on the key, you can check $key.</span></span> <span data-ttu-id="41595-828">De nombreuses liaisons personnalisées ignorent cet argument.</span><span class="sxs-lookup"><span data-stu-id="41595-828">Many custom bindings ignore this argument.</span></span>

- <span data-ttu-id="41595-829">`$arg` : Argument arbitraire.</span><span class="sxs-lookup"><span data-stu-id="41595-829">`$arg` - An arbitrary argument.</span></span> <span data-ttu-id="41595-830">Le plus souvent, il s’agit d’un argument entier que l’utilisateur passe à partir des combinaisons de touches DigitArgument.</span><span class="sxs-lookup"><span data-stu-id="41595-830">Most often, this would be an integer argument that the user passes from the key bindings DigitArgument.</span></span> <span data-ttu-id="41595-831">Si votre liaison n’accepte pas d’arguments, il est raisonnable d’ignorer cet argument.</span><span class="sxs-lookup"><span data-stu-id="41595-831">If your binding doesn't accept arguments, it's reasonable to ignore this argument.</span></span>

<span data-ttu-id="41595-832">Jetons un coup d’œil à un exemple qui ajoute une ligne de commande à l’historique sans l’exécuter.</span><span class="sxs-lookup"><span data-stu-id="41595-832">Let's take a look at an example that adds a command line to history without executing it.</span></span> <span data-ttu-id="41595-833">Cela est utile lorsque vous vous rendez compte que vous avez oublié d’effectuer une opération, mais que vous ne voulez pas entrer à nouveau la ligne de commande que vous avez déjà entrée.</span><span class="sxs-lookup"><span data-stu-id="41595-833">This is useful when you realize you forgot to do something, but don't want to re-enter the command line you've already entered.</span></span>

```powershell
$parameters = @{
    Key = 'Alt+w'
    BriefDescription = 'SaveInHistory'
    LongDescription = 'Save current line in history but do not execute'
    ScriptBlock = {
      param($key, $arg)   # The arguments are ignored in this example

      # GetBufferState gives us the command line (with the cursor position)
      $line = $null
      $cursor = $null
      [Microsoft.PowerShell.PSConsoleReadLine]::GetBufferState([ref]$line,
        [ref]$cursor)

      # AddToHistory saves the line in history, but does not execute it.
      [Microsoft.PowerShell.PSConsoleReadLine]::AddToHistory($line)

      # RevertLine is like pressing Escape.
      [Microsoft.PowerShell.PSConsoleReadLine]::RevertLine()
  }
}
Set-PSReadLineKeyHandler @parameters
```

<span data-ttu-id="41595-834">Vous pouvez voir beaucoup plus d’exemples dans le fichier `SamplePSReadLineProfile.ps1` qui est installé dans le dossier du module PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="41595-834">You can see many more examples in the file `SamplePSReadLineProfile.ps1` which is installed in the PSReadLine module folder.</span></span>

<span data-ttu-id="41595-835">La plupart des combinaisons de touches utilisent des fonctions d’assistance pour la modification de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="41595-835">Most key bindings use some helper functions for editing the command line.</span></span>
<span data-ttu-id="41595-836">Ces API sont documentées dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="41595-836">Those APIs are documented in the next section.</span></span>

## <a name="custom-key-binding-support-apis"></a><span data-ttu-id="41595-837">API de prise en charge de la liaison de clé personnalisée</span><span class="sxs-lookup"><span data-stu-id="41595-837">Custom Key Binding Support APIs</span></span>

<span data-ttu-id="41595-838">Les fonctions suivantes sont publiques dans Microsoft. PowerShell. PSConsoleReadLine, mais ne peuvent pas être directement liées à une clé.</span><span class="sxs-lookup"><span data-stu-id="41595-838">The following functions are public in Microsoft.PowerShell.PSConsoleReadLine, but cannot be directly bound to a key.</span></span> <span data-ttu-id="41595-839">La plupart sont utiles dans les combinaisons de touches personnalisées.</span><span class="sxs-lookup"><span data-stu-id="41595-839">Most are useful in custom key bindings.</span></span>

```csharp
void AddToHistory(string command)
```

<span data-ttu-id="41595-840">Ajoutez une ligne de commande à l’historique sans l’exécuter.</span><span class="sxs-lookup"><span data-stu-id="41595-840">Add a command line to history without executing it.</span></span>

```csharp
void ClearKillRing()
```

<span data-ttu-id="41595-841">Effacez le point d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="41595-841">Clear the kill-ring.</span></span>  <span data-ttu-id="41595-842">Cela est principalement utilisé pour les tests.</span><span class="sxs-lookup"><span data-stu-id="41595-842">This is mostly used for testing.</span></span>

```csharp
void Delete(int start, int length)
```

<span data-ttu-id="41595-843">Supprimer les caractères de longueur du début.</span><span class="sxs-lookup"><span data-stu-id="41595-843">Delete length characters from start.</span></span>  <span data-ttu-id="41595-844">Cette opération prend en charge les opérations d’annulation et de rétablissement.</span><span class="sxs-lookup"><span data-stu-id="41595-844">This operation supports undo/redo.</span></span>

```csharp
void Ding()
```

<span data-ttu-id="41595-845">Effectuez l’action Ding en fonction des préférences de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="41595-845">Perform the Ding action based on the users preference.</span></span>

```csharp
void GetBufferState([ref] string input, [ref] int cursor)
void GetBufferState([ref] Ast ast, [ref] Token[] tokens,
  [ref] ParseError[] parseErrors, [ref] int cursor)
```

<span data-ttu-id="41595-846">Ces deux fonctions récupèrent des informations utiles sur l’état actuel de la mémoire tampon d’entrée.</span><span class="sxs-lookup"><span data-stu-id="41595-846">These two functions retrieve useful information about the current state of the input buffer.</span></span>  <span data-ttu-id="41595-847">La première est plus couramment utilisée dans les cas simples.</span><span class="sxs-lookup"><span data-stu-id="41595-847">The first is more commonly used for simple cases.</span></span>  <span data-ttu-id="41595-848">Le second est utilisé si votre liaison fait une opération plus avancée avec l’AST.</span><span class="sxs-lookup"><span data-stu-id="41595-848">The second is used if your binding is doing something more advanced with the Ast.</span></span>

```csharp
IEnumerable[Microsoft.PowerShell.KeyHandler]
  GetKeyHandlers(bool includeBound, bool includeUnbound)

IEnumerable[Microsoft.PowerShell.KeyHandler]
  GetKeyHandlers(string[] Chord)
```

<span data-ttu-id="41595-849">Ces deux fonctions sont utilisées par `Get-PSReadLineKeyHandler` .</span><span class="sxs-lookup"><span data-stu-id="41595-849">These two functions are used by `Get-PSReadLineKeyHandler`.</span></span> <span data-ttu-id="41595-850">La première est utilisée pour récupérer toutes les combinaisons de touches.</span><span class="sxs-lookup"><span data-stu-id="41595-850">The first is used to get all key bindings.</span></span> <span data-ttu-id="41595-851">Le second est utilisé pour recevoir des combinaisons de touches spécifiques.</span><span class="sxs-lookup"><span data-stu-id="41595-851">The second is used to get specific key bindings.</span></span>

```csharp
Microsoft.PowerShell.PSConsoleReadLineOptions GetOptions()
```

<span data-ttu-id="41595-852">Cette fonction est utilisée par Get-PSReadLineOption et n’est probablement pas trop utile dans une liaison de clé personnalisée.</span><span class="sxs-lookup"><span data-stu-id="41595-852">This function is used by Get-PSReadLineOption and probably isn't too useful in a custom key binding.</span></span>

```csharp
void GetSelectionState([ref] int start, [ref] int length)
```

<span data-ttu-id="41595-853">Si aucune sélection n’est effectuée sur la ligne de commande,-1 est retourné à la fois en début et en longueur.</span><span class="sxs-lookup"><span data-stu-id="41595-853">If there is no selection on the command line, -1 will be returned in both start and length.</span></span> <span data-ttu-id="41595-854">Si une sélection est effectuée sur la ligne de commande, le début et la longueur de la sélection sont retournés.</span><span class="sxs-lookup"><span data-stu-id="41595-854">If there is a selection on the command line, the start and length of the selection are returned.</span></span>

```csharp
void Insert(char c)
void Insert(string s)
```

<span data-ttu-id="41595-855">Insérez un caractère ou une chaîne au niveau du curseur.</span><span class="sxs-lookup"><span data-stu-id="41595-855">Insert a character or string at the cursor.</span></span>  <span data-ttu-id="41595-856">Cette opération prend en charge les opérations d’annulation et de rétablissement.</span><span class="sxs-lookup"><span data-stu-id="41595-856">This operation supports undo/redo.</span></span>

```csharp
string ReadLine(runspace remoteRunspace,
  System.Management.Automation.EngineIntrinsics engineIntrinsics)
```

<span data-ttu-id="41595-857">Il s’agit du point d’entrée principal de PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="41595-857">This is the main entry point to PSReadLine.</span></span> <span data-ttu-id="41595-858">Comme il ne prend pas en charge la récursivité, il n’est pas utile dans une liaison de clé personnalisée.</span><span class="sxs-lookup"><span data-stu-id="41595-858">It does not support recursion, so is not useful in a custom key binding.</span></span>

```csharp
void RemoveKeyHandler(string[] key)
```

<span data-ttu-id="41595-859">Cette fonction est utilisée par Remove-PSReadLineKeyHandler et n’est probablement pas trop utile dans une liaison de clé personnalisée.</span><span class="sxs-lookup"><span data-stu-id="41595-859">This function is used by Remove-PSReadLineKeyHandler and probably isn't too useful in a custom key binding.</span></span>

```csharp
void Replace(int start, int length, string replacement)
```

<span data-ttu-id="41595-860">Remplacez une partie de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="41595-860">Replace some of the input.</span></span> <span data-ttu-id="41595-861">Cette opération prend en charge les opérations d’annulation et de rétablissement.</span><span class="sxs-lookup"><span data-stu-id="41595-861">This operation supports undo/redo.</span></span> <span data-ttu-id="41595-862">C’est préférable à Delete, suivi de Insert, car il est traité comme une action unique pour Undo.</span><span class="sxs-lookup"><span data-stu-id="41595-862">This is preferred over Delete followed by Insert because it is treated as a single action for undo.</span></span>

```csharp
void SetCursorPosition(int cursor)
```

<span data-ttu-id="41595-863">Déplacer le curseur vers l’offset donné.</span><span class="sxs-lookup"><span data-stu-id="41595-863">Move the cursor to the given offset.</span></span> <span data-ttu-id="41595-864">Le déplacement du curseur n’est pas suivi pour l’annulation.</span><span class="sxs-lookup"><span data-stu-id="41595-864">Cursor movement is not tracked for undo.</span></span>

```csharp
void SetOptions(Microsoft.PowerShell.SetPSReadLineOption options)
```

<span data-ttu-id="41595-865">Cette fonction est une méthode d’assistance utilisée par l’applet de commande Set-PSReadLineOption, mais peut être utile pour une combinaison de touches personnalisée qui souhaite modifier temporairement un paramètre.</span><span class="sxs-lookup"><span data-stu-id="41595-865">This function is a helper method used by the cmdlet Set-PSReadLineOption, but might be useful to a custom key binding that wants to temporarily change a setting.</span></span>

```csharp
bool TryGetArgAsInt(System.Object arg, [ref] int numericArg,
  int defaultNumericArg)
```

<span data-ttu-id="41595-866">Cette méthode d’assistance est utilisée pour les liaisons personnalisées qui respectent DigitArgument.</span><span class="sxs-lookup"><span data-stu-id="41595-866">This helper method is used for custom bindings that honor DigitArgument.</span></span> <span data-ttu-id="41595-867">Un appel classique ressemble à ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="41595-867">A typical call looks like</span></span>

```powershell
[int]$numericArg = 0
[Microsoft.PowerShell.PSConsoleReadLine]::TryGetArgAsInt($arg,
  [ref]$numericArg, 1)
```

## <a name="note"></a><span data-ttu-id="41595-868">Notes</span><span class="sxs-lookup"><span data-stu-id="41595-868">Note</span></span>

### <a name="command-history"></a><span data-ttu-id="41595-869">Historique des commandes</span><span class="sxs-lookup"><span data-stu-id="41595-869">Command History</span></span>

<span data-ttu-id="41595-870">PSReadLine gère un fichier d’historique contenant toutes les commandes et données que vous avez entrées à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="41595-870">PSReadLine maintains a history file containing all the commands and data you have entered from the command line.</span></span> <span data-ttu-id="41595-871">Cela peut contenir des données sensibles, y compris des mots de passe.</span><span class="sxs-lookup"><span data-stu-id="41595-871">This may contain sensitive data including passwords.</span></span> <span data-ttu-id="41595-872">Par exemple, si vous utilisez l’applet de commande, `ConvertTo-SecureString` le mot de passe est enregistré dans le fichier d’historique sous forme de texte brut.</span><span class="sxs-lookup"><span data-stu-id="41595-872">For example, if you use the `ConvertTo-SecureString` cmdlet the password is logged in the history file as plain text.</span></span> <span data-ttu-id="41595-873">Les fichiers d’historique sont un fichier nommé `$($host.Name)_history.txt` .</span><span class="sxs-lookup"><span data-stu-id="41595-873">The history files is a file named `$($host.Name)_history.txt`.</span></span> <span data-ttu-id="41595-874">Sur les systèmes Windows, le fichier d’historique est stocké à l’adresse `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine` .</span><span class="sxs-lookup"><span data-stu-id="41595-874">On Windows systems the history file is stored at `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine`.</span></span> <span data-ttu-id="41595-875">Sur les systèmes non-Windows, les fichiers d’historique sont stockés dans `$env:XDG_DATA_HOME/powershell/PSReadLine` ou `$env:HOME/.local/share/powershell/PSReadLine` .</span><span class="sxs-lookup"><span data-stu-id="41595-875">On non-Windows systems, the history files is stored at `$env:XDG_DATA_HOME/powershell/PSReadLine` or `$env:HOME/.local/share/powershell/PSReadLine`.</span></span>

### <a name="feedback--contributing-to-psreadline"></a><span data-ttu-id="41595-876">Commentaires & contribution à PSReadLine</span><span class="sxs-lookup"><span data-stu-id="41595-876">Feedback & Contributing To PSReadLine</span></span>

[<span data-ttu-id="41595-877">PSReadLine sur GitHub</span><span class="sxs-lookup"><span data-stu-id="41595-877">PSReadLine on GitHub</span></span>](https://github.com/PowerShell/PSReadLine)

<span data-ttu-id="41595-878">N’hésitez pas à envoyer une demande de tirage ou à envoyer des commentaires sur la page GitHub.</span><span class="sxs-lookup"><span data-stu-id="41595-878">Feel free to submit a pull request or submit feedback on the GitHub page.</span></span>

## <a name="see-also"></a><span data-ttu-id="41595-879">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="41595-879">See Also</span></span>

<span data-ttu-id="41595-880">PSReadLine est fortement influencé par la bibliothèque GNU [ReadLine](https://tiswww.case.edu/php/chet/readline/rltop.html) .</span><span class="sxs-lookup"><span data-stu-id="41595-880">PSReadLine is heavily influenced by the GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) library.</span></span>
