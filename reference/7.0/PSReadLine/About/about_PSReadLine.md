---
description: PSReadLine fournit une expérience d’édition de ligne de commande améliorée dans la console PowerShell.
keywords: powershell
Locale: en-US
ms.date: 02/10/2020
online version: https://docs.microsoft.com/powershell/module/psreadline/about/about_psreadline?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: À propos de PSReadLine
ms.openlocfilehash: 890f8e92172f2d492b6b817b558d4f25c70e8949
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206561"
---
# <a name="psreadline"></a><span data-ttu-id="93f26-104">PSReadLine</span><span class="sxs-lookup"><span data-stu-id="93f26-104">PSReadLine</span></span>

## <a name="about_psreadline"></a><span data-ttu-id="93f26-105">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="93f26-105">about_PSReadLine</span></span>

## <a name="short-description"></a><span data-ttu-id="93f26-106">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="93f26-106">SHORT DESCRIPTION</span></span>

<span data-ttu-id="93f26-107">PSReadLine fournit une expérience d’édition de ligne de commande améliorée dans la console PowerShell.</span><span class="sxs-lookup"><span data-stu-id="93f26-107">PSReadLine provides an improved command-line editing experience in the PowerShell console.</span></span>

## <a name="long-description"></a><span data-ttu-id="93f26-108">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="93f26-108">LONG DESCRIPTION</span></span>

<span data-ttu-id="93f26-109">PSReadLine 2,0 fournit une expérience d’édition de ligne de commande puissante pour la console PowerShell.</span><span class="sxs-lookup"><span data-stu-id="93f26-109">PSReadLine 2.0 provides a powerful command-line editing experience for the PowerShell console.</span></span> <span data-ttu-id="93f26-110">Elle offre les possibilités suivantes :</span><span class="sxs-lookup"><span data-stu-id="93f26-110">It provides:</span></span>

- <span data-ttu-id="93f26-111">Coloration de la syntaxe de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="93f26-111">Syntax coloring of the command line</span></span>
- <span data-ttu-id="93f26-112">Indication visuelle des erreurs de syntaxe</span><span class="sxs-lookup"><span data-stu-id="93f26-112">A visual indication of syntax errors</span></span>
- <span data-ttu-id="93f26-113">Une meilleure expérience multi-ligne (modification et historique)</span><span class="sxs-lookup"><span data-stu-id="93f26-113">A better multi-line experience (both editing and history)</span></span>
- <span data-ttu-id="93f26-114">Combinaisons de touches personnalisables</span><span class="sxs-lookup"><span data-stu-id="93f26-114">Customizable key bindings</span></span>
- <span data-ttu-id="93f26-115">Modes cmd et Emacs</span><span class="sxs-lookup"><span data-stu-id="93f26-115">Cmd and Emacs modes</span></span>
- <span data-ttu-id="93f26-116">Nombreuses options de configuration</span><span class="sxs-lookup"><span data-stu-id="93f26-116">Many configuration options</span></span>
- <span data-ttu-id="93f26-117">Saisie semi-automatique du style bash (facultatif en mode cmd, par défaut en mode emacs)</span><span class="sxs-lookup"><span data-stu-id="93f26-117">Bash style completion (optional in Cmd mode, default in Emacs mode)</span></span>
- <span data-ttu-id="93f26-118">Emacs-Yank/Kill-Ring</span><span class="sxs-lookup"><span data-stu-id="93f26-118">Emacs yank/kill-ring</span></span>
- <span data-ttu-id="93f26-119">Mouvement « mot » basé sur un jeton PowerShell et Kill</span><span class="sxs-lookup"><span data-stu-id="93f26-119">PowerShell token based "word" movement and kill</span></span>

<span data-ttu-id="93f26-120">Les fonctions suivantes sont disponibles dans la classe **[Microsoft. PowerShell. PSConsoleReadLine]** .</span><span class="sxs-lookup"><span data-stu-id="93f26-120">The following functions are available in the class **[Microsoft.PowerShell.PSConsoleReadLine]** .</span></span>

> [!NOTE]
> <span data-ttu-id="93f26-121">À compter de PowerShell 7,0, PowerShell ignore le chargement automatique de PSReadLine sur Windows si un programme de lecture d’écran est détecté.</span><span class="sxs-lookup"><span data-stu-id="93f26-121">Beginning with PowerShell 7.0, PowerShell skips auto-loading PSReadLine on Windows if a screen reader program is detected.</span></span> <span data-ttu-id="93f26-122">Actuellement, PSReadLine ne fonctionne pas correctement avec les lecteurs d’écran.</span><span class="sxs-lookup"><span data-stu-id="93f26-122">Currently, PSReadLine doesn't work well with the screen readers.</span></span> <span data-ttu-id="93f26-123">Le rendu et la mise en forme par défaut de PowerShell 7,0 sur Windows fonctionnent correctement.</span><span class="sxs-lookup"><span data-stu-id="93f26-123">The default rendering and formatting of PowerShell 7.0 on Windows works properly.</span></span> <span data-ttu-id="93f26-124">Vous pouvez charger le module manuellement, si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="93f26-124">You can manually load the module if necessary.</span></span>

## <a name="basic-editing-functions"></a><span data-ttu-id="93f26-125">Fonctions d’édition de base</span><span class="sxs-lookup"><span data-stu-id="93f26-125">Basic editing functions</span></span>

### <a name="abort"></a><span data-ttu-id="93f26-126">Abandon</span><span class="sxs-lookup"><span data-stu-id="93f26-126">Abort</span></span>

<span data-ttu-id="93f26-127">Annuler l’action en cours, par exemple, recherche de l’historique incrémentiel.</span><span class="sxs-lookup"><span data-stu-id="93f26-127">Abort current action, e.g. incremental history search.</span></span>

- <span data-ttu-id="93f26-128">Emacs- `<Ctrl+g>`</span><span class="sxs-lookup"><span data-stu-id="93f26-128">Emacs: `<Ctrl+g>`</span></span>

### <a name="acceptandgetnext"></a><span data-ttu-id="93f26-129">AcceptAndGetNext</span><span class="sxs-lookup"><span data-stu-id="93f26-129">AcceptAndGetNext</span></span>

<span data-ttu-id="93f26-130">Tentative d’exécution de l’entrée en cours.</span><span class="sxs-lookup"><span data-stu-id="93f26-130">Attempt to execute the current input.</span></span> <span data-ttu-id="93f26-131">Si elle peut être exécutée (par exemple, AcceptLine), rappelez l’élément suivant de l’historique la prochaine fois que ReadLine est appelé.</span><span class="sxs-lookup"><span data-stu-id="93f26-131">If it can be executed (like AcceptLine), then recall the next item from history the next time ReadLine is called.</span></span>

- <span data-ttu-id="93f26-132">Emacs- `<Ctrl+o>`</span><span class="sxs-lookup"><span data-stu-id="93f26-132">Emacs: `<Ctrl+o>`</span></span>

### <a name="acceptline"></a><span data-ttu-id="93f26-133">AcceptLine</span><span class="sxs-lookup"><span data-stu-id="93f26-133">AcceptLine</span></span>

<span data-ttu-id="93f26-134">Tentative d’exécution de l’entrée en cours.</span><span class="sxs-lookup"><span data-stu-id="93f26-134">Attempt to execute the current input.</span></span> <span data-ttu-id="93f26-135">Si l’entrée actuelle est incomplète (par exemple, il manque une parenthèse fermante, un crochet ou un guillemet, l’invite de continuation est affichée sur la ligne suivante et PSReadLine attend que les clés modifient l’entrée actuelle.</span><span class="sxs-lookup"><span data-stu-id="93f26-135">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="93f26-136">Cmd `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="93f26-136">Cmd: `<Enter>`</span></span>
- <span data-ttu-id="93f26-137">Emacs- `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="93f26-137">Emacs: `<Enter>`</span></span>
- <span data-ttu-id="93f26-138">Mode d’insertion VI : `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="93f26-138">Vi insert mode: `<Enter>`</span></span>

### <a name="addline"></a><span data-ttu-id="93f26-139">AddLine</span><span class="sxs-lookup"><span data-stu-id="93f26-139">AddLine</span></span>

<span data-ttu-id="93f26-140">L’invite de continuation est affichée sur la ligne suivante et PSReadLine attend que les clés modifient l’entrée actuelle.</span><span class="sxs-lookup"><span data-stu-id="93f26-140">The continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span> <span data-ttu-id="93f26-141">Cela est utile pour entrer une entrée multiligne sous la forme d’une commande unique, même lorsqu’une seule ligne est complète en entrée.</span><span class="sxs-lookup"><span data-stu-id="93f26-141">This is useful to enter multi-line input as a single command even when a single line is complete input by itself.</span></span>

- <span data-ttu-id="93f26-142">Cmd `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="93f26-142">Cmd: `<Shift+Enter>`</span></span>
- <span data-ttu-id="93f26-143">Emacs- `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="93f26-143">Emacs: `<Shift+Enter>`</span></span>
- <span data-ttu-id="93f26-144">Mode d’insertion VI : `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="93f26-144">Vi insert mode: `<Shift+Enter>`</span></span>
- <span data-ttu-id="93f26-145">Mode de commande VI : `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="93f26-145">Vi command mode: `<Shift+Enter>`</span></span>

### <a name="backwarddeletechar"></a><span data-ttu-id="93f26-146">BackwardDeleteChar</span><span class="sxs-lookup"><span data-stu-id="93f26-146">BackwardDeleteChar</span></span>

<span data-ttu-id="93f26-147">Supprimez le caractère avant le curseur.</span><span class="sxs-lookup"><span data-stu-id="93f26-147">Delete the character before the cursor.</span></span>

- <span data-ttu-id="93f26-148">Cmd : `<Backspace>` , `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="93f26-148">Cmd: `<Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="93f26-149">Emacs : `<Backspace>` , `<Ctrl+Backspace>` , `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="93f26-149">Emacs: `<Backspace>`, `<Ctrl+Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="93f26-150">Mode d’insertion VI : `<Backspace>`</span><span class="sxs-lookup"><span data-stu-id="93f26-150">Vi insert mode: `<Backspace>`</span></span>
- <span data-ttu-id="93f26-151">Mode de commande VI : `<X>` , `<d,h>`</span><span class="sxs-lookup"><span data-stu-id="93f26-151">Vi command mode: `<X>`, `<d,h>`</span></span>

### <a name="backwarddeleteline"></a><span data-ttu-id="93f26-152">BackwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="93f26-152">BackwardDeleteLine</span></span>

<span data-ttu-id="93f26-153">Comme BackwardKillLine-supprime le texte du point jusqu’au début de la ligne, mais ne place pas le texte supprimé dans l’anneau d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="93f26-153">Like BackwardKillLine - deletes text from the point to the start of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="93f26-154">Cmd `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="93f26-154">Cmd: `<Ctrl+Home>`</span></span>
- <span data-ttu-id="93f26-155">Mode d’insertion VI : `<Ctrl+u>` , `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="93f26-155">Vi insert mode: `<Ctrl+u>`, `<Ctrl+Home>`</span></span>
- <span data-ttu-id="93f26-156">Mode de commande VI : `<Ctrl+u>` , `<Ctrl+Home>` , `<d,0>`</span><span class="sxs-lookup"><span data-stu-id="93f26-156">Vi command mode: `<Ctrl+u>`, `<Ctrl+Home>`, `<d,0>`</span></span>

### <a name="backwarddeleteword"></a><span data-ttu-id="93f26-157">BackwardDeleteWord</span><span class="sxs-lookup"><span data-stu-id="93f26-157">BackwardDeleteWord</span></span>

<span data-ttu-id="93f26-158">Supprime le mot précédent.</span><span class="sxs-lookup"><span data-stu-id="93f26-158">Deletes the previous word.</span></span>

- <span data-ttu-id="93f26-159">Mode de commande VI : `<Ctrl+w>` , `<d,b>`</span><span class="sxs-lookup"><span data-stu-id="93f26-159">Vi command mode: `<Ctrl+w>`, `<d,b>`</span></span>

### <a name="backwardkillline"></a><span data-ttu-id="93f26-160">BackwardKillLine</span><span class="sxs-lookup"><span data-stu-id="93f26-160">BackwardKillLine</span></span>

<span data-ttu-id="93f26-161">Effacez l’entrée à partir du début de l’entrée jusqu’au curseur.</span><span class="sxs-lookup"><span data-stu-id="93f26-161">Clear the input from the start of the input to the cursor.</span></span> <span data-ttu-id="93f26-162">Le texte effacé est placé dans le Kill-Ring.</span><span class="sxs-lookup"><span data-stu-id="93f26-162">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="93f26-163">Emacs- `<Ctrl+u>` , `<Ctrl+x,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="93f26-163">Emacs: `<Ctrl+u>`, `<Ctrl+x,Backspace>`</span></span>

### <a name="backwardkillword"></a><span data-ttu-id="93f26-164">BackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="93f26-164">BackwardKillWord</span></span>

<span data-ttu-id="93f26-165">Efface l’entrée du début du mot actuel jusqu’au curseur.</span><span class="sxs-lookup"><span data-stu-id="93f26-165">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="93f26-166">Si le curseur se trouve entre des mots, l’entrée est effacée du début du mot précédent au curseur.</span><span class="sxs-lookup"><span data-stu-id="93f26-166">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="93f26-167">Le texte effacé est placé dans le Kill-Ring.</span><span class="sxs-lookup"><span data-stu-id="93f26-167">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="93f26-168">Cmd `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="93f26-168">Cmd: `<Ctrl+Backspace>`</span></span>
- <span data-ttu-id="93f26-169">Emacs- `<Alt+Backspace>` , `<Escape,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="93f26-169">Emacs: `<Alt+Backspace>`, `<Escape,Backspace>`</span></span>
- <span data-ttu-id="93f26-170">Mode d’insertion VI : `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="93f26-170">Vi insert mode: `<Ctrl+Backspace>`</span></span>
- <span data-ttu-id="93f26-171">Mode de commande VI : `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="93f26-171">Vi command mode: `<Ctrl+Backspace>`</span></span>

### <a name="cancelline"></a><span data-ttu-id="93f26-172">CancelLine</span><span class="sxs-lookup"><span data-stu-id="93f26-172">CancelLine</span></span>

<span data-ttu-id="93f26-173">Annule l’entrée actuelle, en laissant l’entrée à l’écran, mais retourne à l’hôte afin que l’invite soit de nouveau évaluée.</span><span class="sxs-lookup"><span data-stu-id="93f26-173">Cancel the current input, leaving the input on the screen, but returns back to the host so the prompt is evaluated again.</span></span>

- <span data-ttu-id="93f26-174">Mode d’insertion VI : `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="93f26-174">Vi insert mode: `<Ctrl+c>`</span></span>
- <span data-ttu-id="93f26-175">Mode de commande VI : `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="93f26-175">Vi command mode: `<Ctrl+c>`</span></span>

### <a name="copy"></a><span data-ttu-id="93f26-176">Copier</span><span class="sxs-lookup"><span data-stu-id="93f26-176">Copy</span></span>

<span data-ttu-id="93f26-177">Copier la région sélectionnée dans le presse-papiers du système.</span><span class="sxs-lookup"><span data-stu-id="93f26-177">Copy selected region to the system clipboard.</span></span> <span data-ttu-id="93f26-178">Si aucune région n’est sélectionnée, copiez la ligne entière.</span><span class="sxs-lookup"><span data-stu-id="93f26-178">If no region is selected, copy the whole line.</span></span>

- <span data-ttu-id="93f26-179">Cmd `<Ctrl+C>`</span><span class="sxs-lookup"><span data-stu-id="93f26-179">Cmd: `<Ctrl+C>`</span></span>

### <a name="copyorcancelline"></a><span data-ttu-id="93f26-180">CopyOrCancelLine</span><span class="sxs-lookup"><span data-stu-id="93f26-180">CopyOrCancelLine</span></span>

<span data-ttu-id="93f26-181">Si le texte est sélectionné, copiez-le dans le presse-papiers, sinon, annulez la ligne.</span><span class="sxs-lookup"><span data-stu-id="93f26-181">If text is selected, copy to the clipboard, otherwise cancel the line.</span></span>

- <span data-ttu-id="93f26-182">Cmd `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="93f26-182">Cmd: `<Ctrl+c>`</span></span>
- <span data-ttu-id="93f26-183">Emacs- `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="93f26-183">Emacs: `<Ctrl+c>`</span></span>

### <a name="cut"></a><span data-ttu-id="93f26-184">Couper</span><span class="sxs-lookup"><span data-stu-id="93f26-184">Cut</span></span>

<span data-ttu-id="93f26-185">Supprimer la zone sélectionnée en plaçant le texte supprimé dans le presse-papiers du système.</span><span class="sxs-lookup"><span data-stu-id="93f26-185">Delete selected region placing deleted text in the system clipboard.</span></span>

- <span data-ttu-id="93f26-186">Cmd `<Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="93f26-186">Cmd: `<Ctrl+x>`</span></span>

### <a name="deletechar"></a><span data-ttu-id="93f26-187">DeleteChar</span><span class="sxs-lookup"><span data-stu-id="93f26-187">DeleteChar</span></span>

<span data-ttu-id="93f26-188">Supprimez le caractère sous le curseur.</span><span class="sxs-lookup"><span data-stu-id="93f26-188">Delete the character under the cursor.</span></span>

- <span data-ttu-id="93f26-189">Cmd `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="93f26-189">Cmd: `<Delete>`</span></span>
- <span data-ttu-id="93f26-190">Emacs- `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="93f26-190">Emacs: `<Delete>`</span></span>
- <span data-ttu-id="93f26-191">Mode d’insertion VI : `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="93f26-191">Vi insert mode: `<Delete>`</span></span>
- <span data-ttu-id="93f26-192">Mode de commande VI : `<Delete>` , `<x>` , `<d,l>` , `<d,Space>`</span><span class="sxs-lookup"><span data-stu-id="93f26-192">Vi command mode: `<Delete>`, `<x>`, `<d,l>`, `<d,Space>`</span></span>

### <a name="deletecharorexit"></a><span data-ttu-id="93f26-193">DeleteCharOrExit</span><span class="sxs-lookup"><span data-stu-id="93f26-193">DeleteCharOrExit</span></span>

<span data-ttu-id="93f26-194">Supprimez le caractère sous le curseur, ou si la ligne est vide, quittez le processus.</span><span class="sxs-lookup"><span data-stu-id="93f26-194">Delete the character under the cursor, or if the line is empty, exit the process.</span></span>

- <span data-ttu-id="93f26-195">Emacs- `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="93f26-195">Emacs: `<Ctrl+d>`</span></span>

### <a name="deleteendofword"></a><span data-ttu-id="93f26-196">DeleteEndOfWord</span><span class="sxs-lookup"><span data-stu-id="93f26-196">DeleteEndOfWord</span></span>

<span data-ttu-id="93f26-197">Supprimer à la fin du mot.</span><span class="sxs-lookup"><span data-stu-id="93f26-197">Delete to the end of the word.</span></span>

- <span data-ttu-id="93f26-198">Mode de commande VI : `<d,e>`</span><span class="sxs-lookup"><span data-stu-id="93f26-198">Vi command mode: `<d,e>`</span></span>

### <a name="deleteline"></a><span data-ttu-id="93f26-199">DeleteLine</span><span class="sxs-lookup"><span data-stu-id="93f26-199">DeleteLine</span></span>

<span data-ttu-id="93f26-200">Supprime la ligne active, en activant l’annulation.</span><span class="sxs-lookup"><span data-stu-id="93f26-200">Deletes the current line, enabling undo.</span></span>

- <span data-ttu-id="93f26-201">Mode de commande VI : `<d,d>`</span><span class="sxs-lookup"><span data-stu-id="93f26-201">Vi command mode: `<d,d>`</span></span>

### <a name="deletelinetofirstchar"></a><span data-ttu-id="93f26-202">DeleteLineToFirstChar</span><span class="sxs-lookup"><span data-stu-id="93f26-202">DeleteLineToFirstChar</span></span>

<span data-ttu-id="93f26-203">Supprime le texte du curseur jusqu’au premier caractère non vide de la ligne.</span><span class="sxs-lookup"><span data-stu-id="93f26-203">Deletes text from the cursor to the first non-blank character of the line.</span></span>

- <span data-ttu-id="93f26-204">Mode de commande VI : `<d,^>`</span><span class="sxs-lookup"><span data-stu-id="93f26-204">Vi command mode: `<d,^>`</span></span>

### <a name="deletetoend"></a><span data-ttu-id="93f26-205">DeleteToEnd</span><span class="sxs-lookup"><span data-stu-id="93f26-205">DeleteToEnd</span></span>

<span data-ttu-id="93f26-206">Supprimer à la fin de la ligne.</span><span class="sxs-lookup"><span data-stu-id="93f26-206">Delete to the end of the line.</span></span>

- <span data-ttu-id="93f26-207">Mode de commande VI : `<D>` , `<d,$>`</span><span class="sxs-lookup"><span data-stu-id="93f26-207">Vi command mode: `<D>`, `<d,$>`</span></span>

### <a name="deleteword"></a><span data-ttu-id="93f26-208">DeleteWord</span><span class="sxs-lookup"><span data-stu-id="93f26-208">DeleteWord</span></span>

<span data-ttu-id="93f26-209">Supprimer le mot suivant.</span><span class="sxs-lookup"><span data-stu-id="93f26-209">Delete the next word.</span></span>

- <span data-ttu-id="93f26-210">Mode de commande VI : `<d,w>`</span><span class="sxs-lookup"><span data-stu-id="93f26-210">Vi command mode: `<d,w>`</span></span>

### <a name="forwarddeleteline"></a><span data-ttu-id="93f26-211">ForwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="93f26-211">ForwardDeleteLine</span></span>

<span data-ttu-id="93f26-212">Comme ForwardKillLine-supprime le texte du point jusqu’à la fin de la ligne, mais ne place pas le texte supprimé dans l’anneau Kill.</span><span class="sxs-lookup"><span data-stu-id="93f26-212">Like ForwardKillLine - deletes text from the point to the end of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="93f26-213">Cmd `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="93f26-213">Cmd: `<Ctrl+End>`</span></span>
- <span data-ttu-id="93f26-214">Mode d’insertion VI : `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="93f26-214">Vi insert mode: `<Ctrl+End>`</span></span>
- <span data-ttu-id="93f26-215">Mode de commande VI : `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="93f26-215">Vi command mode: `<Ctrl+End>`</span></span>

### <a name="insertlineabove"></a><span data-ttu-id="93f26-216">InsertLineAbove</span><span class="sxs-lookup"><span data-stu-id="93f26-216">InsertLineAbove</span></span>

<span data-ttu-id="93f26-217">Une nouvelle ligne vide est créée au-dessus de la ligne active, quel que soit l’endroit où se trouve le curseur sur la ligne active.</span><span class="sxs-lookup"><span data-stu-id="93f26-217">A new empty line is created above the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="93f26-218">Le curseur se déplace au début de la nouvelle ligne.</span><span class="sxs-lookup"><span data-stu-id="93f26-218">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="93f26-219">Cmd `<Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="93f26-219">Cmd: `<Ctrl+Enter>`</span></span>

### <a name="insertlinebelow"></a><span data-ttu-id="93f26-220">InsertLineBelow</span><span class="sxs-lookup"><span data-stu-id="93f26-220">InsertLineBelow</span></span>

<span data-ttu-id="93f26-221">Une nouvelle ligne vide est créée sous la ligne active, quel que soit l’endroit où se trouve le curseur sur la ligne active.</span><span class="sxs-lookup"><span data-stu-id="93f26-221">A new empty line is created below the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="93f26-222">Le curseur se déplace au début de la nouvelle ligne.</span><span class="sxs-lookup"><span data-stu-id="93f26-222">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="93f26-223">Cmd `<Shift+Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="93f26-223">Cmd: `<Shift+Ctrl+Enter>`</span></span>

### <a name="invertcase"></a><span data-ttu-id="93f26-224">InvertCase</span><span class="sxs-lookup"><span data-stu-id="93f26-224">InvertCase</span></span>

<span data-ttu-id="93f26-225">Inverser la casse du caractère actuel et passer au suivant.</span><span class="sxs-lookup"><span data-stu-id="93f26-225">Invert the case of the current character and move to the next one.</span></span>

- <span data-ttu-id="93f26-226">Mode de commande VI : `<~>`</span><span class="sxs-lookup"><span data-stu-id="93f26-226">Vi command mode: `<~>`</span></span>

### <a name="killline"></a><span data-ttu-id="93f26-227">KillLine</span><span class="sxs-lookup"><span data-stu-id="93f26-227">KillLine</span></span>

<span data-ttu-id="93f26-228">Effacez l’entrée du curseur jusqu’à la fin de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="93f26-228">Clear the input from the cursor to the end of the input.</span></span> <span data-ttu-id="93f26-229">Le texte effacé est placé dans le Kill-Ring.</span><span class="sxs-lookup"><span data-stu-id="93f26-229">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="93f26-230">Emacs- `<Ctrl+k>`</span><span class="sxs-lookup"><span data-stu-id="93f26-230">Emacs: `<Ctrl+k>`</span></span>

### <a name="killregion"></a><span data-ttu-id="93f26-231">KillRegion</span><span class="sxs-lookup"><span data-stu-id="93f26-231">KillRegion</span></span>

<span data-ttu-id="93f26-232">Supprimer le texte situé entre le curseur et la marque.</span><span class="sxs-lookup"><span data-stu-id="93f26-232">Kill the text between the cursor and the mark.</span></span>

- <span data-ttu-id="93f26-233">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="93f26-233">Function is unbound.</span></span>

### <a name="killword"></a><span data-ttu-id="93f26-234">KillWord</span><span class="sxs-lookup"><span data-stu-id="93f26-234">KillWord</span></span>

<span data-ttu-id="93f26-235">Efface l’entrée du curseur jusqu’à la fin du mot actuel.</span><span class="sxs-lookup"><span data-stu-id="93f26-235">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="93f26-236">Si le curseur se trouve entre des mots, l’entrée est effacée du curseur jusqu’à la fin du mot suivant.</span><span class="sxs-lookup"><span data-stu-id="93f26-236">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="93f26-237">Le texte effacé est placé dans le Kill-Ring.</span><span class="sxs-lookup"><span data-stu-id="93f26-237">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="93f26-238">Cmd `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="93f26-238">Cmd: `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="93f26-239">Emacs- `<Alt+d>` , `<Escape,d>`</span><span class="sxs-lookup"><span data-stu-id="93f26-239">Emacs: `<Alt+d>`, `<Escape,d>`</span></span>
- <span data-ttu-id="93f26-240">Mode d’insertion VI : `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="93f26-240">Vi insert mode: `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="93f26-241">Mode de commande VI : `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="93f26-241">Vi command mode: `<Ctrl+Delete>`</span></span>

### <a name="paste"></a><span data-ttu-id="93f26-242">Coller</span><span class="sxs-lookup"><span data-stu-id="93f26-242">Paste</span></span>

<span data-ttu-id="93f26-243">Collez le texte à partir du presse-papiers du système.</span><span class="sxs-lookup"><span data-stu-id="93f26-243">Paste text from the system clipboard.</span></span>

- <span data-ttu-id="93f26-244">Cmd : `<Ctrl+v>` , `<Shift+Insert>`</span><span class="sxs-lookup"><span data-stu-id="93f26-244">Cmd: `<Ctrl+v>`, `<Shift+Insert>`</span></span>
- <span data-ttu-id="93f26-245">Mode d’insertion VI : `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="93f26-245">Vi insert mode: `<Ctrl+v>`</span></span>
- <span data-ttu-id="93f26-246">Mode de commande VI : `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="93f26-246">Vi command mode: `<Ctrl+v>`</span></span>

> [!IMPORTANT]
> <span data-ttu-id="93f26-247">Lors de l’utilisation de la fonction **Paste** , le contenu entier de la mémoire tampon du presse-papiers est collé dans la mémoire tampon d’entrée de PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="93f26-247">When using the **Paste** function, the entire contents of the clipboard buffer is pasted into the input buffer of PSReadLine.</span></span> <span data-ttu-id="93f26-248">La mémoire tampon d’entrée est ensuite transmise à l’analyseur PowerShell.</span><span class="sxs-lookup"><span data-stu-id="93f26-248">The input buffer is then passed to the PowerShell parser.</span></span> <span data-ttu-id="93f26-249">L’entrée collée à l’aide de la méthode de collage **avec le bouton droit** de la console de l’application de console est copiée dans la mémoire tampon d’entrée un caractère à la fois.</span><span class="sxs-lookup"><span data-stu-id="93f26-249">Input pasted using the console application's **right-click** paste method is copied to the input buffer one character at a time.</span></span> <span data-ttu-id="93f26-250">La mémoire tampon d’entrée est transmise à l’analyseur lorsqu’un caractère de saut de ligne est copié.</span><span class="sxs-lookup"><span data-stu-id="93f26-250">The input buffer is passed to the parser when a newline character is copied.</span></span> <span data-ttu-id="93f26-251">Par conséquent, l’entrée est analysée une ligne à la fois.</span><span class="sxs-lookup"><span data-stu-id="93f26-251">Therefore, the input is parsed one line at a time.</span></span> <span data-ttu-id="93f26-252">La différence entre les méthodes de collage entraîne un comportement d’exécution différent.</span><span class="sxs-lookup"><span data-stu-id="93f26-252">The difference between paste methods results in different execution behavior.</span></span>

### <a name="pasteafter"></a><span data-ttu-id="93f26-253">PasteAfter</span><span class="sxs-lookup"><span data-stu-id="93f26-253">PasteAfter</span></span>

<span data-ttu-id="93f26-254">Collez le presse-papiers après le curseur, en déplaçant le curseur à la fin du texte collé.</span><span class="sxs-lookup"><span data-stu-id="93f26-254">Paste the clipboard after the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="93f26-255">Mode de commande VI : `<p>`</span><span class="sxs-lookup"><span data-stu-id="93f26-255">Vi command mode: `<p>`</span></span>

### <a name="pastebefore"></a><span data-ttu-id="93f26-256">PasteBefore</span><span class="sxs-lookup"><span data-stu-id="93f26-256">PasteBefore</span></span>

<span data-ttu-id="93f26-257">Collez le presse-papiers avant le curseur, en déplaçant le curseur à la fin du texte collé.</span><span class="sxs-lookup"><span data-stu-id="93f26-257">Paste the clipboard before the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="93f26-258">Mode de commande VI : `<P>`</span><span class="sxs-lookup"><span data-stu-id="93f26-258">Vi command mode: `<P>`</span></span>

### <a name="prependandaccept"></a><span data-ttu-id="93f26-259">PrependAndAccept</span><span class="sxs-lookup"><span data-stu-id="93f26-259">PrependAndAccept</span></span>

<span data-ttu-id="93f26-260">Faites précéder un' # 'et acceptez la ligne.</span><span class="sxs-lookup"><span data-stu-id="93f26-260">Prepend a '#' and accept the line.</span></span>

- <span data-ttu-id="93f26-261">Mode de commande VI : `<#>`</span><span class="sxs-lookup"><span data-stu-id="93f26-261">Vi command mode: `<#>`</span></span>

### <a name="redo"></a><span data-ttu-id="93f26-262">Rétablir</span><span class="sxs-lookup"><span data-stu-id="93f26-262">Redo</span></span>

<span data-ttu-id="93f26-263">Annule une annulation.</span><span class="sxs-lookup"><span data-stu-id="93f26-263">Undo an undo.</span></span>

- <span data-ttu-id="93f26-264">Cmd `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="93f26-264">Cmd: `<Ctrl+y>`</span></span>
- <span data-ttu-id="93f26-265">Mode d’insertion VI : `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="93f26-265">Vi insert mode: `<Ctrl+y>`</span></span>
- <span data-ttu-id="93f26-266">Mode de commande VI : `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="93f26-266">Vi command mode: `<Ctrl+y>`</span></span>

### <a name="repeatlastcommand"></a><span data-ttu-id="93f26-267">RepeatLastCommand</span><span class="sxs-lookup"><span data-stu-id="93f26-267">RepeatLastCommand</span></span>

<span data-ttu-id="93f26-268">Répète la dernière modification de texte.</span><span class="sxs-lookup"><span data-stu-id="93f26-268">Repeat the last text modification.</span></span>

- <span data-ttu-id="93f26-269">Mode de commande VI : `<.>`</span><span class="sxs-lookup"><span data-stu-id="93f26-269">Vi command mode: `<.>`</span></span>

### <a name="revertline"></a><span data-ttu-id="93f26-270">RevertLine</span><span class="sxs-lookup"><span data-stu-id="93f26-270">RevertLine</span></span>

<span data-ttu-id="93f26-271">Rétablit toutes les entrées de l’entrée actuelle.</span><span class="sxs-lookup"><span data-stu-id="93f26-271">Reverts all of the input to the current input.</span></span>

- <span data-ttu-id="93f26-272">Cmd `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="93f26-272">Cmd: `<Escape>`</span></span>
- <span data-ttu-id="93f26-273">Emacs- `<Alt+r>` , `<Escape,r>`</span><span class="sxs-lookup"><span data-stu-id="93f26-273">Emacs: `<Alt+r>`, `<Escape,r>`</span></span>

### <a name="shellbackwardkillword"></a><span data-ttu-id="93f26-274">ShellBackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="93f26-274">ShellBackwardKillWord</span></span>

<span data-ttu-id="93f26-275">Efface l’entrée du début du mot actuel jusqu’au curseur.</span><span class="sxs-lookup"><span data-stu-id="93f26-275">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="93f26-276">Si le curseur se trouve entre des mots, l’entrée est effacée du début du mot précédent au curseur.</span><span class="sxs-lookup"><span data-stu-id="93f26-276">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="93f26-277">Le texte effacé est placé dans le Kill-Ring.</span><span class="sxs-lookup"><span data-stu-id="93f26-277">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="93f26-278">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="93f26-278">Function is unbound.</span></span>

### <a name="shellkillword"></a><span data-ttu-id="93f26-279">ShellKillWord</span><span class="sxs-lookup"><span data-stu-id="93f26-279">ShellKillWord</span></span>

<span data-ttu-id="93f26-280">Efface l’entrée du curseur jusqu’à la fin du mot actuel.</span><span class="sxs-lookup"><span data-stu-id="93f26-280">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="93f26-281">Si le curseur se trouve entre des mots, l’entrée est effacée du curseur jusqu’à la fin du mot suivant.</span><span class="sxs-lookup"><span data-stu-id="93f26-281">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="93f26-282">Le texte effacé est placé dans le Kill-Ring.</span><span class="sxs-lookup"><span data-stu-id="93f26-282">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="93f26-283">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="93f26-283">Function is unbound.</span></span>

### <a name="swapcharacters"></a><span data-ttu-id="93f26-284">SwapCharacters</span><span class="sxs-lookup"><span data-stu-id="93f26-284">SwapCharacters</span></span>

<span data-ttu-id="93f26-285">Permuter le caractère actuel et celui qui le précèdent.</span><span class="sxs-lookup"><span data-stu-id="93f26-285">Swap the current character and the one before it.</span></span>

- <span data-ttu-id="93f26-286">Emacs- `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="93f26-286">Emacs: `<Ctrl+t>`</span></span>
- <span data-ttu-id="93f26-287">Mode d’insertion VI : `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="93f26-287">Vi insert mode: `<Ctrl+t>`</span></span>
- <span data-ttu-id="93f26-288">Mode de commande VI : `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="93f26-288">Vi command mode: `<Ctrl+t>`</span></span>

### <a name="undo"></a><span data-ttu-id="93f26-289">Annuler</span><span class="sxs-lookup"><span data-stu-id="93f26-289">Undo</span></span>

<span data-ttu-id="93f26-290">Annuler une modification précédente.</span><span class="sxs-lookup"><span data-stu-id="93f26-290">Undo a previous edit.</span></span>

- <span data-ttu-id="93f26-291">Cmd `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="93f26-291">Cmd: `<Ctrl+z>`</span></span>
- <span data-ttu-id="93f26-292">Emacs- `<Ctrl+_>` , `<Ctrl+x,Ctrl+u>`</span><span class="sxs-lookup"><span data-stu-id="93f26-292">Emacs: `<Ctrl+_>`, `<Ctrl+x,Ctrl+u>`</span></span>
- <span data-ttu-id="93f26-293">Mode d’insertion VI : `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="93f26-293">Vi insert mode: `<Ctrl+z>`</span></span>
- <span data-ttu-id="93f26-294">Mode de commande VI : `<Ctrl+z>` , `<u>`</span><span class="sxs-lookup"><span data-stu-id="93f26-294">Vi command mode: `<Ctrl+z>`, `<u>`</span></span>

### <a name="undoall"></a><span data-ttu-id="93f26-295">UndoAll</span><span class="sxs-lookup"><span data-stu-id="93f26-295">UndoAll</span></span>

<span data-ttu-id="93f26-296">Annule toutes les modifications précédentes pour la ligne.</span><span class="sxs-lookup"><span data-stu-id="93f26-296">Undo all previous edits for line.</span></span>

- <span data-ttu-id="93f26-297">Mode de commande VI : `<U>`</span><span class="sxs-lookup"><span data-stu-id="93f26-297">Vi command mode: `<U>`</span></span>

### <a name="unixwordrubout"></a><span data-ttu-id="93f26-298">UnixWordRubout</span><span class="sxs-lookup"><span data-stu-id="93f26-298">UnixWordRubout</span></span>

<span data-ttu-id="93f26-299">Efface l’entrée du début du mot actuel jusqu’au curseur.</span><span class="sxs-lookup"><span data-stu-id="93f26-299">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="93f26-300">Si le curseur se trouve entre des mots, l’entrée est effacée du début du mot précédent au curseur.</span><span class="sxs-lookup"><span data-stu-id="93f26-300">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="93f26-301">Le texte effacé est placé dans le Kill-Ring.</span><span class="sxs-lookup"><span data-stu-id="93f26-301">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="93f26-302">Emacs- `<Ctrl+w>`</span><span class="sxs-lookup"><span data-stu-id="93f26-302">Emacs: `<Ctrl+w>`</span></span>

### <a name="validateandacceptline"></a><span data-ttu-id="93f26-303">ValidateAndAcceptLine</span><span class="sxs-lookup"><span data-stu-id="93f26-303">ValidateAndAcceptLine</span></span>

<span data-ttu-id="93f26-304">Tentative d’exécution de l’entrée en cours.</span><span class="sxs-lookup"><span data-stu-id="93f26-304">Attempt to execute the current input.</span></span> <span data-ttu-id="93f26-305">Si l’entrée actuelle est incomplète (par exemple, il manque une parenthèse fermante, un crochet ou un guillemet, l’invite de continuation est affichée sur la ligne suivante et PSReadLine attend que les clés modifient l’entrée actuelle.</span><span class="sxs-lookup"><span data-stu-id="93f26-305">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="93f26-306">Emacs- `<Ctrl+m>`</span><span class="sxs-lookup"><span data-stu-id="93f26-306">Emacs: `<Ctrl+m>`</span></span>

### <a name="viacceptline"></a><span data-ttu-id="93f26-307">ViAcceptLine</span><span class="sxs-lookup"><span data-stu-id="93f26-307">ViAcceptLine</span></span>

<span data-ttu-id="93f26-308">Acceptez la ligne et passez en mode insertion.</span><span class="sxs-lookup"><span data-stu-id="93f26-308">Accept the line and switch to Insert mode.</span></span>

- <span data-ttu-id="93f26-309">Mode de commande VI : `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="93f26-309">Vi command mode: `<Enter>`</span></span>

### <a name="viacceptlineorexit"></a><span data-ttu-id="93f26-310">ViAcceptLineOrExit</span><span class="sxs-lookup"><span data-stu-id="93f26-310">ViAcceptLineOrExit</span></span>

<span data-ttu-id="93f26-311">Comme DeleteCharOrExit en mode emacs, mais accepte la ligne au lieu de supprimer un caractère.</span><span class="sxs-lookup"><span data-stu-id="93f26-311">Like DeleteCharOrExit in Emacs mode, but accepts the line instead of deleting a character.</span></span>

- <span data-ttu-id="93f26-312">Mode d’insertion VI : `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="93f26-312">Vi insert mode: `<Ctrl+d>`</span></span>
- <span data-ttu-id="93f26-313">Mode de commande VI : `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="93f26-313">Vi command mode: `<Ctrl+d>`</span></span>

### <a name="viappendline"></a><span data-ttu-id="93f26-314">ViAppendLine</span><span class="sxs-lookup"><span data-stu-id="93f26-314">ViAppendLine</span></span>

<span data-ttu-id="93f26-315">Une nouvelle ligne est insérée au-dessous de la ligne active.</span><span class="sxs-lookup"><span data-stu-id="93f26-315">A new line is inserted below the current line.</span></span>

- <span data-ttu-id="93f26-316">Mode de commande VI : `<o>`</span><span class="sxs-lookup"><span data-stu-id="93f26-316">Vi command mode: `<o>`</span></span>

### <a name="vibackwarddeleteglob"></a><span data-ttu-id="93f26-317">ViBackwardDeleteGlob</span><span class="sxs-lookup"><span data-stu-id="93f26-317">ViBackwardDeleteGlob</span></span>

<span data-ttu-id="93f26-318">Supprime le mot précédent, en utilisant uniquement un espace blanc comme délimiteur de mot.</span><span class="sxs-lookup"><span data-stu-id="93f26-318">Deletes the previous word, using only white space as the word delimiter.</span></span>

- <span data-ttu-id="93f26-319">Mode de commande VI : `<d,B>`</span><span class="sxs-lookup"><span data-stu-id="93f26-319">Vi command mode: `<d,B>`</span></span>

### <a name="vibackwardglob"></a><span data-ttu-id="93f26-320">ViBackwardGlob</span><span class="sxs-lookup"><span data-stu-id="93f26-320">ViBackwardGlob</span></span>

<span data-ttu-id="93f26-321">Déplace le curseur au début du mot précédent, en utilisant uniquement des espaces blancs comme délimiteurs.</span><span class="sxs-lookup"><span data-stu-id="93f26-321">Moves the cursor back to the beginning of the previous word, using only white space as delimiters.</span></span>

- <span data-ttu-id="93f26-322">Mode de commande VI : `<B>`</span><span class="sxs-lookup"><span data-stu-id="93f26-322">Vi command mode: `<B>`</span></span>

### <a name="videletebrace"></a><span data-ttu-id="93f26-323">ViDeleteBrace</span><span class="sxs-lookup"><span data-stu-id="93f26-323">ViDeleteBrace</span></span>

<span data-ttu-id="93f26-324">Recherchez l’accolade correspondante, la parenthèse ou le crochet, et supprimez tout le contenu dans, y compris l’accolade.</span><span class="sxs-lookup"><span data-stu-id="93f26-324">Find the matching brace, parenthesis, or square bracket and delete all contents within, including the brace.</span></span>

- <span data-ttu-id="93f26-325">Mode de commande VI : `<d,%>`</span><span class="sxs-lookup"><span data-stu-id="93f26-325">Vi command mode: `<d,%>`</span></span>

### <a name="videleteendofglob"></a><span data-ttu-id="93f26-326">ViDeleteEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="93f26-326">ViDeleteEndOfGlob</span></span>

<span data-ttu-id="93f26-327">Supprimer à la fin du mot.</span><span class="sxs-lookup"><span data-stu-id="93f26-327">Delete to the end of the word.</span></span>

- <span data-ttu-id="93f26-328">Mode de commande VI : `<d,E>`</span><span class="sxs-lookup"><span data-stu-id="93f26-328">Vi command mode: `<d,E>`</span></span>

### <a name="videleteglob"></a><span data-ttu-id="93f26-329">ViDeleteGlob</span><span class="sxs-lookup"><span data-stu-id="93f26-329">ViDeleteGlob</span></span>

<span data-ttu-id="93f26-330">Supprime la glob suivante (mot blanc délimité par des espaces).</span><span class="sxs-lookup"><span data-stu-id="93f26-330">Delete the next glob (white space delimited word).</span></span>

- <span data-ttu-id="93f26-331">Mode de commande VI : `<d,W>`</span><span class="sxs-lookup"><span data-stu-id="93f26-331">Vi command mode: `<d,W>`</span></span>

### <a name="videletetobeforechar"></a><span data-ttu-id="93f26-332">ViDeleteToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="93f26-332">ViDeleteToBeforeChar</span></span>

<span data-ttu-id="93f26-333">Supprime jusqu’au caractère donné.</span><span class="sxs-lookup"><span data-stu-id="93f26-333">Deletes until given character.</span></span>

- <span data-ttu-id="93f26-334">Mode de commande VI : `<d,t>`</span><span class="sxs-lookup"><span data-stu-id="93f26-334">Vi command mode: `<d,t>`</span></span>

### <a name="videletetobeforecharbackward"></a><span data-ttu-id="93f26-335">ViDeleteToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="93f26-335">ViDeleteToBeforeCharBackward</span></span>

<span data-ttu-id="93f26-336">Supprime jusqu’au caractère donné.</span><span class="sxs-lookup"><span data-stu-id="93f26-336">Deletes until given character.</span></span>

- <span data-ttu-id="93f26-337">Mode de commande VI : `<d,T>`</span><span class="sxs-lookup"><span data-stu-id="93f26-337">Vi command mode: `<d,T>`</span></span>

### <a name="videletetochar"></a><span data-ttu-id="93f26-338">ViDeleteToChar</span><span class="sxs-lookup"><span data-stu-id="93f26-338">ViDeleteToChar</span></span>

<span data-ttu-id="93f26-339">Supprime jusqu’au caractère donné.</span><span class="sxs-lookup"><span data-stu-id="93f26-339">Deletes until given character.</span></span>

- <span data-ttu-id="93f26-340">Mode de commande VI : `<d,f>`</span><span class="sxs-lookup"><span data-stu-id="93f26-340">Vi command mode: `<d,f>`</span></span>

### <a name="videletetocharbackward"></a><span data-ttu-id="93f26-341">ViDeleteToCharBackward</span><span class="sxs-lookup"><span data-stu-id="93f26-341">ViDeleteToCharBackward</span></span>

<span data-ttu-id="93f26-342">Supprime vers l’arrière jusqu’au caractère donné.</span><span class="sxs-lookup"><span data-stu-id="93f26-342">Deletes backwards until given character.</span></span>

- <span data-ttu-id="93f26-343">Mode de commande VI : `<d,F>`</span><span class="sxs-lookup"><span data-stu-id="93f26-343">Vi command mode: `<d,F>`</span></span>

### <a name="viinsertatbegining"></a><span data-ttu-id="93f26-344">ViInsertAtBegining</span><span class="sxs-lookup"><span data-stu-id="93f26-344">ViInsertAtBegining</span></span>

<span data-ttu-id="93f26-345">Basculez en mode insertion et positionnez le curseur au début de la ligne.</span><span class="sxs-lookup"><span data-stu-id="93f26-345">Switch to Insert mode and position the cursor at the beginning of the line.</span></span>

- <span data-ttu-id="93f26-346">Mode de commande VI : `<I>`</span><span class="sxs-lookup"><span data-stu-id="93f26-346">Vi command mode: `<I>`</span></span>

### <a name="viinsertatend"></a><span data-ttu-id="93f26-347">ViInsertAtEnd</span><span class="sxs-lookup"><span data-stu-id="93f26-347">ViInsertAtEnd</span></span>

<span data-ttu-id="93f26-348">Basculez en mode insertion et positionnez le curseur à la fin de la ligne.</span><span class="sxs-lookup"><span data-stu-id="93f26-348">Switch to Insert mode and position the cursor at the end of the line.</span></span>

- <span data-ttu-id="93f26-349">Mode de commande VI : `<A>`</span><span class="sxs-lookup"><span data-stu-id="93f26-349">Vi command mode: `<A>`</span></span>

### <a name="viinsertline"></a><span data-ttu-id="93f26-350">ViInsertLine</span><span class="sxs-lookup"><span data-stu-id="93f26-350">ViInsertLine</span></span>

<span data-ttu-id="93f26-351">Une nouvelle ligne est insérée au-dessus de la ligne active.</span><span class="sxs-lookup"><span data-stu-id="93f26-351">A new line is inserted above the current line.</span></span>

- <span data-ttu-id="93f26-352">Mode de commande VI : `<O>`</span><span class="sxs-lookup"><span data-stu-id="93f26-352">Vi command mode: `<O>`</span></span>

### <a name="viinsertwithappend"></a><span data-ttu-id="93f26-353">ViInsertWithAppend</span><span class="sxs-lookup"><span data-stu-id="93f26-353">ViInsertWithAppend</span></span>

<span data-ttu-id="93f26-354">Ajouter à partir de la position de la ligne active.</span><span class="sxs-lookup"><span data-stu-id="93f26-354">Append from the current line position.</span></span>

- <span data-ttu-id="93f26-355">Mode de commande VI : `<a>`</span><span class="sxs-lookup"><span data-stu-id="93f26-355">Vi command mode: `<a>`</span></span>

### <a name="viinsertwithdelete"></a><span data-ttu-id="93f26-356">ViInsertWithDelete</span><span class="sxs-lookup"><span data-stu-id="93f26-356">ViInsertWithDelete</span></span>

<span data-ttu-id="93f26-357">Supprimez le caractère actuel et basculez en mode insertion.</span><span class="sxs-lookup"><span data-stu-id="93f26-357">Delete the current character and switch to Insert mode.</span></span>

- <span data-ttu-id="93f26-358">Mode de commande VI : `<s>`</span><span class="sxs-lookup"><span data-stu-id="93f26-358">Vi command mode: `<s>`</span></span>

### <a name="vijoinlines"></a><span data-ttu-id="93f26-359">ViJoinLines</span><span class="sxs-lookup"><span data-stu-id="93f26-359">ViJoinLines</span></span>

<span data-ttu-id="93f26-360">Joint la ligne active et la ligne suivante.</span><span class="sxs-lookup"><span data-stu-id="93f26-360">Joins the current line and the next line.</span></span>

- <span data-ttu-id="93f26-361">Mode de commande VI : `<J>`</span><span class="sxs-lookup"><span data-stu-id="93f26-361">Vi command mode: `<J>`</span></span>

### <a name="vireplaceline"></a><span data-ttu-id="93f26-362">ViReplaceLine</span><span class="sxs-lookup"><span data-stu-id="93f26-362">ViReplaceLine</span></span>

<span data-ttu-id="93f26-363">Effacez l’intégralité de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="93f26-363">Erase the entire command line.</span></span>

- <span data-ttu-id="93f26-364">Mode de commande VI : `<S>` , `<c,c>`</span><span class="sxs-lookup"><span data-stu-id="93f26-364">Vi command mode: `<S>`, `<c,c>`</span></span>

### <a name="vireplacetobeforechar"></a><span data-ttu-id="93f26-365">ViReplaceToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="93f26-365">ViReplaceToBeforeChar</span></span>

<span data-ttu-id="93f26-366">Remplace jusqu’au caractère donné.</span><span class="sxs-lookup"><span data-stu-id="93f26-366">Replaces until given character.</span></span>

- <span data-ttu-id="93f26-367">Mode de commande VI : `<c,t>`</span><span class="sxs-lookup"><span data-stu-id="93f26-367">Vi command mode: `<c,t>`</span></span>

### <a name="vireplacetobeforecharbackward"></a><span data-ttu-id="93f26-368">ViReplaceToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="93f26-368">ViReplaceToBeforeCharBackward</span></span>

<span data-ttu-id="93f26-369">Remplace jusqu’au caractère donné.</span><span class="sxs-lookup"><span data-stu-id="93f26-369">Replaces until given character.</span></span>

- <span data-ttu-id="93f26-370">Mode de commande VI : `<c,T>`</span><span class="sxs-lookup"><span data-stu-id="93f26-370">Vi command mode: `<c,T>`</span></span>

### <a name="vireplacetochar"></a><span data-ttu-id="93f26-371">ViReplaceToChar</span><span class="sxs-lookup"><span data-stu-id="93f26-371">ViReplaceToChar</span></span>

<span data-ttu-id="93f26-372">Supprime jusqu’au caractère donné.</span><span class="sxs-lookup"><span data-stu-id="93f26-372">Deletes until given character.</span></span>

- <span data-ttu-id="93f26-373">Mode de commande VI : `<c,f>`</span><span class="sxs-lookup"><span data-stu-id="93f26-373">Vi command mode: `<c,f>`</span></span>

### <a name="vireplacetocharbackward"></a><span data-ttu-id="93f26-374">ViReplaceToCharBackward</span><span class="sxs-lookup"><span data-stu-id="93f26-374">ViReplaceToCharBackward</span></span>

<span data-ttu-id="93f26-375">Remplace jusqu’au caractère donné.</span><span class="sxs-lookup"><span data-stu-id="93f26-375">Replaces until given character.</span></span>

- <span data-ttu-id="93f26-376">Mode de commande VI : `<c,F>`</span><span class="sxs-lookup"><span data-stu-id="93f26-376">Vi command mode: `<c,F>`</span></span>

### <a name="viyankbeginningofline"></a><span data-ttu-id="93f26-377">ViYankBeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="93f26-377">ViYankBeginningOfLine</span></span>

<span data-ttu-id="93f26-378">Yank entre le début de la mémoire tampon et le curseur.</span><span class="sxs-lookup"><span data-stu-id="93f26-378">Yank from the beginning of the buffer to the cursor.</span></span>

- <span data-ttu-id="93f26-379">Mode de commande VI : `<y,0>`</span><span class="sxs-lookup"><span data-stu-id="93f26-379">Vi command mode: `<y,0>`</span></span>

### <a name="viyankendofglob"></a><span data-ttu-id="93f26-380">ViYankEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="93f26-380">ViYankEndOfGlob</span></span>

<span data-ttu-id="93f26-381">Yank du curseur jusqu’à la fin du ou des mots.</span><span class="sxs-lookup"><span data-stu-id="93f26-381">Yank from the cursor to the end of the WORD(s).</span></span>

- <span data-ttu-id="93f26-382">Mode de commande VI : `<y,E>`</span><span class="sxs-lookup"><span data-stu-id="93f26-382">Vi command mode: `<y,E>`</span></span>

### <a name="viyankendofword"></a><span data-ttu-id="93f26-383">ViYankEndOfWord</span><span class="sxs-lookup"><span data-stu-id="93f26-383">ViYankEndOfWord</span></span>

<span data-ttu-id="93f26-384">Yank du curseur jusqu’à la fin du ou des mots.</span><span class="sxs-lookup"><span data-stu-id="93f26-384">Yank from the cursor to the end of the word(s).</span></span>

- <span data-ttu-id="93f26-385">Mode de commande VI : `<y,e>`</span><span class="sxs-lookup"><span data-stu-id="93f26-385">Vi command mode: `<y,e>`</span></span>

### <a name="viyankleft"></a><span data-ttu-id="93f26-386">ViYankLeft</span><span class="sxs-lookup"><span data-stu-id="93f26-386">ViYankLeft</span></span>

<span data-ttu-id="93f26-387">Yank caractère (s) à gauche du curseur.</span><span class="sxs-lookup"><span data-stu-id="93f26-387">Yank character(s) to the left of the cursor.</span></span>

- <span data-ttu-id="93f26-388">Mode de commande VI : `<y,h>`</span><span class="sxs-lookup"><span data-stu-id="93f26-388">Vi command mode: `<y,h>`</span></span>

### <a name="viyankline"></a><span data-ttu-id="93f26-389">ViYankLine</span><span class="sxs-lookup"><span data-stu-id="93f26-389">ViYankLine</span></span>

<span data-ttu-id="93f26-390">Yank la mémoire tampon entière.</span><span class="sxs-lookup"><span data-stu-id="93f26-390">Yank the entire buffer.</span></span>

- <span data-ttu-id="93f26-391">Mode de commande VI : `<y,y>`</span><span class="sxs-lookup"><span data-stu-id="93f26-391">Vi command mode: `<y,y>`</span></span>

### <a name="viyanknextglob"></a><span data-ttu-id="93f26-392">ViYankNextGlob</span><span class="sxs-lookup"><span data-stu-id="93f26-392">ViYankNextGlob</span></span>

<span data-ttu-id="93f26-393">Yank à partir d’un curseur jusqu’au début du ou des mots suivants.</span><span class="sxs-lookup"><span data-stu-id="93f26-393">Yank from cursor to the start of the next WORD(s).</span></span>

- <span data-ttu-id="93f26-394">Mode de commande VI : `<y,W>`</span><span class="sxs-lookup"><span data-stu-id="93f26-394">Vi command mode: `<y,W>`</span></span>

### <a name="viyanknextword"></a><span data-ttu-id="93f26-395">ViYankNextWord</span><span class="sxs-lookup"><span data-stu-id="93f26-395">ViYankNextWord</span></span>

<span data-ttu-id="93f26-396">Yank le ou les mots après le curseur.</span><span class="sxs-lookup"><span data-stu-id="93f26-396">Yank the word(s) after the cursor.</span></span>

- <span data-ttu-id="93f26-397">Mode de commande VI : `<y,w>`</span><span class="sxs-lookup"><span data-stu-id="93f26-397">Vi command mode: `<y,w>`</span></span>

### <a name="viyankpercent"></a><span data-ttu-id="93f26-398">ViYankPercent</span><span class="sxs-lookup"><span data-stu-id="93f26-398">ViYankPercent</span></span>

<span data-ttu-id="93f26-399">Yank à/à partir de l’accolade correspondante.</span><span class="sxs-lookup"><span data-stu-id="93f26-399">Yank to/from matching brace.</span></span>

- <span data-ttu-id="93f26-400">Mode de commande VI : `<y,%>`</span><span class="sxs-lookup"><span data-stu-id="93f26-400">Vi command mode: `<y,%>`</span></span>

### <a name="viyankpreviousglob"></a><span data-ttu-id="93f26-401">ViYankPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="93f26-401">ViYankPreviousGlob</span></span>

<span data-ttu-id="93f26-402">Yank entre le début du ou des mots et le curseur.</span><span class="sxs-lookup"><span data-stu-id="93f26-402">Yank from beginning of the WORD(s) to cursor.</span></span>

- <span data-ttu-id="93f26-403">Mode de commande VI : `<y,B>`</span><span class="sxs-lookup"><span data-stu-id="93f26-403">Vi command mode: `<y,B>`</span></span>

### <a name="viyankpreviousword"></a><span data-ttu-id="93f26-404">ViYankPreviousWord</span><span class="sxs-lookup"><span data-stu-id="93f26-404">ViYankPreviousWord</span></span>

<span data-ttu-id="93f26-405">Yank le ou les mots avant le curseur.</span><span class="sxs-lookup"><span data-stu-id="93f26-405">Yank the word(s) before the cursor.</span></span>

- <span data-ttu-id="93f26-406">Mode de commande VI : `<y,b>`</span><span class="sxs-lookup"><span data-stu-id="93f26-406">Vi command mode: `<y,b>`</span></span>

### <a name="viyankright"></a><span data-ttu-id="93f26-407">ViYankRight</span><span class="sxs-lookup"><span data-stu-id="93f26-407">ViYankRight</span></span>

<span data-ttu-id="93f26-408">Yank caractère (s) situé sous et à droite du curseur.</span><span class="sxs-lookup"><span data-stu-id="93f26-408">Yank character(s) under and to the right of the cursor.</span></span>

- <span data-ttu-id="93f26-409">Mode de commande VI : `<y,l>` , `<y,Space>`</span><span class="sxs-lookup"><span data-stu-id="93f26-409">Vi command mode: `<y,l>`, `<y,Space>`</span></span>

### <a name="viyanktoendofline"></a><span data-ttu-id="93f26-410">ViYankToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="93f26-410">ViYankToEndOfLine</span></span>

<span data-ttu-id="93f26-411">Yank du curseur jusqu’à la fin de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="93f26-411">Yank from the cursor to the end of the buffer.</span></span>

- <span data-ttu-id="93f26-412">Mode de commande VI : `<y,$>`</span><span class="sxs-lookup"><span data-stu-id="93f26-412">Vi command mode: `<y,$>`</span></span>

### <a name="viyanktofirstchar"></a><span data-ttu-id="93f26-413">ViYankToFirstChar</span><span class="sxs-lookup"><span data-stu-id="93f26-413">ViYankToFirstChar</span></span>

<span data-ttu-id="93f26-414">Yank du premier caractère autre qu’un espace blanc au curseur.</span><span class="sxs-lookup"><span data-stu-id="93f26-414">Yank from the first non-whitespace character to the cursor.</span></span>

- <span data-ttu-id="93f26-415">Mode de commande VI : `<y,^>`</span><span class="sxs-lookup"><span data-stu-id="93f26-415">Vi command mode: `<y,^>`</span></span>

### <a name="yank"></a><span data-ttu-id="93f26-416">Yank</span><span class="sxs-lookup"><span data-stu-id="93f26-416">Yank</span></span>

<span data-ttu-id="93f26-417">Ajoutez le texte le plus récemment supprimé à l’entrée.</span><span class="sxs-lookup"><span data-stu-id="93f26-417">Add the most recently killed text to the input.</span></span>

- <span data-ttu-id="93f26-418">Emacs- `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="93f26-418">Emacs: `<Ctrl+y>`</span></span>

### <a name="yanklastarg"></a><span data-ttu-id="93f26-419">YankLastArg</span><span class="sxs-lookup"><span data-stu-id="93f26-419">YankLastArg</span></span>

<span data-ttu-id="93f26-420">Yank le dernier argument de la ligne d’historique précédente.</span><span class="sxs-lookup"><span data-stu-id="93f26-420">Yank the last argument from the previous history line.</span></span> <span data-ttu-id="93f26-421">Avec un argument, la première fois qu’il est appelé, se comporte comme YankNthArg.</span><span class="sxs-lookup"><span data-stu-id="93f26-421">With an argument, the first time it is invoked, behaves just like YankNthArg.</span></span> <span data-ttu-id="93f26-422">Si elle est appelée plusieurs fois, elle itère au sein de l’historique et ARG définit la direction (négatif inverse la direction).</span><span class="sxs-lookup"><span data-stu-id="93f26-422">If invoked multiple times, instead it iterates through history and arg sets the direction (negative reverses the direction.)</span></span>

- <span data-ttu-id="93f26-423">Cmd `<Alt+.>`</span><span class="sxs-lookup"><span data-stu-id="93f26-423">Cmd: `<Alt+.>`</span></span>
- <span data-ttu-id="93f26-424">Emacs : `<Alt+.>` , `<Alt+_>` , `<Escape,.>` , `<Escape,_>`</span><span class="sxs-lookup"><span data-stu-id="93f26-424">Emacs: `<Alt+.>`, `<Alt+_>`, `<Escape,.>`, `<Escape,_>`</span></span>

### <a name="yankntharg"></a><span data-ttu-id="93f26-425">YankNthArg</span><span class="sxs-lookup"><span data-stu-id="93f26-425">YankNthArg</span></span>

<span data-ttu-id="93f26-426">Yank le premier argument (après la commande) à partir de la ligne précédente de l’historique.</span><span class="sxs-lookup"><span data-stu-id="93f26-426">Yank the first argument (after the command) from the previous history line.</span></span>
<span data-ttu-id="93f26-427">Avec un argument, Yank le nième argument (à partir de 0), si l’argument est négatif, commencez par le dernier argument.</span><span class="sxs-lookup"><span data-stu-id="93f26-427">With an argument, yank the nth argument (starting from 0), if the argument is negative, start from the last argument.</span></span>

- <span data-ttu-id="93f26-428">Emacs- `<Ctrl+Alt+y>` , `<Escape,Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="93f26-428">Emacs: `<Ctrl+Alt+y>`, `<Escape,Ctrl+y>`</span></span>

### <a name="yankpop"></a><span data-ttu-id="93f26-429">YankPop</span><span class="sxs-lookup"><span data-stu-id="93f26-429">YankPop</span></span>

<span data-ttu-id="93f26-430">Si l’opération précédente était Yank ou YankPop, remplacez le texte précédemment extrait par le texte supprimé suivant de l’instruction KILL-Ring.</span><span class="sxs-lookup"><span data-stu-id="93f26-430">If the previous operation was Yank or YankPop, replace the previously yanked text with the next killed text from the kill-ring.</span></span>

- <span data-ttu-id="93f26-431">Emacs- `<Alt+y>` , `<Escape,y>`</span><span class="sxs-lookup"><span data-stu-id="93f26-431">Emacs: `<Alt+y>`, `<Escape,y>`</span></span>

## <a name="cursor-movement-functions"></a><span data-ttu-id="93f26-432">Fonctions de déplacement de curseur</span><span class="sxs-lookup"><span data-stu-id="93f26-432">Cursor movement functions</span></span>

### <a name="backwardchar"></a><span data-ttu-id="93f26-433">BackwardChar</span><span class="sxs-lookup"><span data-stu-id="93f26-433">BackwardChar</span></span>

<span data-ttu-id="93f26-434">Déplacer le curseur d’un caractère vers la gauche.</span><span class="sxs-lookup"><span data-stu-id="93f26-434">Move the cursor one character to the left.</span></span> <span data-ttu-id="93f26-435">Cela peut déplacer le curseur vers la ligne précédente de l’entrée multiligne.</span><span class="sxs-lookup"><span data-stu-id="93f26-435">This may move the cursor to the previous line of multi-line input.</span></span>

- <span data-ttu-id="93f26-436">Cmd `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="93f26-436">Cmd: `<LeftArrow>`</span></span>
- <span data-ttu-id="93f26-437">Emacs- `<LeftArrow>` , `<Ctrl+b>`</span><span class="sxs-lookup"><span data-stu-id="93f26-437">Emacs: `<LeftArrow>`, `<Ctrl+b>`</span></span>
- <span data-ttu-id="93f26-438">Mode d’insertion VI : `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="93f26-438">Vi insert mode: `<LeftArrow>`</span></span>
- <span data-ttu-id="93f26-439">Mode de commande VI : `<LeftArrow>` , `<Backspace>` , `<h>`</span><span class="sxs-lookup"><span data-stu-id="93f26-439">Vi command mode: `<LeftArrow>`, `<Backspace>`, `<h>`</span></span>

### <a name="backwardword"></a><span data-ttu-id="93f26-440">BackwardWord</span><span class="sxs-lookup"><span data-stu-id="93f26-440">BackwardWord</span></span>

<span data-ttu-id="93f26-441">Ramener le curseur au début du mot actuel, ou si entre les mots, le début du mot précédent.</span><span class="sxs-lookup"><span data-stu-id="93f26-441">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="93f26-442">Les limites de mots sont définies par un jeu de caractères configurable.</span><span class="sxs-lookup"><span data-stu-id="93f26-442">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="93f26-443">Cmd `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="93f26-443">Cmd: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="93f26-444">Emacs- `<Alt+b>` , `<Escape,b>`</span><span class="sxs-lookup"><span data-stu-id="93f26-444">Emacs: `<Alt+b>`, `<Escape,b>`</span></span>
- <span data-ttu-id="93f26-445">Mode d’insertion VI : `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="93f26-445">Vi insert mode: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="93f26-446">Mode de commande VI : `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="93f26-446">Vi command mode: `<Ctrl+LeftArrow>`</span></span>

### <a name="beginningofline"></a><span data-ttu-id="93f26-447">BeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="93f26-447">BeginningOfLine</span></span>

<span data-ttu-id="93f26-448">Si l’entrée comporte plusieurs lignes, se déplacer au début de la ligne active ou, le cas échéant, au début de la ligne, se déplacer au début de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="93f26-448">If the input has multiple lines, move to the start of the current line, or if already at the start of the line, move to the start of the input.</span></span> <span data-ttu-id="93f26-449">Si l’entrée comporte une seule ligne, accédez au début de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="93f26-449">If the input has a single line, move to the start of the input.</span></span>

- <span data-ttu-id="93f26-450">Cmd `<Home>`</span><span class="sxs-lookup"><span data-stu-id="93f26-450">Cmd: `<Home>`</span></span>
- <span data-ttu-id="93f26-451">Emacs- `<Home>` , `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="93f26-451">Emacs: `<Home>`, `<Ctrl+a>`</span></span>
- <span data-ttu-id="93f26-452">Mode d’insertion VI : `<Home>`</span><span class="sxs-lookup"><span data-stu-id="93f26-452">Vi insert mode: `<Home>`</span></span>
- <span data-ttu-id="93f26-453">Mode de commande VI : `<Home>`</span><span class="sxs-lookup"><span data-stu-id="93f26-453">Vi command mode: `<Home>`</span></span>

### <a name="endofline"></a><span data-ttu-id="93f26-454">EndOfLine</span><span class="sxs-lookup"><span data-stu-id="93f26-454">EndOfLine</span></span>

<span data-ttu-id="93f26-455">Si l’entrée comporte plusieurs lignes, passez à la fin de la ligne active ou, si elle se trouve déjà à la fin de la ligne, à la fin de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="93f26-455">If the input has multiple lines, move to the end of the current line, or if already at the end of the line, move to the end of the input.</span></span> <span data-ttu-id="93f26-456">Si l’entrée comporte une seule ligne, passez à la fin de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="93f26-456">If the input has a single line, move to the end of the input.</span></span>

- <span data-ttu-id="93f26-457">Cmd `<End>`</span><span class="sxs-lookup"><span data-stu-id="93f26-457">Cmd: `<End>`</span></span>
- <span data-ttu-id="93f26-458">Emacs- `<End>` , `<Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="93f26-458">Emacs: `<End>`, `<Ctrl+e>`</span></span>
- <span data-ttu-id="93f26-459">Mode d’insertion VI : `<End>`</span><span class="sxs-lookup"><span data-stu-id="93f26-459">Vi insert mode: `<End>`</span></span>

### <a name="forwardchar"></a><span data-ttu-id="93f26-460">ForwardChar</span><span class="sxs-lookup"><span data-stu-id="93f26-460">ForwardChar</span></span>

<span data-ttu-id="93f26-461">Déplacer le curseur d’un caractère vers la droite.</span><span class="sxs-lookup"><span data-stu-id="93f26-461">Move the cursor one character to the right.</span></span> <span data-ttu-id="93f26-462">Cela peut déplacer le curseur à la ligne suivante de l’entrée multiligne.</span><span class="sxs-lookup"><span data-stu-id="93f26-462">This may move the cursor to the next line of multi-line input.</span></span>

- <span data-ttu-id="93f26-463">Cmd `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="93f26-463">Cmd: `<RightArrow>`</span></span>
- <span data-ttu-id="93f26-464">Emacs- `<RightArrow>` , `<Ctrl+f>`</span><span class="sxs-lookup"><span data-stu-id="93f26-464">Emacs: `<RightArrow>`, `<Ctrl+f>`</span></span>
- <span data-ttu-id="93f26-465">Mode d’insertion VI : `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="93f26-465">Vi insert mode: `<RightArrow>`</span></span>
- <span data-ttu-id="93f26-466">Mode de commande VI : `<RightArrow>` , `<Space>` , `<l>`</span><span class="sxs-lookup"><span data-stu-id="93f26-466">Vi command mode: `<RightArrow>`, `<Space>`, `<l>`</span></span>

### <a name="forwardword"></a><span data-ttu-id="93f26-467">ForwardWord</span><span class="sxs-lookup"><span data-stu-id="93f26-467">ForwardWord</span></span>

<span data-ttu-id="93f26-468">Déplacer le curseur vers l’avant jusqu’à la fin du mot actuel, ou si entre les mots, à la fin du mot suivant.</span><span class="sxs-lookup"><span data-stu-id="93f26-468">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="93f26-469">Les limites de mots sont définies par un jeu de caractères configurable.</span><span class="sxs-lookup"><span data-stu-id="93f26-469">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="93f26-470">Emacs- `<Alt+f>` , `<Escape,f>`</span><span class="sxs-lookup"><span data-stu-id="93f26-470">Emacs: `<Alt+f>`, `<Escape,f>`</span></span>

### <a name="gotobrace"></a><span data-ttu-id="93f26-471">GotoBrace</span><span class="sxs-lookup"><span data-stu-id="93f26-471">GotoBrace</span></span>

<span data-ttu-id="93f26-472">Atteindre l’accolade correspondante, les parenthèses ou les crochets.</span><span class="sxs-lookup"><span data-stu-id="93f26-472">Go to the matching brace, parenthesis, or square bracket.</span></span>

- <span data-ttu-id="93f26-473">Cmd `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="93f26-473">Cmd: `<Ctrl+]>`</span></span>
- <span data-ttu-id="93f26-474">Mode d’insertion VI : `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="93f26-474">Vi insert mode: `<Ctrl+]>`</span></span>
- <span data-ttu-id="93f26-475">Mode de commande VI : `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="93f26-475">Vi command mode: `<Ctrl+]>`</span></span>

### <a name="gotocolumn"></a><span data-ttu-id="93f26-476">GotoColumn</span><span class="sxs-lookup"><span data-stu-id="93f26-476">GotoColumn</span></span>

<span data-ttu-id="93f26-477">Accédez à la colonne indiquée par arg.</span><span class="sxs-lookup"><span data-stu-id="93f26-477">Move to the column indicated by arg.</span></span>

- <span data-ttu-id="93f26-478">Mode de commande VI : `<|>`</span><span class="sxs-lookup"><span data-stu-id="93f26-478">Vi command mode: `<|>`</span></span>

### <a name="gotofirstnonblankofline"></a><span data-ttu-id="93f26-479">GotoFirstNonBlankOfLine</span><span class="sxs-lookup"><span data-stu-id="93f26-479">GotoFirstNonBlankOfLine</span></span>

<span data-ttu-id="93f26-480">Placez le curseur sur le premier caractère non vide de la ligne.</span><span class="sxs-lookup"><span data-stu-id="93f26-480">Move the cursor to the first non-blank character in the line.</span></span>

- <span data-ttu-id="93f26-481">Mode de commande VI : `<^>`</span><span class="sxs-lookup"><span data-stu-id="93f26-481">Vi command mode: `<^>`</span></span>

### <a name="movetoendofline"></a><span data-ttu-id="93f26-482">MoveToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="93f26-482">MoveToEndOfLine</span></span>

<span data-ttu-id="93f26-483">Placez le curseur à la fin de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="93f26-483">Move the cursor to the end of the input.</span></span>

- <span data-ttu-id="93f26-484">Mode de commande VI : `<End>` , `<$>`</span><span class="sxs-lookup"><span data-stu-id="93f26-484">Vi command mode: `<End>`, `<$>`</span></span>

### <a name="nextline"></a><span data-ttu-id="93f26-485">NextLine</span><span class="sxs-lookup"><span data-stu-id="93f26-485">NextLine</span></span>

<span data-ttu-id="93f26-486">Déplacer le curseur sur la ligne suivante.</span><span class="sxs-lookup"><span data-stu-id="93f26-486">Move the cursor to the next line.</span></span>

- <span data-ttu-id="93f26-487">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="93f26-487">Function is unbound.</span></span>

### <a name="nextword"></a><span data-ttu-id="93f26-488">NextWord</span><span class="sxs-lookup"><span data-stu-id="93f26-488">NextWord</span></span>

<span data-ttu-id="93f26-489">Déplacer le curseur vers l’avant jusqu’au début du mot suivant.</span><span class="sxs-lookup"><span data-stu-id="93f26-489">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="93f26-490">Les limites de mots sont définies par un jeu de caractères configurable.</span><span class="sxs-lookup"><span data-stu-id="93f26-490">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="93f26-491">Cmd `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="93f26-491">Cmd: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="93f26-492">Mode d’insertion VI : `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="93f26-492">Vi insert mode: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="93f26-493">Mode de commande VI : `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="93f26-493">Vi command mode: `<Ctrl+RightArrow>`</span></span>

### <a name="nextwordend"></a><span data-ttu-id="93f26-494">NextWordEnd</span><span class="sxs-lookup"><span data-stu-id="93f26-494">NextWordEnd</span></span>

<span data-ttu-id="93f26-495">Déplacer le curseur vers l’avant jusqu’à la fin du mot actuel, ou si entre les mots, à la fin du mot suivant.</span><span class="sxs-lookup"><span data-stu-id="93f26-495">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="93f26-496">Les limites de mots sont définies par un jeu de caractères configurable.</span><span class="sxs-lookup"><span data-stu-id="93f26-496">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="93f26-497">Mode de commande VI : `<e>`</span><span class="sxs-lookup"><span data-stu-id="93f26-497">Vi command mode: `<e>`</span></span>

### <a name="previousline"></a><span data-ttu-id="93f26-498">PreviousLine</span><span class="sxs-lookup"><span data-stu-id="93f26-498">PreviousLine</span></span>

<span data-ttu-id="93f26-499">Placez le curseur sur la ligne précédente.</span><span class="sxs-lookup"><span data-stu-id="93f26-499">Move the cursor to the previous line.</span></span>

- <span data-ttu-id="93f26-500">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="93f26-500">Function is unbound.</span></span>

### <a name="shellbackwardword"></a><span data-ttu-id="93f26-501">ShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="93f26-501">ShellBackwardWord</span></span>

<span data-ttu-id="93f26-502">Ramener le curseur au début du mot actuel, ou si entre les mots, le début du mot précédent.</span><span class="sxs-lookup"><span data-stu-id="93f26-502">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="93f26-503">Les limites de mots sont définies par les jetons PowerShell.</span><span class="sxs-lookup"><span data-stu-id="93f26-503">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="93f26-504">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="93f26-504">Function is unbound.</span></span>

### <a name="shellforwardword"></a><span data-ttu-id="93f26-505">ShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="93f26-505">ShellForwardWord</span></span>

<span data-ttu-id="93f26-506">Déplacer le curseur vers l’avant jusqu’au début du mot suivant.</span><span class="sxs-lookup"><span data-stu-id="93f26-506">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="93f26-507">Les limites de mots sont définies par les jetons PowerShell.</span><span class="sxs-lookup"><span data-stu-id="93f26-507">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="93f26-508">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="93f26-508">Function is unbound.</span></span>

### <a name="shellnextword"></a><span data-ttu-id="93f26-509">ShellNextWord</span><span class="sxs-lookup"><span data-stu-id="93f26-509">ShellNextWord</span></span>

<span data-ttu-id="93f26-510">Déplacer le curseur vers l’avant jusqu’à la fin du mot actuel, ou si entre les mots, à la fin du mot suivant.</span><span class="sxs-lookup"><span data-stu-id="93f26-510">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="93f26-511">Les limites de mots sont définies par les jetons PowerShell.</span><span class="sxs-lookup"><span data-stu-id="93f26-511">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="93f26-512">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="93f26-512">Function is unbound.</span></span>

### <a name="vibackwardword"></a><span data-ttu-id="93f26-513">ViBackwardWord</span><span class="sxs-lookup"><span data-stu-id="93f26-513">ViBackwardWord</span></span>

<span data-ttu-id="93f26-514">Ramener le curseur au début du mot actuel, ou si entre les mots, le début du mot précédent.</span><span class="sxs-lookup"><span data-stu-id="93f26-514">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="93f26-515">Les limites de mots sont définies par un jeu de caractères configurable.</span><span class="sxs-lookup"><span data-stu-id="93f26-515">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="93f26-516">Mode de commande VI : `<b>`</span><span class="sxs-lookup"><span data-stu-id="93f26-516">Vi command mode: `<b>`</span></span>

### <a name="viendofglob"></a><span data-ttu-id="93f26-517">ViEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="93f26-517">ViEndOfGlob</span></span>

<span data-ttu-id="93f26-518">Déplace le curseur à la fin du mot, en utilisant uniquement des espaces blancs comme délimiteurs.</span><span class="sxs-lookup"><span data-stu-id="93f26-518">Moves the cursor to the end of the word, using only white space as delimiters.</span></span>

- <span data-ttu-id="93f26-519">Mode de commande VI : `<E>`</span><span class="sxs-lookup"><span data-stu-id="93f26-519">Vi command mode: `<E>`</span></span>

### <a name="viendofpreviousglob"></a><span data-ttu-id="93f26-520">ViEndOfPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="93f26-520">ViEndOfPreviousGlob</span></span>

<span data-ttu-id="93f26-521">Passe à la fin du mot précédent, en utilisant uniquement un espace blanc comme délimiteur de mot.</span><span class="sxs-lookup"><span data-stu-id="93f26-521">Moves to the end of the previous word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="93f26-522">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="93f26-522">Function is unbound.</span></span>

### <a name="vigotobrace"></a><span data-ttu-id="93f26-523">ViGotoBrace</span><span class="sxs-lookup"><span data-stu-id="93f26-523">ViGotoBrace</span></span>

<span data-ttu-id="93f26-524">Semblable à GotoBrace, mais est basé sur un caractère et non sur un jeton.</span><span class="sxs-lookup"><span data-stu-id="93f26-524">Similar to GotoBrace, but is character based instead of token based.</span></span>

- <span data-ttu-id="93f26-525">Mode de commande VI : `<%>`</span><span class="sxs-lookup"><span data-stu-id="93f26-525">Vi command mode: `<%>`</span></span>

### <a name="vinextglob"></a><span data-ttu-id="93f26-526">ViNextGlob</span><span class="sxs-lookup"><span data-stu-id="93f26-526">ViNextGlob</span></span>

<span data-ttu-id="93f26-527">Passe au mot suivant, en utilisant uniquement un espace blanc comme délimiteur de mot.</span><span class="sxs-lookup"><span data-stu-id="93f26-527">Moves to the next word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="93f26-528">Mode de commande VI : `<W>`</span><span class="sxs-lookup"><span data-stu-id="93f26-528">Vi command mode: `<W>`</span></span>

### <a name="vinextword"></a><span data-ttu-id="93f26-529">ViNextWord</span><span class="sxs-lookup"><span data-stu-id="93f26-529">ViNextWord</span></span>

<span data-ttu-id="93f26-530">Déplacer le curseur vers l’avant jusqu’au début du mot suivant.</span><span class="sxs-lookup"><span data-stu-id="93f26-530">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="93f26-531">Les limites de mots sont définies par un jeu de caractères configurable.</span><span class="sxs-lookup"><span data-stu-id="93f26-531">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="93f26-532">Mode de commande VI : `<w>`</span><span class="sxs-lookup"><span data-stu-id="93f26-532">Vi command mode: `<w>`</span></span>

## <a name="history-functions"></a><span data-ttu-id="93f26-533">Fonctions d’historique</span><span class="sxs-lookup"><span data-stu-id="93f26-533">History functions</span></span>

### <a name="beginningofhistory"></a><span data-ttu-id="93f26-534">BeginningOfHistory</span><span class="sxs-lookup"><span data-stu-id="93f26-534">BeginningOfHistory</span></span>

<span data-ttu-id="93f26-535">Accéder au premier élément de l’historique.</span><span class="sxs-lookup"><span data-stu-id="93f26-535">Move to the first item in the history.</span></span>

- <span data-ttu-id="93f26-536">Emacs- `<Alt+`<>\`</span><span class="sxs-lookup"><span data-stu-id="93f26-536">Emacs: `<Alt+`<>\`</span></span>

### <a name="clearhistory"></a><span data-ttu-id="93f26-537">ClearHistory</span><span class="sxs-lookup"><span data-stu-id="93f26-537">ClearHistory</span></span>

<span data-ttu-id="93f26-538">Efface l’historique dans PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="93f26-538">Clears history in PSReadLine.</span></span> <span data-ttu-id="93f26-539">Cela n’affecte pas l’historique PowerShell.</span><span class="sxs-lookup"><span data-stu-id="93f26-539">This does not affect PowerShell history.</span></span>

- <span data-ttu-id="93f26-540">Cmd `<Alt+F7>`</span><span class="sxs-lookup"><span data-stu-id="93f26-540">Cmd: `<Alt+F7>`</span></span>

### <a name="endofhistory"></a><span data-ttu-id="93f26-541">EndOfHistory</span><span class="sxs-lookup"><span data-stu-id="93f26-541">EndOfHistory</span></span>

<span data-ttu-id="93f26-542">Accéder au dernier élément (l’entrée en cours) dans l’historique.</span><span class="sxs-lookup"><span data-stu-id="93f26-542">Move to the last item (the current input) in the history.</span></span>

- <span data-ttu-id="93f26-543">Emacs- `<Alt+>>`</span><span class="sxs-lookup"><span data-stu-id="93f26-543">Emacs: `<Alt+>>`</span></span>

### <a name="forwardsearchhistory"></a><span data-ttu-id="93f26-544">ForwardSearchHistory</span><span class="sxs-lookup"><span data-stu-id="93f26-544">ForwardSearchHistory</span></span>

<span data-ttu-id="93f26-545">Effectuer une recherche incrémentielle par progression dans l’historique.</span><span class="sxs-lookup"><span data-stu-id="93f26-545">Perform an incremental forward search through history.</span></span>

- <span data-ttu-id="93f26-546">Cmd `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="93f26-546">Cmd: `<Ctrl+s>`</span></span>
- <span data-ttu-id="93f26-547">Emacs- `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="93f26-547">Emacs: `<Ctrl+s>`</span></span>

### <a name="historysearchbackward"></a><span data-ttu-id="93f26-548">HistorySearchBackward</span><span class="sxs-lookup"><span data-stu-id="93f26-548">HistorySearchBackward</span></span>

<span data-ttu-id="93f26-549">Remplacez l’entrée actuelle par l’élément « Previous » de l’historique PSReadLine qui correspond aux caractères entre le début et l’entrée et le curseur.</span><span class="sxs-lookup"><span data-stu-id="93f26-549">Replace the current input with the 'previous' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="93f26-550">Cmd `<F8>`</span><span class="sxs-lookup"><span data-stu-id="93f26-550">Cmd: `<F8>`</span></span>

### <a name="historysearchforward"></a><span data-ttu-id="93f26-551">HistorySearchForward</span><span class="sxs-lookup"><span data-stu-id="93f26-551">HistorySearchForward</span></span>

<span data-ttu-id="93f26-552">Remplacez l’entrée actuelle par l’élément « Next » de l’historique PSReadLine qui correspond aux caractères entre le début et l’entrée et le curseur.</span><span class="sxs-lookup"><span data-stu-id="93f26-552">Replace the current input with the 'next' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="93f26-553">Cmd `<Shift+F8>`</span><span class="sxs-lookup"><span data-stu-id="93f26-553">Cmd: `<Shift+F8>`</span></span>

### <a name="nexthistory"></a><span data-ttu-id="93f26-554">NextHistory</span><span class="sxs-lookup"><span data-stu-id="93f26-554">NextHistory</span></span>

<span data-ttu-id="93f26-555">Remplacez l’entrée actuelle par l’élément « Next » de l’historique PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="93f26-555">Replace the current input with the 'next' item from PSReadLine history.</span></span>

- <span data-ttu-id="93f26-556">Cmd `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="93f26-556">Cmd: `<DownArrow>`</span></span>
- <span data-ttu-id="93f26-557">Emacs- `<DownArrow>` , `<Ctrl+n>`</span><span class="sxs-lookup"><span data-stu-id="93f26-557">Emacs: `<DownArrow>`, `<Ctrl+n>`</span></span>
- <span data-ttu-id="93f26-558">Mode d’insertion VI : `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="93f26-558">Vi insert mode: `<DownArrow>`</span></span>
- <span data-ttu-id="93f26-559">Mode de commande VI : `<DownArrow>` , `<j>` , `<+>`</span><span class="sxs-lookup"><span data-stu-id="93f26-559">Vi command mode: `<DownArrow>`, `<j>`, `<+>`</span></span>

### <a name="previoushistory"></a><span data-ttu-id="93f26-560">PreviousHistory</span><span class="sxs-lookup"><span data-stu-id="93f26-560">PreviousHistory</span></span>

<span data-ttu-id="93f26-561">Remplacez l’entrée actuelle par l’élément « Previous » de l’historique PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="93f26-561">Replace the current input with the 'previous' item from PSReadLine history.</span></span>

- <span data-ttu-id="93f26-562">Cmd `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="93f26-562">Cmd: `<UpArrow>`</span></span>
- <span data-ttu-id="93f26-563">Emacs- `<UpArrow>` , `<Ctrl+p>`</span><span class="sxs-lookup"><span data-stu-id="93f26-563">Emacs: `<UpArrow>`, `<Ctrl+p>`</span></span>
- <span data-ttu-id="93f26-564">Mode d’insertion VI : `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="93f26-564">Vi insert mode: `<UpArrow>`</span></span>
- <span data-ttu-id="93f26-565">Mode de commande VI : `<UpArrow>` , `<k>` , `<->`</span><span class="sxs-lookup"><span data-stu-id="93f26-565">Vi command mode: `<UpArrow>`, `<k>`, `<->`</span></span>

### <a name="reversesearchhistory"></a><span data-ttu-id="93f26-566">ReverseSearchHistory</span><span class="sxs-lookup"><span data-stu-id="93f26-566">ReverseSearchHistory</span></span>

<span data-ttu-id="93f26-567">Effectuer une recherche incrémentielle incrémentielle dans l’historique.</span><span class="sxs-lookup"><span data-stu-id="93f26-567">Perform an incremental backward search through history.</span></span>

- <span data-ttu-id="93f26-568">Cmd `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="93f26-568">Cmd: `<Ctrl+r>`</span></span>
- <span data-ttu-id="93f26-569">Emacs- `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="93f26-569">Emacs: `<Ctrl+r>`</span></span>

### <a name="visearchhistorybackward"></a><span data-ttu-id="93f26-570">ViSearchHistoryBackward</span><span class="sxs-lookup"><span data-stu-id="93f26-570">ViSearchHistoryBackward</span></span>

<span data-ttu-id="93f26-571">Demande une chaîne de recherche et lance la recherche sur AcceptLine.</span><span class="sxs-lookup"><span data-stu-id="93f26-571">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="93f26-572">Mode d’insertion VI : `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="93f26-572">Vi insert mode: `<Ctrl+r>`</span></span>
- <span data-ttu-id="93f26-573">Mode de commande VI : `</>` , `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="93f26-573">Vi command mode: `</>`, `<Ctrl+r>`</span></span>

## <a name="completion-functions"></a><span data-ttu-id="93f26-574">Fonctions d’achèvement</span><span class="sxs-lookup"><span data-stu-id="93f26-574">Completion functions</span></span>

### <a name="complete"></a><span data-ttu-id="93f26-575">Terminé</span><span class="sxs-lookup"><span data-stu-id="93f26-575">Complete</span></span>

<span data-ttu-id="93f26-576">Tentative d’exécution de l’opération sur le texte entourant le curseur.</span><span class="sxs-lookup"><span data-stu-id="93f26-576">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="93f26-577">S’il existe plusieurs saisies semi-automatiques possibles, le plus long préfixe non ambigu est utilisé pour la finalisation.</span><span class="sxs-lookup"><span data-stu-id="93f26-577">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="93f26-578">Si vous essayez de terminer la saisie semi-automatique la plus longue, une liste des saisies semi-automatiques possibles s’affiche.</span><span class="sxs-lookup"><span data-stu-id="93f26-578">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="93f26-579">Emacs- `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="93f26-579">Emacs: `<Tab>`</span></span>

### <a name="menucomplete"></a><span data-ttu-id="93f26-580">MenuComplete</span><span class="sxs-lookup"><span data-stu-id="93f26-580">MenuComplete</span></span>

<span data-ttu-id="93f26-581">Tentative d’exécution de l’opération sur le texte entourant le curseur.</span><span class="sxs-lookup"><span data-stu-id="93f26-581">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="93f26-582">S’il existe plusieurs saisies semi-automatiques possibles, le plus long préfixe non ambigu est utilisé pour la finalisation.</span><span class="sxs-lookup"><span data-stu-id="93f26-582">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="93f26-583">Si vous essayez de terminer la saisie semi-automatique la plus longue, une liste des saisies semi-automatiques possibles s’affiche.</span><span class="sxs-lookup"><span data-stu-id="93f26-583">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="93f26-584">Cmd `<Ctrl+Space>`</span><span class="sxs-lookup"><span data-stu-id="93f26-584">Cmd: `<Ctrl+Space>`</span></span>
- <span data-ttu-id="93f26-585">Emacs- `<Ctrl+Space>`</span><span class="sxs-lookup"><span data-stu-id="93f26-585">Emacs: `<Ctrl+Space>`</span></span>

### <a name="possiblecompletions"></a><span data-ttu-id="93f26-586">PossibleCompletions</span><span class="sxs-lookup"><span data-stu-id="93f26-586">PossibleCompletions</span></span>

<span data-ttu-id="93f26-587">Affiche la liste des saisies semi-automatiques possibles.</span><span class="sxs-lookup"><span data-stu-id="93f26-587">Display the list of possible completions.</span></span>

- <span data-ttu-id="93f26-588">Emacs- `<Alt+=>`</span><span class="sxs-lookup"><span data-stu-id="93f26-588">Emacs: `<Alt+=>`</span></span>
- <span data-ttu-id="93f26-589">Mode d’insertion VI : `<Ctrl+Space>`</span><span class="sxs-lookup"><span data-stu-id="93f26-589">Vi insert mode: `<Ctrl+Space>`</span></span>
- <span data-ttu-id="93f26-590">Mode de commande VI : `<Ctrl+Space>`</span><span class="sxs-lookup"><span data-stu-id="93f26-590">Vi command mode: `<Ctrl+Space>`</span></span>

### <a name="tabcompletenext"></a><span data-ttu-id="93f26-591">TabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="93f26-591">TabCompleteNext</span></span>

<span data-ttu-id="93f26-592">Tente de terminer le texte entourant le curseur avec la prochaine saisie semi-automatique disponible.</span><span class="sxs-lookup"><span data-stu-id="93f26-592">Attempt to complete the text surrounding the cursor with the next available completion.</span></span>

- <span data-ttu-id="93f26-593">Cmd `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="93f26-593">Cmd: `<Tab>`</span></span>
- <span data-ttu-id="93f26-594">Mode de commande VI : `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="93f26-594">Vi command mode: `<Tab>`</span></span>

### <a name="tabcompleteprevious"></a><span data-ttu-id="93f26-595">TabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="93f26-595">TabCompletePrevious</span></span>

<span data-ttu-id="93f26-596">Tente de terminer le texte entourant le curseur avec l’achèvement disponible précédent.</span><span class="sxs-lookup"><span data-stu-id="93f26-596">Attempt to complete the text surrounding the cursor with the previous available completion.</span></span>

- <span data-ttu-id="93f26-597">Cmd `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="93f26-597">Cmd: `<Shift+Tab>`</span></span>
- <span data-ttu-id="93f26-598">Mode de commande VI : `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="93f26-598">Vi command mode: `<Shift+Tab>`</span></span>

### <a name="vitabcompletenext"></a><span data-ttu-id="93f26-599">ViTabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="93f26-599">ViTabCompleteNext</span></span>

<span data-ttu-id="93f26-600">Met fin au groupe d’édition actuel, si nécessaire, et appelle TabCompleteNext.</span><span class="sxs-lookup"><span data-stu-id="93f26-600">Ends the current edit group, if needed, and invokes TabCompleteNext.</span></span>

- <span data-ttu-id="93f26-601">Mode d’insertion VI : `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="93f26-601">Vi insert mode: `<Tab>`</span></span>

### <a name="vitabcompleteprevious"></a><span data-ttu-id="93f26-602">ViTabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="93f26-602">ViTabCompletePrevious</span></span>

<span data-ttu-id="93f26-603">Met fin au groupe d’édition actuel, si nécessaire, et appelle TabCompletePrevious.</span><span class="sxs-lookup"><span data-stu-id="93f26-603">Ends the current edit group, if needed, and invokes TabCompletePrevious.</span></span>

- <span data-ttu-id="93f26-604">Mode d’insertion VI : `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="93f26-604">Vi insert mode: `<Shift+Tab>`</span></span>

## <a name="miscellaneous-functions"></a><span data-ttu-id="93f26-605">Fonctions diverses</span><span class="sxs-lookup"><span data-stu-id="93f26-605">Miscellaneous functions</span></span>

### <a name="capturescreen"></a><span data-ttu-id="93f26-606">CaptureScreen</span><span class="sxs-lookup"><span data-stu-id="93f26-606">CaptureScreen</span></span>

<span data-ttu-id="93f26-607">Démarrer la capture d’écran interactive-flèches haut et bas sélectionnez lignes, entrez copie le texte sélectionné dans le presse-papiers en tant que texte et html.</span><span class="sxs-lookup"><span data-stu-id="93f26-607">Start interactive screen capture - up/down arrows select lines, enter copies selected text to clipboard as text and html.</span></span>

- <span data-ttu-id="93f26-608">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="93f26-608">Function is unbound.</span></span>

### <a name="clearscreen"></a><span data-ttu-id="93f26-609">ClearScreen</span><span class="sxs-lookup"><span data-stu-id="93f26-609">ClearScreen</span></span>

<span data-ttu-id="93f26-610">Effacez l’écran et dessinez la ligne active en haut de l’écran.</span><span class="sxs-lookup"><span data-stu-id="93f26-610">Clear the screen and draw the current line at the top of the screen.</span></span>

- <span data-ttu-id="93f26-611">Cmd `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="93f26-611">Cmd: `<Ctrl+l>`</span></span>
- <span data-ttu-id="93f26-612">Emacs- `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="93f26-612">Emacs: `<Ctrl+l>`</span></span>
- <span data-ttu-id="93f26-613">Mode d’insertion VI : `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="93f26-613">Vi insert mode: `<Ctrl+l>`</span></span>
- <span data-ttu-id="93f26-614">Mode de commande VI : `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="93f26-614">Vi command mode: `<Ctrl+l>`</span></span>

### <a name="digitargument"></a><span data-ttu-id="93f26-615">DigitArgument</span><span class="sxs-lookup"><span data-stu-id="93f26-615">DigitArgument</span></span>

<span data-ttu-id="93f26-616">Démarrez un nouvel argument digit à passer à d’autres fonctions.</span><span class="sxs-lookup"><span data-stu-id="93f26-616">Start a new digit argument to pass to other functions.</span></span>

- <span data-ttu-id="93f26-617">Cmd : `<Alt+0>` ,,,,, `<Alt+1>` `<Alt+2>` `<Alt+3>` `<Alt+4>` `<Alt+5>` , `<Alt+6>` , `<Alt+7>` , `<Alt+8>` , `<Alt+9>` , `<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="93f26-617">Cmd: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="93f26-618">Emacs-,,,,,,,,, `<Alt+0>` `<Alt+1>` `<Alt+2>` `<Alt+3>` `<Alt+4>` `<Alt+5>` `<Alt+6>` `<Alt+7>` `<Alt+8>` , `<Alt+9>` , `<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="93f26-618">Emacs: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="93f26-619">Mode de commande VI : `<0>` , `<1>` ,, `<2>` `<3>` , `<4>` , `<5>` , `<6>` , `<7>` , `<8>` , `<9>`</span><span class="sxs-lookup"><span data-stu-id="93f26-619">Vi command mode: `<0>`, `<1>`, `<2>`, `<3>`, `<4>`, `<5>`, `<6>`, `<7>`, `<8>`, `<9>`</span></span>

### <a name="invokeprompt"></a><span data-ttu-id="93f26-620">InvokePrompt</span><span class="sxs-lookup"><span data-stu-id="93f26-620">InvokePrompt</span></span>

<span data-ttu-id="93f26-621">Efface l’invite en cours et appelle la fonction prompt pour réafficher l’invite.</span><span class="sxs-lookup"><span data-stu-id="93f26-621">Erases the current prompt and calls the prompt function to redisplay the prompt.</span></span> <span data-ttu-id="93f26-622">Utile pour les gestionnaires de clés personnalisés qui changent d’État, par exemple modifier le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="93f26-622">Useful for custom key handlers that change state, e.g. change the current directory.</span></span>

- <span data-ttu-id="93f26-623">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="93f26-623">Function is unbound.</span></span>

### <a name="scrolldisplaydown"></a><span data-ttu-id="93f26-624">ScrollDisplayDown</span><span class="sxs-lookup"><span data-stu-id="93f26-624">ScrollDisplayDown</span></span>

<span data-ttu-id="93f26-625">Faites défiler l’écran vers le volet d’affichage.</span><span class="sxs-lookup"><span data-stu-id="93f26-625">Scroll the display down one screen.</span></span>

- <span data-ttu-id="93f26-626">Cmd `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="93f26-626">Cmd: `<PageDown>`</span></span>
- <span data-ttu-id="93f26-627">Emacs- `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="93f26-627">Emacs: `<PageDown>`</span></span>

### <a name="scrolldisplaydownline"></a><span data-ttu-id="93f26-628">ScrollDisplayDownLine</span><span class="sxs-lookup"><span data-stu-id="93f26-628">ScrollDisplayDownLine</span></span>

<span data-ttu-id="93f26-629">Faites défiler l’affichage d’une ligne vers le dessous.</span><span class="sxs-lookup"><span data-stu-id="93f26-629">Scroll the display down one line.</span></span>

- <span data-ttu-id="93f26-630">Cmd `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="93f26-630">Cmd: `<Ctrl+PageDown>`</span></span>
- <span data-ttu-id="93f26-631">Emacs- `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="93f26-631">Emacs: `<Ctrl+PageDown>`</span></span>

### <a name="scrolldisplaytocursor"></a><span data-ttu-id="93f26-632">ScrollDisplayToCursor</span><span class="sxs-lookup"><span data-stu-id="93f26-632">ScrollDisplayToCursor</span></span>

<span data-ttu-id="93f26-633">Faites défiler l’affichage jusqu’au curseur.</span><span class="sxs-lookup"><span data-stu-id="93f26-633">Scroll the display to the cursor.</span></span>

- <span data-ttu-id="93f26-634">Emacs- `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="93f26-634">Emacs: `<Ctrl+End>`</span></span>

### <a name="scrolldisplaytop"></a><span data-ttu-id="93f26-635">ScrollDisplayTop</span><span class="sxs-lookup"><span data-stu-id="93f26-635">ScrollDisplayTop</span></span>

<span data-ttu-id="93f26-636">Faites défiler l’affichage vers le haut.</span><span class="sxs-lookup"><span data-stu-id="93f26-636">Scroll the display to the top.</span></span>

- <span data-ttu-id="93f26-637">Emacs- `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="93f26-637">Emacs: `<Ctrl+Home>`</span></span>

### <a name="scrolldisplayup"></a><span data-ttu-id="93f26-638">ScrollDisplayUp</span><span class="sxs-lookup"><span data-stu-id="93f26-638">ScrollDisplayUp</span></span>

<span data-ttu-id="93f26-639">Faites défiler l’écran afficher vers le haut.</span><span class="sxs-lookup"><span data-stu-id="93f26-639">Scroll the display up one screen.</span></span>

- <span data-ttu-id="93f26-640">Cmd `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="93f26-640">Cmd: `<PageUp>`</span></span>
- <span data-ttu-id="93f26-641">Emacs- `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="93f26-641">Emacs: `<PageUp>`</span></span>

### <a name="scrolldisplayupline"></a><span data-ttu-id="93f26-642">ScrollDisplayUpLine</span><span class="sxs-lookup"><span data-stu-id="93f26-642">ScrollDisplayUpLine</span></span>

<span data-ttu-id="93f26-643">Faites défiler l’affichage d’une ligne vers le haut.</span><span class="sxs-lookup"><span data-stu-id="93f26-643">Scroll the display up one line.</span></span>

- <span data-ttu-id="93f26-644">Cmd `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="93f26-644">Cmd: `<Ctrl+PageUp>`</span></span>
- <span data-ttu-id="93f26-645">Emacs- `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="93f26-645">Emacs: `<Ctrl+PageUp>`</span></span>

### <a name="selfinsert"></a><span data-ttu-id="93f26-646">SelfInsert</span><span class="sxs-lookup"><span data-stu-id="93f26-646">SelfInsert</span></span>

<span data-ttu-id="93f26-647">Insérez la clé.</span><span class="sxs-lookup"><span data-stu-id="93f26-647">Insert the key.</span></span>

- <span data-ttu-id="93f26-648">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="93f26-648">Function is unbound.</span></span>

### <a name="showkeybindings"></a><span data-ttu-id="93f26-649">ShowKeyBindings</span><span class="sxs-lookup"><span data-stu-id="93f26-649">ShowKeyBindings</span></span>

<span data-ttu-id="93f26-650">Affiche toutes les clés liées.</span><span class="sxs-lookup"><span data-stu-id="93f26-650">Show all bound keys.</span></span>

- <span data-ttu-id="93f26-651">Cmd `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="93f26-651">Cmd: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="93f26-652">Emacs- `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="93f26-652">Emacs: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="93f26-653">Mode d’insertion VI : `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="93f26-653">Vi insert mode: `<Ctrl+Alt+?>`</span></span>

### <a name="vicommandmode"></a><span data-ttu-id="93f26-654">ViCommandMode</span><span class="sxs-lookup"><span data-stu-id="93f26-654">ViCommandMode</span></span>

<span data-ttu-id="93f26-655">Basculez le mode d’opération actuel de Vi-Insert à VI-Command.</span><span class="sxs-lookup"><span data-stu-id="93f26-655">Switch the current operating mode from Vi-Insert to Vi-Command.</span></span>

- <span data-ttu-id="93f26-656">Mode d’insertion VI : `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="93f26-656">Vi insert mode: `<Escape>`</span></span>

### <a name="vidigitargumentinchord"></a><span data-ttu-id="93f26-657">ViDigitArgumentInChord</span><span class="sxs-lookup"><span data-stu-id="93f26-657">ViDigitArgumentInChord</span></span>

<span data-ttu-id="93f26-658">Démarrez un nouvel argument digit à passer à d’autres fonctions dans l’un des cordes de VI.</span><span class="sxs-lookup"><span data-stu-id="93f26-658">Start a new digit argument to pass to other functions while in one of vi's chords.</span></span>

- <span data-ttu-id="93f26-659">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="93f26-659">Function is unbound.</span></span>

### <a name="vieditvisually"></a><span data-ttu-id="93f26-660">ViEditVisually</span><span class="sxs-lookup"><span data-stu-id="93f26-660">ViEditVisually</span></span>

<span data-ttu-id="93f26-661">Modifiez la ligne de commande dans un éditeur de texte spécifié par $env : EDITOR ou $env : VISUAL.</span><span class="sxs-lookup"><span data-stu-id="93f26-661">Edit the command line in a text editor specified by $env:EDITOR or $env:VISUAL.</span></span>

- <span data-ttu-id="93f26-662">Emacs- `<Ctrl+x,Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="93f26-662">Emacs: `<Ctrl+x,Ctrl+e>`</span></span>
- <span data-ttu-id="93f26-663">Mode de commande VI : `<v>`</span><span class="sxs-lookup"><span data-stu-id="93f26-663">Vi command mode: `<v>`</span></span>

### <a name="viexit"></a><span data-ttu-id="93f26-664">ViExit</span><span class="sxs-lookup"><span data-stu-id="93f26-664">ViExit</span></span>

<span data-ttu-id="93f26-665">Quitte l’interpréteur de commandes.</span><span class="sxs-lookup"><span data-stu-id="93f26-665">Exits the shell.</span></span>

- <span data-ttu-id="93f26-666">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="93f26-666">Function is unbound.</span></span>

### <a name="viinsertmode"></a><span data-ttu-id="93f26-667">ViInsertMode</span><span class="sxs-lookup"><span data-stu-id="93f26-667">ViInsertMode</span></span>

<span data-ttu-id="93f26-668">Basculez en mode insertion.</span><span class="sxs-lookup"><span data-stu-id="93f26-668">Switch to Insert mode.</span></span>

- <span data-ttu-id="93f26-669">Mode de commande VI : `<i>`</span><span class="sxs-lookup"><span data-stu-id="93f26-669">Vi command mode: `<i>`</span></span>

### <a name="whatiskey"></a><span data-ttu-id="93f26-670">WhatIsKey</span><span class="sxs-lookup"><span data-stu-id="93f26-670">WhatIsKey</span></span>

<span data-ttu-id="93f26-671">Lisez une clé et dites-moi à quoi la clé est liée.</span><span class="sxs-lookup"><span data-stu-id="93f26-671">Read a key and tell me what the key is bound to.</span></span>

- <span data-ttu-id="93f26-672">Cmd `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="93f26-672">Cmd: `<Alt+?>`</span></span>
- <span data-ttu-id="93f26-673">Emacs- `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="93f26-673">Emacs: `<Alt+?>`</span></span>

## <a name="selection-functions"></a><span data-ttu-id="93f26-674">Fonctions de sélection</span><span class="sxs-lookup"><span data-stu-id="93f26-674">Selection functions</span></span>

### <a name="exchangepointandmark"></a><span data-ttu-id="93f26-675">ExchangePointAndMark</span><span class="sxs-lookup"><span data-stu-id="93f26-675">ExchangePointAndMark</span></span>

<span data-ttu-id="93f26-676">Le curseur est placé à l’emplacement de la marque et la marque est déplacée vers l’emplacement du curseur.</span><span class="sxs-lookup"><span data-stu-id="93f26-676">The cursor is placed at the location of the mark and the mark is moved to the location of the cursor.</span></span>

- <span data-ttu-id="93f26-677">Emacs- `<Ctrl+x,Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="93f26-677">Emacs: `<Ctrl+x,Ctrl+x>`</span></span>

### <a name="selectall"></a><span data-ttu-id="93f26-678">SelectAll</span><span class="sxs-lookup"><span data-stu-id="93f26-678">SelectAll</span></span>

<span data-ttu-id="93f26-679">Sélectionnez la ligne entière.</span><span class="sxs-lookup"><span data-stu-id="93f26-679">Select the entire line.</span></span>

- <span data-ttu-id="93f26-680">Cmd `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="93f26-680">Cmd: `<Ctrl+a>`</span></span>

### <a name="selectbackwardchar"></a><span data-ttu-id="93f26-681">SelectBackwardChar</span><span class="sxs-lookup"><span data-stu-id="93f26-681">SelectBackwardChar</span></span>

<span data-ttu-id="93f26-682">Ajustez la sélection actuelle pour inclure le caractère précédent.</span><span class="sxs-lookup"><span data-stu-id="93f26-682">Adjust the current selection to include the previous character.</span></span>

- <span data-ttu-id="93f26-683">Cmd `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="93f26-683">Cmd: `<Shift+LeftArrow>`</span></span>
- <span data-ttu-id="93f26-684">Emacs- `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="93f26-684">Emacs: `<Shift+LeftArrow>`</span></span>

### <a name="selectbackwardsline"></a><span data-ttu-id="93f26-685">SelectBackwardsLine</span><span class="sxs-lookup"><span data-stu-id="93f26-685">SelectBackwardsLine</span></span>

<span data-ttu-id="93f26-686">Ajustez la sélection actuelle à inclure à partir du curseur jusqu’au début de la ligne.</span><span class="sxs-lookup"><span data-stu-id="93f26-686">Adjust the current selection to include from the cursor to the start of the line.</span></span>

- <span data-ttu-id="93f26-687">Cmd `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="93f26-687">Cmd: `<Shift+Home>`</span></span>
- <span data-ttu-id="93f26-688">Emacs- `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="93f26-688">Emacs: `<Shift+Home>`</span></span>

### <a name="selectbackwardword"></a><span data-ttu-id="93f26-689">SelectBackwardWord</span><span class="sxs-lookup"><span data-stu-id="93f26-689">SelectBackwardWord</span></span>

<span data-ttu-id="93f26-690">Ajustez la sélection actuelle pour inclure le mot précédent.</span><span class="sxs-lookup"><span data-stu-id="93f26-690">Adjust the current selection to include the previous word.</span></span>

- <span data-ttu-id="93f26-691">Cmd `<Shift+Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="93f26-691">Cmd: `<Shift+Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="93f26-692">Emacs- `<Alt+B>`</span><span class="sxs-lookup"><span data-stu-id="93f26-692">Emacs: `<Alt+B>`</span></span>

### <a name="selectforwardchar"></a><span data-ttu-id="93f26-693">SelectForwardChar</span><span class="sxs-lookup"><span data-stu-id="93f26-693">SelectForwardChar</span></span>

<span data-ttu-id="93f26-694">Ajustez la sélection actuelle pour inclure le caractère suivant.</span><span class="sxs-lookup"><span data-stu-id="93f26-694">Adjust the current selection to include the next character.</span></span>

- <span data-ttu-id="93f26-695">Cmd `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="93f26-695">Cmd: `<Shift+RightArrow>`</span></span>
- <span data-ttu-id="93f26-696">Emacs- `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="93f26-696">Emacs: `<Shift+RightArrow>`</span></span>

### <a name="selectforwardword"></a><span data-ttu-id="93f26-697">SelectForwardWord</span><span class="sxs-lookup"><span data-stu-id="93f26-697">SelectForwardWord</span></span>

<span data-ttu-id="93f26-698">Ajustez la sélection actuelle pour inclure le mot suivant à l’aide de ForwardWord.</span><span class="sxs-lookup"><span data-stu-id="93f26-698">Adjust the current selection to include the next word using ForwardWord.</span></span>

- <span data-ttu-id="93f26-699">Emacs- `<Alt+F>`</span><span class="sxs-lookup"><span data-stu-id="93f26-699">Emacs: `<Alt+F>`</span></span>

### <a name="selectline"></a><span data-ttu-id="93f26-700">SelectLine</span><span class="sxs-lookup"><span data-stu-id="93f26-700">SelectLine</span></span>

<span data-ttu-id="93f26-701">Ajustez la sélection actuelle à inclure à partir du curseur jusqu’à la fin de la ligne.</span><span class="sxs-lookup"><span data-stu-id="93f26-701">Adjust the current selection to include from the cursor to the end of the line.</span></span>

- <span data-ttu-id="93f26-702">Cmd `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="93f26-702">Cmd: `<Shift+End>`</span></span>
- <span data-ttu-id="93f26-703">Emacs- `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="93f26-703">Emacs: `<Shift+End>`</span></span>

### <a name="selectnextword"></a><span data-ttu-id="93f26-704">SelectNextWord</span><span class="sxs-lookup"><span data-stu-id="93f26-704">SelectNextWord</span></span>

<span data-ttu-id="93f26-705">Ajustez la sélection actuelle pour inclure le mot suivant.</span><span class="sxs-lookup"><span data-stu-id="93f26-705">Adjust the current selection to include the next word.</span></span>

- <span data-ttu-id="93f26-706">Cmd `<Shift+Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="93f26-706">Cmd: `<Shift+Ctrl+RightArrow>`</span></span>

### <a name="selectshellbackwardword"></a><span data-ttu-id="93f26-707">SelectShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="93f26-707">SelectShellBackwardWord</span></span>

<span data-ttu-id="93f26-708">Ajustez la sélection actuelle pour inclure le mot précédent à l’aide de ShellBackwardWord.</span><span class="sxs-lookup"><span data-stu-id="93f26-708">Adjust the current selection to include the previous word using ShellBackwardWord.</span></span>

- <span data-ttu-id="93f26-709">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="93f26-709">Function is unbound.</span></span>

### <a name="selectshellforwardword"></a><span data-ttu-id="93f26-710">SelectShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="93f26-710">SelectShellForwardWord</span></span>

<span data-ttu-id="93f26-711">Ajustez la sélection actuelle pour inclure le mot suivant à l’aide de ShellForwardWord.</span><span class="sxs-lookup"><span data-stu-id="93f26-711">Adjust the current selection to include the next word using ShellForwardWord.</span></span>

- <span data-ttu-id="93f26-712">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="93f26-712">Function is unbound.</span></span>

### <a name="selectshellnextword"></a><span data-ttu-id="93f26-713">SelectShellNextWord</span><span class="sxs-lookup"><span data-stu-id="93f26-713">SelectShellNextWord</span></span>

<span data-ttu-id="93f26-714">Ajustez la sélection actuelle pour inclure le mot suivant à l’aide de ShellNextWord.</span><span class="sxs-lookup"><span data-stu-id="93f26-714">Adjust the current selection to include the next word using ShellNextWord.</span></span>

- <span data-ttu-id="93f26-715">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="93f26-715">Function is unbound.</span></span>

### <a name="setmark"></a><span data-ttu-id="93f26-716">SetMark</span><span class="sxs-lookup"><span data-stu-id="93f26-716">SetMark</span></span>

<span data-ttu-id="93f26-717">Marquez l’emplacement actuel du curseur pour une utilisation dans une commande d’édition suivante.</span><span class="sxs-lookup"><span data-stu-id="93f26-717">Mark the current location of the cursor for use in a subsequent editing command.</span></span>

- <span data-ttu-id="93f26-718">Emacs- `<Ctrl+`>\`</span><span class="sxs-lookup"><span data-stu-id="93f26-718">Emacs: `<Ctrl+`>\`</span></span>

## <a name="search-functions"></a><span data-ttu-id="93f26-719">Fonctions de recherche</span><span class="sxs-lookup"><span data-stu-id="93f26-719">Search functions</span></span>

### <a name="charactersearch"></a><span data-ttu-id="93f26-720">CharacterSearch</span><span class="sxs-lookup"><span data-stu-id="93f26-720">CharacterSearch</span></span>

<span data-ttu-id="93f26-721">Lisez un caractère et recherchez l’occurrence suivante de ce caractère.</span><span class="sxs-lookup"><span data-stu-id="93f26-721">Read a character and search forward for the next occurrence of that character.</span></span>
<span data-ttu-id="93f26-722">Si un argument est spécifié, effectuez une recherche vers l’avant (ou vers l’arrière si négatif) pour la nième occurrence.</span><span class="sxs-lookup"><span data-stu-id="93f26-722">If an argument is specified, search forward (or backward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="93f26-723">Cmd `<F3>`</span><span class="sxs-lookup"><span data-stu-id="93f26-723">Cmd: `<F3>`</span></span>
- <span data-ttu-id="93f26-724">Emacs- `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="93f26-724">Emacs: `<Ctrl+]>`</span></span>
- <span data-ttu-id="93f26-725">Mode d’insertion VI : `<F3>`</span><span class="sxs-lookup"><span data-stu-id="93f26-725">Vi insert mode: `<F3>`</span></span>
- <span data-ttu-id="93f26-726">Mode de commande VI : `<F3>`</span><span class="sxs-lookup"><span data-stu-id="93f26-726">Vi command mode: `<F3>`</span></span>

### <a name="charactersearchbackward"></a><span data-ttu-id="93f26-727">CharacterSearchBackward</span><span class="sxs-lookup"><span data-stu-id="93f26-727">CharacterSearchBackward</span></span>

<span data-ttu-id="93f26-728">Lisez un caractère et recherchez l’occurrence suivante de ce caractère.</span><span class="sxs-lookup"><span data-stu-id="93f26-728">Read a character and search backward for the next occurrence of that character.</span></span> <span data-ttu-id="93f26-729">Si un argument est spécifié, effectuez une recherche vers l’arrière (ou vers l’avant si négatif) pour la nième occurrence.</span><span class="sxs-lookup"><span data-stu-id="93f26-729">If an argument is specified, search backward (or forward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="93f26-730">Cmd `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="93f26-730">Cmd: `<Shift+F3>`</span></span>
- <span data-ttu-id="93f26-731">Emacs- `<Ctrl+Alt+]>`</span><span class="sxs-lookup"><span data-stu-id="93f26-731">Emacs: `<Ctrl+Alt+]>`</span></span>
- <span data-ttu-id="93f26-732">Mode d’insertion VI : `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="93f26-732">Vi insert mode: `<Shift+F3>`</span></span>
- <span data-ttu-id="93f26-733">Mode de commande VI : `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="93f26-733">Vi command mode: `<Shift+F3>`</span></span>

### <a name="repeatlastcharsearch"></a><span data-ttu-id="93f26-734">RepeatLastCharSearch</span><span class="sxs-lookup"><span data-stu-id="93f26-734">RepeatLastCharSearch</span></span>

<span data-ttu-id="93f26-735">Répète la dernière recherche de caractères enregistrée.</span><span class="sxs-lookup"><span data-stu-id="93f26-735">Repeat the last recorded character search.</span></span>

- <span data-ttu-id="93f26-736">Mode de commande VI : `<;>`</span><span class="sxs-lookup"><span data-stu-id="93f26-736">Vi command mode: `<;>`</span></span>

### <a name="repeatlastcharsearchbackwards"></a><span data-ttu-id="93f26-737">RepeatLastCharSearchBackwards</span><span class="sxs-lookup"><span data-stu-id="93f26-737">RepeatLastCharSearchBackwards</span></span>

<span data-ttu-id="93f26-738">Répète la dernière recherche de caractères enregistrée, mais dans la direction opposée.</span><span class="sxs-lookup"><span data-stu-id="93f26-738">Repeat the last recorded character search, but in the opposite direction.</span></span>

- <span data-ttu-id="93f26-739">Mode de commande VI : `<,>`</span><span class="sxs-lookup"><span data-stu-id="93f26-739">Vi command mode: `<,>`</span></span>

### <a name="repeatsearch"></a><span data-ttu-id="93f26-740">RepeatSearch</span><span class="sxs-lookup"><span data-stu-id="93f26-740">RepeatSearch</span></span>

<span data-ttu-id="93f26-741">Répétez la dernière recherche dans la même direction que précédemment.</span><span class="sxs-lookup"><span data-stu-id="93f26-741">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="93f26-742">Mode de commande VI : `<n>`</span><span class="sxs-lookup"><span data-stu-id="93f26-742">Vi command mode: `<n>`</span></span>

### <a name="repeatsearchbackward"></a><span data-ttu-id="93f26-743">RepeatSearchBackward</span><span class="sxs-lookup"><span data-stu-id="93f26-743">RepeatSearchBackward</span></span>

<span data-ttu-id="93f26-744">Répétez la dernière recherche dans la même direction que précédemment.</span><span class="sxs-lookup"><span data-stu-id="93f26-744">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="93f26-745">Mode de commande VI : `<N>`</span><span class="sxs-lookup"><span data-stu-id="93f26-745">Vi command mode: `<N>`</span></span>

### <a name="searchchar"></a><span data-ttu-id="93f26-746">SearchChar</span><span class="sxs-lookup"><span data-stu-id="93f26-746">SearchChar</span></span>

<span data-ttu-id="93f26-747">Lisez le caractère suivant, puis recherchez-le, à l’avenir, puis annulez un caractère.</span><span class="sxs-lookup"><span data-stu-id="93f26-747">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="93f26-748">Il s’agit de la fonctionnalité’t'.</span><span class="sxs-lookup"><span data-stu-id="93f26-748">This is for 't' functionality.</span></span>

- <span data-ttu-id="93f26-749">Mode de commande VI : `<f>`</span><span class="sxs-lookup"><span data-stu-id="93f26-749">Vi command mode: `<f>`</span></span>

### <a name="searchcharbackward"></a><span data-ttu-id="93f26-750">SearchCharBackward</span><span class="sxs-lookup"><span data-stu-id="93f26-750">SearchCharBackward</span></span>

<span data-ttu-id="93f26-751">Lisez le caractère suivant, puis recherchez-le, en accédant à l’arrière, puis en annulant un caractère.</span><span class="sxs-lookup"><span data-stu-id="93f26-751">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="93f26-752">Il s’agit de la fonctionnalité’t'.</span><span class="sxs-lookup"><span data-stu-id="93f26-752">This is for 'T' functionality.</span></span>

- <span data-ttu-id="93f26-753">Mode de commande VI : `<F>`</span><span class="sxs-lookup"><span data-stu-id="93f26-753">Vi command mode: `<F>`</span></span>

### <a name="searchcharbackwardwithbackoff"></a><span data-ttu-id="93f26-754">SearchCharBackwardWithBackoff</span><span class="sxs-lookup"><span data-stu-id="93f26-754">SearchCharBackwardWithBackoff</span></span>

<span data-ttu-id="93f26-755">Lisez le caractère suivant, puis recherchez-le, en accédant à l’arrière, puis en annulant un caractère.</span><span class="sxs-lookup"><span data-stu-id="93f26-755">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="93f26-756">Il s’agit de la fonctionnalité’t'.</span><span class="sxs-lookup"><span data-stu-id="93f26-756">This is for 'T' functionality.</span></span>

- <span data-ttu-id="93f26-757">Mode de commande VI : `<T>`</span><span class="sxs-lookup"><span data-stu-id="93f26-757">Vi command mode: `<T>`</span></span>

### <a name="searchcharwithbackoff"></a><span data-ttu-id="93f26-758">SearchCharWithBackoff</span><span class="sxs-lookup"><span data-stu-id="93f26-758">SearchCharWithBackoff</span></span>

<span data-ttu-id="93f26-759">Lisez le caractère suivant, puis recherchez-le, à l’avenir, puis annulez un caractère.</span><span class="sxs-lookup"><span data-stu-id="93f26-759">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="93f26-760">Il s’agit de la fonctionnalité’t'.</span><span class="sxs-lookup"><span data-stu-id="93f26-760">This is for 't' functionality.</span></span>

- <span data-ttu-id="93f26-761">Mode de commande VI : `<t>`</span><span class="sxs-lookup"><span data-stu-id="93f26-761">Vi command mode: `<t>`</span></span>

### <a name="searchforward"></a><span data-ttu-id="93f26-762">SearchForward</span><span class="sxs-lookup"><span data-stu-id="93f26-762">SearchForward</span></span>

<span data-ttu-id="93f26-763">Demande une chaîne de recherche et lance la recherche sur AcceptLine.</span><span class="sxs-lookup"><span data-stu-id="93f26-763">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="93f26-764">Mode d’insertion VI : `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="93f26-764">Vi insert mode: `<Ctrl+s>`</span></span>
- <span data-ttu-id="93f26-765">Mode de commande VI : `<?>` , `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="93f26-765">Vi command mode: `<?>`, `<Ctrl+s>`</span></span>

## <a name="custom-key-bindings"></a><span data-ttu-id="93f26-766">Combinaisons de touches personnalisées</span><span class="sxs-lookup"><span data-stu-id="93f26-766">Custom Key Bindings</span></span>

<span data-ttu-id="93f26-767">PSReadLine prend en charge les combinaisons de touches personnalisées à l’aide de l’applet de commande `Set-PSReadLineKeyHandler` .</span><span class="sxs-lookup"><span data-stu-id="93f26-767">PSReadLine supports custom key bindings using the cmdlet `Set-PSReadLineKeyHandler`.</span></span> <span data-ttu-id="93f26-768">La plupart des combinaisons de touches personnalisées appellent l’une des fonctions ci-dessus, par exemple</span><span class="sxs-lookup"><span data-stu-id="93f26-768">Most custom key bindings call one of the above functions, for example</span></span>

```powershell
Set-PSReadLineKeyHandler -Key UpArrow -Function HistorySearchBackward
```

<span data-ttu-id="93f26-769">Vous pouvez lier un ScriptBlock à une clé.</span><span class="sxs-lookup"><span data-stu-id="93f26-769">You can bind a ScriptBlock to a key.</span></span> <span data-ttu-id="93f26-770">Le ScriptBlock peut faire à peu près tout ce que vous voulez.</span><span class="sxs-lookup"><span data-stu-id="93f26-770">The ScriptBlock can do pretty much anything you want.</span></span> <span data-ttu-id="93f26-771">Voici quelques exemples utiles :</span><span class="sxs-lookup"><span data-stu-id="93f26-771">Some useful examples include</span></span>

- <span data-ttu-id="93f26-772">modifier la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="93f26-772">edit the command line</span></span>
- <span data-ttu-id="93f26-773">ouverture d’une nouvelle fenêtre (par exemple, aide)</span><span class="sxs-lookup"><span data-stu-id="93f26-773">opening a new window (e.g. help)</span></span>
- <span data-ttu-id="93f26-774">modifier les répertoires sans modifier la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="93f26-774">change directories without changing the command line</span></span>

<span data-ttu-id="93f26-775">Le ScriptBlock reçoit deux arguments :</span><span class="sxs-lookup"><span data-stu-id="93f26-775">The ScriptBlock receives two arguments:</span></span>

- <span data-ttu-id="93f26-776">`$key` -Objet **[ConsoleKeyInfo]** qui est la clé qui a déclenché la liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="93f26-776">`$key` - A **[ConsoleKeyInfo]** object that is the key that triggered the custom binding.</span></span> <span data-ttu-id="93f26-777">Si vous liez le même ScriptBlock à plusieurs clés et que vous devez effectuer des actions différentes en fonction de la clé, vous pouvez vérifier $key.</span><span class="sxs-lookup"><span data-stu-id="93f26-777">If you bind the same ScriptBlock to multiple keys and need to perform different actions depending on the key, you can check $key.</span></span> <span data-ttu-id="93f26-778">De nombreuses liaisons personnalisées ignorent cet argument.</span><span class="sxs-lookup"><span data-stu-id="93f26-778">Many custom bindings ignore this argument.</span></span>

- <span data-ttu-id="93f26-779">`$arg` : Argument arbitraire.</span><span class="sxs-lookup"><span data-stu-id="93f26-779">`$arg` - An arbitrary argument.</span></span> <span data-ttu-id="93f26-780">Le plus souvent, il s’agit d’un argument entier que l’utilisateur passe à partir des combinaisons de touches DigitArgument.</span><span class="sxs-lookup"><span data-stu-id="93f26-780">Most often, this would be an integer argument that the user passes from the key bindings DigitArgument.</span></span> <span data-ttu-id="93f26-781">Si votre liaison n’accepte pas d’arguments, il est raisonnable d’ignorer cet argument.</span><span class="sxs-lookup"><span data-stu-id="93f26-781">If your binding doesn't accept arguments, it's reasonable to ignore this argument.</span></span>

<span data-ttu-id="93f26-782">Jetons un coup d’œil à un exemple qui ajoute une ligne de commande à l’historique sans l’exécuter.</span><span class="sxs-lookup"><span data-stu-id="93f26-782">Let's take a look at an example that adds a command line to history without executing it.</span></span> <span data-ttu-id="93f26-783">Cela est utile lorsque vous vous rendez compte que vous avez oublié d’effectuer une opération, mais que vous ne voulez pas entrer à nouveau la ligne de commande que vous avez déjà entrée.</span><span class="sxs-lookup"><span data-stu-id="93f26-783">This is useful when you realize you forgot to do something, but don't want to re-enter the command line you've already entered.</span></span>

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

<span data-ttu-id="93f26-784">Vous pouvez voir beaucoup plus d’exemples dans le fichier `SamplePSReadLineProfile.ps1` qui est installé dans le dossier du module PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="93f26-784">You can see many more examples in the file `SamplePSReadLineProfile.ps1` which is installed in the PSReadLine module folder.</span></span>

<span data-ttu-id="93f26-785">La plupart des combinaisons de touches utilisent des fonctions d’assistance pour la modification de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="93f26-785">Most key bindings use some helper functions for editing the command line.</span></span>
<span data-ttu-id="93f26-786">Ces API sont documentées dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="93f26-786">Those APIs are documented in the next section.</span></span>

## <a name="custom-key-binding-support-apis"></a><span data-ttu-id="93f26-787">API de prise en charge de la liaison de clé personnalisée</span><span class="sxs-lookup"><span data-stu-id="93f26-787">Custom Key Binding Support APIs</span></span>

<span data-ttu-id="93f26-788">Les fonctions suivantes sont publiques dans Microsoft. PowerShell. PSConsoleReadLine, mais ne peuvent pas être directement liées à une clé.</span><span class="sxs-lookup"><span data-stu-id="93f26-788">The following functions are public in Microsoft.PowerShell.PSConsoleReadLine, but cannot be directly bound to a key.</span></span> <span data-ttu-id="93f26-789">La plupart sont utiles dans les combinaisons de touches personnalisées.</span><span class="sxs-lookup"><span data-stu-id="93f26-789">Most are useful in custom key bindings.</span></span>

```csharp
void AddToHistory(string command)
```

<span data-ttu-id="93f26-790">Ajoutez une ligne de commande à l’historique sans l’exécuter.</span><span class="sxs-lookup"><span data-stu-id="93f26-790">Add a command line to history without executing it.</span></span>

```csharp
void ClearKillRing()
```

<span data-ttu-id="93f26-791">Effacez le point d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="93f26-791">Clear the kill-ring.</span></span>  <span data-ttu-id="93f26-792">Cela est principalement utilisé pour les tests.</span><span class="sxs-lookup"><span data-stu-id="93f26-792">This is mostly used for testing.</span></span>

```csharp
void Delete(int start, int length)
```

<span data-ttu-id="93f26-793">Supprimer les caractères de longueur du début.</span><span class="sxs-lookup"><span data-stu-id="93f26-793">Delete length characters from start.</span></span>  <span data-ttu-id="93f26-794">Cette opération prend en charge les opérations d’annulation et de rétablissement.</span><span class="sxs-lookup"><span data-stu-id="93f26-794">This operation supports undo/redo.</span></span>

```csharp
void Ding()
```

<span data-ttu-id="93f26-795">Effectuez l’action Ding en fonction des préférences de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="93f26-795">Perform the Ding action based on the users preference.</span></span>

```csharp
void GetBufferState([ref] string input, [ref] int cursor)
void GetBufferState([ref] Ast ast, [ref] Token[] tokens,
  [ref] ParseError[] parseErrors, [ref] int cursor)
```

<span data-ttu-id="93f26-796">Ces deux fonctions récupèrent des informations utiles sur l’état actuel de la mémoire tampon d’entrée.</span><span class="sxs-lookup"><span data-stu-id="93f26-796">These two functions retrieve useful information about the current state of the input buffer.</span></span>  <span data-ttu-id="93f26-797">La première est plus couramment utilisée dans les cas simples.</span><span class="sxs-lookup"><span data-stu-id="93f26-797">The first is more commonly used for simple cases.</span></span>  <span data-ttu-id="93f26-798">Le second est utilisé si votre liaison fait une opération plus avancée avec l’AST.</span><span class="sxs-lookup"><span data-stu-id="93f26-798">The second is used if your binding is doing something more advanced with the Ast.</span></span>

```csharp
IEnumerable[Microsoft.PowerShell.KeyHandler]
  GetKeyHandlers(bool includeBound, bool includeUnbound)

```

<span data-ttu-id="93f26-799">Cette fonction est utilisée par Get-PSReadLineKeyHandler et n’est probablement pas utile dans une combinaison de touches personnalisée.</span><span class="sxs-lookup"><span data-stu-id="93f26-799">This function is used by Get-PSReadLineKeyHandler and probably isn't useful in a custom key binding.</span></span>

```csharp
Microsoft.PowerShell.PSConsoleReadLineOptions GetOptions()
```

<span data-ttu-id="93f26-800">Cette fonction est utilisée par Get-PSReadLineOption et n’est probablement pas trop utile dans une liaison de clé personnalisée.</span><span class="sxs-lookup"><span data-stu-id="93f26-800">This function is used by Get-PSReadLineOption and probably isn't too useful in a custom key binding.</span></span>

```csharp
void GetSelectionState([ref] int start, [ref] int length)
```

<span data-ttu-id="93f26-801">Si aucune sélection n’est effectuée sur la ligne de commande,-1 est retourné à la fois en début et en longueur.</span><span class="sxs-lookup"><span data-stu-id="93f26-801">If there is no selection on the command line, -1 will be returned in both start and length.</span></span> <span data-ttu-id="93f26-802">Si une sélection est effectuée sur la ligne de commande, le début et la longueur de la sélection sont retournés.</span><span class="sxs-lookup"><span data-stu-id="93f26-802">If there is a selection on the command line, the start and length of the selection are returned.</span></span>

```csharp
void Insert(char c)
void Insert(string s)
```

<span data-ttu-id="93f26-803">Insérez un caractère ou une chaîne au niveau du curseur.</span><span class="sxs-lookup"><span data-stu-id="93f26-803">Insert a character or string at the cursor.</span></span>  <span data-ttu-id="93f26-804">Cette opération prend en charge les opérations d’annulation et de rétablissement.</span><span class="sxs-lookup"><span data-stu-id="93f26-804">This operation supports undo/redo.</span></span>

```csharp
string ReadLine(runspace remoteRunspace,
  System.Management.Automation.EngineIntrinsics engineIntrinsics)
```

<span data-ttu-id="93f26-805">Il s’agit du point d’entrée principal de PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="93f26-805">This is the main entry point to PSReadLine.</span></span> <span data-ttu-id="93f26-806">Comme il ne prend pas en charge la récursivité, il n’est pas utile dans une liaison de clé personnalisée.</span><span class="sxs-lookup"><span data-stu-id="93f26-806">It does not support recursion, so is not useful in a custom key binding.</span></span>

```csharp
void RemoveKeyHandler(string[] key)
```

<span data-ttu-id="93f26-807">Cette fonction est utilisée par Remove-PSReadLineKeyHandler et n’est probablement pas trop utile dans une liaison de clé personnalisée.</span><span class="sxs-lookup"><span data-stu-id="93f26-807">This function is used by Remove-PSReadLineKeyHandler and probably isn't too useful in a custom key binding.</span></span>

```csharp
void Replace(int start, int length, string replacement)
```

<span data-ttu-id="93f26-808">Remplacez une partie de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="93f26-808">Replace some of the input.</span></span> <span data-ttu-id="93f26-809">Cette opération prend en charge les opérations d’annulation et de rétablissement.</span><span class="sxs-lookup"><span data-stu-id="93f26-809">This operation supports undo/redo.</span></span> <span data-ttu-id="93f26-810">C’est préférable à Delete, suivi de Insert, car il est traité comme une action unique pour Undo.</span><span class="sxs-lookup"><span data-stu-id="93f26-810">This is preferred over Delete followed by Insert because it is treated as a single action for undo.</span></span>

```csharp
void SetCursorPosition(int cursor)
```

<span data-ttu-id="93f26-811">Déplacer le curseur vers l’offset donné.</span><span class="sxs-lookup"><span data-stu-id="93f26-811">Move the cursor to the given offset.</span></span> <span data-ttu-id="93f26-812">Le déplacement du curseur n’est pas suivi pour l’annulation.</span><span class="sxs-lookup"><span data-stu-id="93f26-812">Cursor movement is not tracked for undo.</span></span>

```csharp
void SetOptions(Microsoft.PowerShell.SetPSReadLineOption options)
```

<span data-ttu-id="93f26-813">Cette fonction est une méthode d’assistance utilisée par l’applet de commande Set-PSReadLineOption, mais peut être utile pour une combinaison de touches personnalisée qui souhaite modifier temporairement un paramètre.</span><span class="sxs-lookup"><span data-stu-id="93f26-813">This function is a helper method used by the cmdlet Set-PSReadLineOption, but might be useful to a custom key binding that wants to temporarily change a setting.</span></span>

```csharp
bool TryGetArgAsInt(System.Object arg, [ref] int numericArg,
  int defaultNumericArg)
```

<span data-ttu-id="93f26-814">Cette méthode d’assistance est utilisée pour les liaisons personnalisées qui respectent DigitArgument.</span><span class="sxs-lookup"><span data-stu-id="93f26-814">This helper method is used for custom bindings that honor DigitArgument.</span></span> <span data-ttu-id="93f26-815">Un appel classique ressemble à ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="93f26-815">A typical call looks like</span></span>

```powershell
[int]$numericArg = 0
[Microsoft.PowerShell.PSConsoleReadLine]::TryGetArgAsInt($arg,
  [ref]$numericArg, 1)
```

## <a name="note"></a><span data-ttu-id="93f26-816">REMARQUE</span><span class="sxs-lookup"><span data-stu-id="93f26-816">NOTE</span></span>

### <a name="powershell-compatibility"></a><span data-ttu-id="93f26-817">COMPATIBILITÉ AVEC POWERSHELL</span><span class="sxs-lookup"><span data-stu-id="93f26-817">POWERSHELL COMPATIBILITY</span></span>

<span data-ttu-id="93f26-818">PSReadLine nécessite PowerShell 3,0, ou une version plus récente, et l’hôte de la console.</span><span class="sxs-lookup"><span data-stu-id="93f26-818">PSReadLine requires PowerShell 3.0, or newer, and the console host.</span></span> <span data-ttu-id="93f26-819">Il ne fonctionne pas dans PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="93f26-819">It does not work in PowerShell ISE.</span></span> <span data-ttu-id="93f26-820">Elle fonctionne dans la console de Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="93f26-820">It does work in the console of Visual Studio Code.</span></span>

### <a name="command-history"></a><span data-ttu-id="93f26-821">HISTORIQUE DES COMMANDES</span><span class="sxs-lookup"><span data-stu-id="93f26-821">COMMAND HISTORY</span></span>

<span data-ttu-id="93f26-822">PSReadLine gère un fichier d’historique contenant toutes les commandes et données que vous avez entrées à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="93f26-822">PSReadLine maintains a history file containing all the commands and data you have entered from the command line.</span></span> <span data-ttu-id="93f26-823">Cela peut contenir des données sensibles, y compris des mots de passe.</span><span class="sxs-lookup"><span data-stu-id="93f26-823">This may contain sensitive data including passwords.</span></span> <span data-ttu-id="93f26-824">Par exemple, si vous utilisez l’applet de commande, `ConvertTo-SecureString` le mot de passe est enregistré dans le fichier d’historique sous forme de texte brut.</span><span class="sxs-lookup"><span data-stu-id="93f26-824">For example, if you use the `ConvertTo-SecureString` cmdlet the password is logged in the history file as plain text.</span></span> <span data-ttu-id="93f26-825">Les fichiers d’historique sont un fichier nommé `$($host.Name)_history.txt` .</span><span class="sxs-lookup"><span data-stu-id="93f26-825">The history files is a file named `$($host.Name)_history.txt`.</span></span> <span data-ttu-id="93f26-826">Sur les systèmes Windows, le fichier d’historique est stocké à l’adresse `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine` .</span><span class="sxs-lookup"><span data-stu-id="93f26-826">On Windows systems the history file is stored at `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine`.</span></span> <span data-ttu-id="93f26-827">Sur les systèmes non-Windows, les fichiers d’historique sont stockés dans `$env:XDG_DATA_HOME/powershell/PSReadLine` ou `$env:HOME/.local/share/powershell/PSReadLine` .</span><span class="sxs-lookup"><span data-stu-id="93f26-827">On non-Windows systems, the history files is stored at `$env:XDG_DATA_HOME/powershell/PSReadLine` or `$env:HOME/.local/share/powershell/PSReadLine`.</span></span>

### <a name="feedback--contributing-to-psreadline"></a><span data-ttu-id="93f26-828">Commentaires & contribution à PSReadLine</span><span class="sxs-lookup"><span data-stu-id="93f26-828">FEEDBACK & CONTRIBUTING TO PSReadLine</span></span>

[<span data-ttu-id="93f26-829">PSReadLine sur GitHub</span><span class="sxs-lookup"><span data-stu-id="93f26-829">PSReadLine on GitHub</span></span>](https://github.com/PowerShell/PSReadLine)

<span data-ttu-id="93f26-830">N’hésitez pas à envoyer une demande de tirage ou à envoyer des commentaires sur la page GitHub.</span><span class="sxs-lookup"><span data-stu-id="93f26-830">Feel free to submit a pull request or submit feedback on the GitHub page.</span></span>

## <a name="see-also"></a><span data-ttu-id="93f26-831">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="93f26-831">SEE ALSO</span></span>

<span data-ttu-id="93f26-832">PSReadLine est fortement influencé par la bibliothèque GNU [ReadLine](https://tiswww.case.edu/php/chet/readline/rltop.html) .</span><span class="sxs-lookup"><span data-stu-id="93f26-832">PSReadLine is heavily influenced by the GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) library.</span></span>
