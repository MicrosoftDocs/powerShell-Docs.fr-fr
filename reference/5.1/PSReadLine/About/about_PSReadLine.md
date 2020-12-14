---
description: PSReadLine fournit une expérience d’édition de ligne de commande améliorée dans la console PowerShell.
keywords: powershell
Locale: en-US
ms.date: 11/16/2020
online version: https://docs.microsoft.com/powershell/module/psreadline/about/about_psreadline?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: À propos de PSReadLine
ms.openlocfilehash: 25fc3a9a814728057b1ebc7e721d3fba84ae72c2
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94692307"
---
# <a name="psreadline"></a><span data-ttu-id="b1b37-104">PSReadLine</span><span class="sxs-lookup"><span data-stu-id="b1b37-104">PSReadLine</span></span>

## <a name="about_psreadline"></a><span data-ttu-id="b1b37-105">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="b1b37-105">about_PSReadLine</span></span>

## <a name="short-description"></a><span data-ttu-id="b1b37-106">Description courte</span><span class="sxs-lookup"><span data-stu-id="b1b37-106">Short Description</span></span>

<span data-ttu-id="b1b37-107">PSReadLine fournit une expérience d’édition de ligne de commande améliorée dans la console PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b1b37-107">PSReadLine provides an improved command-line editing experience in the PowerShell console.</span></span>

## <a name="long-description"></a><span data-ttu-id="b1b37-108">Description longue</span><span class="sxs-lookup"><span data-stu-id="b1b37-108">Long Description</span></span>

<span data-ttu-id="b1b37-109">PSReadLine 2,0 fournit une expérience d’édition de ligne de commande puissante pour la console PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b1b37-109">PSReadLine 2.0 provides a powerful command-line editing experience for the PowerShell console.</span></span> <span data-ttu-id="b1b37-110">Elle offre les possibilités suivantes :</span><span class="sxs-lookup"><span data-stu-id="b1b37-110">It provides:</span></span>

- <span data-ttu-id="b1b37-111">Coloration de la syntaxe de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="b1b37-111">Syntax coloring of the command line</span></span>
- <span data-ttu-id="b1b37-112">Indication visuelle des erreurs de syntaxe</span><span class="sxs-lookup"><span data-stu-id="b1b37-112">A visual indication of syntax errors</span></span>
- <span data-ttu-id="b1b37-113">Une meilleure expérience multi-ligne (modification et historique)</span><span class="sxs-lookup"><span data-stu-id="b1b37-113">A better multi-line experience (both editing and history)</span></span>
- <span data-ttu-id="b1b37-114">Combinaisons de touches personnalisables</span><span class="sxs-lookup"><span data-stu-id="b1b37-114">Customizable key bindings</span></span>
- <span data-ttu-id="b1b37-115">Modes cmd et Emacs</span><span class="sxs-lookup"><span data-stu-id="b1b37-115">Cmd and Emacs modes</span></span>
- <span data-ttu-id="b1b37-116">Nombreuses options de configuration</span><span class="sxs-lookup"><span data-stu-id="b1b37-116">Many configuration options</span></span>
- <span data-ttu-id="b1b37-117">Saisie semi-automatique du style bash (facultatif en mode cmd, par défaut en mode emacs)</span><span class="sxs-lookup"><span data-stu-id="b1b37-117">Bash style completion (optional in Cmd mode, default in Emacs mode)</span></span>
- <span data-ttu-id="b1b37-118">Emacs-Yank/Kill-Ring</span><span class="sxs-lookup"><span data-stu-id="b1b37-118">Emacs yank/kill-ring</span></span>
- <span data-ttu-id="b1b37-119">Mouvement « mot » basé sur un jeton PowerShell et Kill</span><span class="sxs-lookup"><span data-stu-id="b1b37-119">PowerShell token based "word" movement and kill</span></span>

<span data-ttu-id="b1b37-120">PSReadLine nécessite PowerShell 3,0, ou une version plus récente, et l’hôte de la console.</span><span class="sxs-lookup"><span data-stu-id="b1b37-120">PSReadLine requires PowerShell 3.0, or newer, and the console host.</span></span> <span data-ttu-id="b1b37-121">Il ne fonctionne pas dans PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="b1b37-121">It does not work in PowerShell ISE.</span></span> <span data-ttu-id="b1b37-122">Elle fonctionne dans la console de Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="b1b37-122">It does work in the console of Visual Studio Code.</span></span>

<span data-ttu-id="b1b37-123">Les fonctions suivantes sont disponibles dans la classe **[Microsoft. PowerShell. PSConsoleReadLine]**.</span><span class="sxs-lookup"><span data-stu-id="b1b37-123">The following functions are available in the class **[Microsoft.PowerShell.PSConsoleReadLine]**.</span></span>

## <a name="basic-editing-functions"></a><span data-ttu-id="b1b37-124">Fonctions d’édition de base</span><span class="sxs-lookup"><span data-stu-id="b1b37-124">Basic editing functions</span></span>

### <a name="abort"></a><span data-ttu-id="b1b37-125">Abandon</span><span class="sxs-lookup"><span data-stu-id="b1b37-125">Abort</span></span>

<span data-ttu-id="b1b37-126">Annuler l’action en cours, par exemple, recherche de l’historique incrémentiel.</span><span class="sxs-lookup"><span data-stu-id="b1b37-126">Abort current action, e.g. incremental history search.</span></span>

- <span data-ttu-id="b1b37-127">Emacs- `<Ctrl+g>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-127">Emacs: `<Ctrl+g>`</span></span>

### <a name="acceptandgetnext"></a><span data-ttu-id="b1b37-128">AcceptAndGetNext</span><span class="sxs-lookup"><span data-stu-id="b1b37-128">AcceptAndGetNext</span></span>

<span data-ttu-id="b1b37-129">Tentative d’exécution de l’entrée en cours.</span><span class="sxs-lookup"><span data-stu-id="b1b37-129">Attempt to execute the current input.</span></span> <span data-ttu-id="b1b37-130">Si elle peut être exécutée (par exemple, AcceptLine), rappelez l’élément suivant de l’historique la prochaine fois que ReadLine est appelé.</span><span class="sxs-lookup"><span data-stu-id="b1b37-130">If it can be executed (like AcceptLine), then recall the next item from history the next time ReadLine is called.</span></span>

- <span data-ttu-id="b1b37-131">Emacs- `<Ctrl+o>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-131">Emacs: `<Ctrl+o>`</span></span>

### <a name="acceptline"></a><span data-ttu-id="b1b37-132">AcceptLine</span><span class="sxs-lookup"><span data-stu-id="b1b37-132">AcceptLine</span></span>

<span data-ttu-id="b1b37-133">Tentative d’exécution de l’entrée en cours.</span><span class="sxs-lookup"><span data-stu-id="b1b37-133">Attempt to execute the current input.</span></span> <span data-ttu-id="b1b37-134">Si l’entrée actuelle est incomplète (par exemple, il manque une parenthèse fermante, un crochet ou un guillemet, l’invite de continuation est affichée sur la ligne suivante et PSReadLine attend que les clés modifient l’entrée actuelle.</span><span class="sxs-lookup"><span data-stu-id="b1b37-134">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="b1b37-135">Cmd `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-135">Cmd: `<Enter>`</span></span>
- <span data-ttu-id="b1b37-136">Emacs- `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-136">Emacs: `<Enter>`</span></span>
- <span data-ttu-id="b1b37-137">Mode d’insertion VI : `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-137">Vi insert mode: `<Enter>`</span></span>

### <a name="addline"></a><span data-ttu-id="b1b37-138">AddLine</span><span class="sxs-lookup"><span data-stu-id="b1b37-138">AddLine</span></span>

<span data-ttu-id="b1b37-139">L’invite de continuation est affichée sur la ligne suivante et PSReadLine attend que les clés modifient l’entrée actuelle.</span><span class="sxs-lookup"><span data-stu-id="b1b37-139">The continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span> <span data-ttu-id="b1b37-140">Cela est utile pour entrer une entrée multiligne sous la forme d’une commande unique, même lorsqu’une seule ligne est complète en entrée.</span><span class="sxs-lookup"><span data-stu-id="b1b37-140">This is useful to enter multi-line input as a single command even when a single line is complete input by itself.</span></span>

- <span data-ttu-id="b1b37-141">Cmd `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-141">Cmd: `<Shift+Enter>`</span></span>
- <span data-ttu-id="b1b37-142">Emacs- `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-142">Emacs: `<Shift+Enter>`</span></span>
- <span data-ttu-id="b1b37-143">Mode d’insertion VI : `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-143">Vi insert mode: `<Shift+Enter>`</span></span>
- <span data-ttu-id="b1b37-144">Mode de commande VI : `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-144">Vi command mode: `<Shift+Enter>`</span></span>

### <a name="backwarddeletechar"></a><span data-ttu-id="b1b37-145">BackwardDeleteChar</span><span class="sxs-lookup"><span data-stu-id="b1b37-145">BackwardDeleteChar</span></span>

<span data-ttu-id="b1b37-146">Supprimez le caractère avant le curseur.</span><span class="sxs-lookup"><span data-stu-id="b1b37-146">Delete the character before the cursor.</span></span>

- <span data-ttu-id="b1b37-147">Cmd : `<Backspace>` , `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-147">Cmd: `<Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="b1b37-148">Emacs : `<Backspace>` , `<Ctrl+Backspace>` , `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-148">Emacs: `<Backspace>`, `<Ctrl+Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="b1b37-149">Mode d’insertion VI : `<Backspace>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-149">Vi insert mode: `<Backspace>`</span></span>
- <span data-ttu-id="b1b37-150">Mode de commande VI : `<X>` , `<d,h>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-150">Vi command mode: `<X>`, `<d,h>`</span></span>

### <a name="backwarddeleteline"></a><span data-ttu-id="b1b37-151">BackwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="b1b37-151">BackwardDeleteLine</span></span>

<span data-ttu-id="b1b37-152">Comme BackwardKillLine-supprime le texte du point jusqu’au début de la ligne, mais ne place pas le texte supprimé dans l’anneau d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="b1b37-152">Like BackwardKillLine - deletes text from the point to the start of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="b1b37-153">Cmd `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-153">Cmd: `<Ctrl+Home>`</span></span>
- <span data-ttu-id="b1b37-154">Mode d’insertion VI : `<Ctrl+u>` , `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-154">Vi insert mode: `<Ctrl+u>`, `<Ctrl+Home>`</span></span>
- <span data-ttu-id="b1b37-155">Mode de commande VI : `<Ctrl+u>` , `<Ctrl+Home>` , `<d,0>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-155">Vi command mode: `<Ctrl+u>`, `<Ctrl+Home>`, `<d,0>`</span></span>

### <a name="backwarddeleteword"></a><span data-ttu-id="b1b37-156">BackwardDeleteWord</span><span class="sxs-lookup"><span data-stu-id="b1b37-156">BackwardDeleteWord</span></span>

<span data-ttu-id="b1b37-157">Supprime le mot précédent.</span><span class="sxs-lookup"><span data-stu-id="b1b37-157">Deletes the previous word.</span></span>

- <span data-ttu-id="b1b37-158">Mode de commande VI : `<Ctrl+w>` , `<d,b>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-158">Vi command mode: `<Ctrl+w>`, `<d,b>`</span></span>

### <a name="backwardkillline"></a><span data-ttu-id="b1b37-159">BackwardKillLine</span><span class="sxs-lookup"><span data-stu-id="b1b37-159">BackwardKillLine</span></span>

<span data-ttu-id="b1b37-160">Effacez l’entrée à partir du début de l’entrée jusqu’au curseur.</span><span class="sxs-lookup"><span data-stu-id="b1b37-160">Clear the input from the start of the input to the cursor.</span></span> <span data-ttu-id="b1b37-161">Le texte effacé est placé dans le Kill-Ring.</span><span class="sxs-lookup"><span data-stu-id="b1b37-161">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="b1b37-162">Emacs- `<Ctrl+u>` , `<Ctrl+x,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-162">Emacs: `<Ctrl+u>`, `<Ctrl+x,Backspace>`</span></span>

### <a name="backwardkillword"></a><span data-ttu-id="b1b37-163">BackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="b1b37-163">BackwardKillWord</span></span>

<span data-ttu-id="b1b37-164">Efface l’entrée du début du mot actuel jusqu’au curseur.</span><span class="sxs-lookup"><span data-stu-id="b1b37-164">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="b1b37-165">Si le curseur se trouve entre des mots, l’entrée est effacée du début du mot précédent au curseur.</span><span class="sxs-lookup"><span data-stu-id="b1b37-165">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="b1b37-166">Le texte effacé est placé dans le Kill-Ring.</span><span class="sxs-lookup"><span data-stu-id="b1b37-166">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="b1b37-167">Cmd `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-167">Cmd: `<Ctrl+Backspace>`</span></span>
- <span data-ttu-id="b1b37-168">Emacs- `<Alt+Backspace>` , `<Escape,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-168">Emacs: `<Alt+Backspace>`, `<Escape,Backspace>`</span></span>
- <span data-ttu-id="b1b37-169">Mode d’insertion VI : `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-169">Vi insert mode: `<Ctrl+Backspace>`</span></span>
- <span data-ttu-id="b1b37-170">Mode de commande VI : `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-170">Vi command mode: `<Ctrl+Backspace>`</span></span>

### <a name="cancelline"></a><span data-ttu-id="b1b37-171">CancelLine</span><span class="sxs-lookup"><span data-stu-id="b1b37-171">CancelLine</span></span>

<span data-ttu-id="b1b37-172">Annule l’entrée actuelle, en laissant l’entrée à l’écran, mais retourne à l’hôte afin que l’invite soit de nouveau évaluée.</span><span class="sxs-lookup"><span data-stu-id="b1b37-172">Cancel the current input, leaving the input on the screen, but returns back to the host so the prompt is evaluated again.</span></span>

- <span data-ttu-id="b1b37-173">Mode d’insertion VI : `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-173">Vi insert mode: `<Ctrl+c>`</span></span>
- <span data-ttu-id="b1b37-174">Mode de commande VI : `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-174">Vi command mode: `<Ctrl+c>`</span></span>

### <a name="copy"></a><span data-ttu-id="b1b37-175">Copier</span><span class="sxs-lookup"><span data-stu-id="b1b37-175">Copy</span></span>

<span data-ttu-id="b1b37-176">Copier la région sélectionnée dans le presse-papiers du système.</span><span class="sxs-lookup"><span data-stu-id="b1b37-176">Copy selected region to the system clipboard.</span></span> <span data-ttu-id="b1b37-177">Si aucune région n’est sélectionnée, copiez la ligne entière.</span><span class="sxs-lookup"><span data-stu-id="b1b37-177">If no region is selected, copy the whole line.</span></span>

- <span data-ttu-id="b1b37-178">Cmd `<Ctrl+C>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-178">Cmd: `<Ctrl+C>`</span></span>

### <a name="copyorcancelline"></a><span data-ttu-id="b1b37-179">CopyOrCancelLine</span><span class="sxs-lookup"><span data-stu-id="b1b37-179">CopyOrCancelLine</span></span>

<span data-ttu-id="b1b37-180">Si le texte est sélectionné, copiez-le dans le presse-papiers, sinon, annulez la ligne.</span><span class="sxs-lookup"><span data-stu-id="b1b37-180">If text is selected, copy to the clipboard, otherwise cancel the line.</span></span>

- <span data-ttu-id="b1b37-181">Cmd `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-181">Cmd: `<Ctrl+c>`</span></span>
- <span data-ttu-id="b1b37-182">Emacs- `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-182">Emacs: `<Ctrl+c>`</span></span>

### <a name="cut"></a><span data-ttu-id="b1b37-183">Couper</span><span class="sxs-lookup"><span data-stu-id="b1b37-183">Cut</span></span>

<span data-ttu-id="b1b37-184">Supprimer la zone sélectionnée en plaçant le texte supprimé dans le presse-papiers du système.</span><span class="sxs-lookup"><span data-stu-id="b1b37-184">Delete selected region placing deleted text in the system clipboard.</span></span>

- <span data-ttu-id="b1b37-185">Cmd `<Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-185">Cmd: `<Ctrl+x>`</span></span>

### <a name="deletechar"></a><span data-ttu-id="b1b37-186">DeleteChar</span><span class="sxs-lookup"><span data-stu-id="b1b37-186">DeleteChar</span></span>

<span data-ttu-id="b1b37-187">Supprimez le caractère sous le curseur.</span><span class="sxs-lookup"><span data-stu-id="b1b37-187">Delete the character under the cursor.</span></span>

- <span data-ttu-id="b1b37-188">Cmd `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-188">Cmd: `<Delete>`</span></span>
- <span data-ttu-id="b1b37-189">Emacs- `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-189">Emacs: `<Delete>`</span></span>
- <span data-ttu-id="b1b37-190">Mode d’insertion VI : `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-190">Vi insert mode: `<Delete>`</span></span>
- <span data-ttu-id="b1b37-191">Mode de commande VI : `<Delete>` , `<x>` , `<d,l>` , `<d,Space>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-191">Vi command mode: `<Delete>`, `<x>`, `<d,l>`, `<d,Space>`</span></span>

### <a name="deletecharorexit"></a><span data-ttu-id="b1b37-192">DeleteCharOrExit</span><span class="sxs-lookup"><span data-stu-id="b1b37-192">DeleteCharOrExit</span></span>

<span data-ttu-id="b1b37-193">Supprimez le caractère sous le curseur, ou si la ligne est vide, quittez le processus.</span><span class="sxs-lookup"><span data-stu-id="b1b37-193">Delete the character under the cursor, or if the line is empty, exit the process.</span></span>

- <span data-ttu-id="b1b37-194">Emacs- `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-194">Emacs: `<Ctrl+d>`</span></span>

### <a name="deleteendofword"></a><span data-ttu-id="b1b37-195">DeleteEndOfWord</span><span class="sxs-lookup"><span data-stu-id="b1b37-195">DeleteEndOfWord</span></span>

<span data-ttu-id="b1b37-196">Supprimer à la fin du mot.</span><span class="sxs-lookup"><span data-stu-id="b1b37-196">Delete to the end of the word.</span></span>

- <span data-ttu-id="b1b37-197">Mode de commande VI : `<d,e>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-197">Vi command mode: `<d,e>`</span></span>

### <a name="deleteline"></a><span data-ttu-id="b1b37-198">DeleteLine</span><span class="sxs-lookup"><span data-stu-id="b1b37-198">DeleteLine</span></span>

<span data-ttu-id="b1b37-199">Supprime la ligne active, en activant l’annulation.</span><span class="sxs-lookup"><span data-stu-id="b1b37-199">Deletes the current line, enabling undo.</span></span>

- <span data-ttu-id="b1b37-200">Mode de commande VI : `<d,d>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-200">Vi command mode: `<d,d>`</span></span>

### <a name="deletelinetofirstchar"></a><span data-ttu-id="b1b37-201">DeleteLineToFirstChar</span><span class="sxs-lookup"><span data-stu-id="b1b37-201">DeleteLineToFirstChar</span></span>

<span data-ttu-id="b1b37-202">Supprime le texte du curseur jusqu’au premier caractère non vide de la ligne.</span><span class="sxs-lookup"><span data-stu-id="b1b37-202">Deletes text from the cursor to the first non-blank character of the line.</span></span>

- <span data-ttu-id="b1b37-203">Mode de commande VI : `<d,^>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-203">Vi command mode: `<d,^>`</span></span>

### <a name="deletetoend"></a><span data-ttu-id="b1b37-204">DeleteToEnd</span><span class="sxs-lookup"><span data-stu-id="b1b37-204">DeleteToEnd</span></span>

<span data-ttu-id="b1b37-205">Supprimer à la fin de la ligne.</span><span class="sxs-lookup"><span data-stu-id="b1b37-205">Delete to the end of the line.</span></span>

- <span data-ttu-id="b1b37-206">Mode de commande VI : `<D>` , `<d,$>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-206">Vi command mode: `<D>`, `<d,$>`</span></span>

### <a name="deleteword"></a><span data-ttu-id="b1b37-207">DeleteWord</span><span class="sxs-lookup"><span data-stu-id="b1b37-207">DeleteWord</span></span>

<span data-ttu-id="b1b37-208">Supprimer le mot suivant.</span><span class="sxs-lookup"><span data-stu-id="b1b37-208">Delete the next word.</span></span>

- <span data-ttu-id="b1b37-209">Mode de commande VI : `<d,w>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-209">Vi command mode: `<d,w>`</span></span>

### <a name="forwarddeleteline"></a><span data-ttu-id="b1b37-210">ForwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="b1b37-210">ForwardDeleteLine</span></span>

<span data-ttu-id="b1b37-211">Comme ForwardKillLine-supprime le texte du point jusqu’à la fin de la ligne, mais ne place pas le texte supprimé dans l’anneau Kill.</span><span class="sxs-lookup"><span data-stu-id="b1b37-211">Like ForwardKillLine - deletes text from the point to the end of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="b1b37-212">Cmd `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-212">Cmd: `<Ctrl+End>`</span></span>
- <span data-ttu-id="b1b37-213">Mode d’insertion VI : `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-213">Vi insert mode: `<Ctrl+End>`</span></span>
- <span data-ttu-id="b1b37-214">Mode de commande VI : `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-214">Vi command mode: `<Ctrl+End>`</span></span>

### <a name="insertlineabove"></a><span data-ttu-id="b1b37-215">InsertLineAbove</span><span class="sxs-lookup"><span data-stu-id="b1b37-215">InsertLineAbove</span></span>

<span data-ttu-id="b1b37-216">Une nouvelle ligne vide est créée au-dessus de la ligne active, quel que soit l’endroit où se trouve le curseur sur la ligne active.</span><span class="sxs-lookup"><span data-stu-id="b1b37-216">A new empty line is created above the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="b1b37-217">Le curseur se déplace au début de la nouvelle ligne.</span><span class="sxs-lookup"><span data-stu-id="b1b37-217">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="b1b37-218">Cmd `<Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-218">Cmd: `<Ctrl+Enter>`</span></span>

### <a name="insertlinebelow"></a><span data-ttu-id="b1b37-219">InsertLineBelow</span><span class="sxs-lookup"><span data-stu-id="b1b37-219">InsertLineBelow</span></span>

<span data-ttu-id="b1b37-220">Une nouvelle ligne vide est créée sous la ligne active, quel que soit l’endroit où se trouve le curseur sur la ligne active.</span><span class="sxs-lookup"><span data-stu-id="b1b37-220">A new empty line is created below the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="b1b37-221">Le curseur se déplace au début de la nouvelle ligne.</span><span class="sxs-lookup"><span data-stu-id="b1b37-221">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="b1b37-222">Cmd `<Shift+Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-222">Cmd: `<Shift+Ctrl+Enter>`</span></span>

### <a name="invertcase"></a><span data-ttu-id="b1b37-223">InvertCase</span><span class="sxs-lookup"><span data-stu-id="b1b37-223">InvertCase</span></span>

<span data-ttu-id="b1b37-224">Inverser la casse du caractère actuel et passer au suivant.</span><span class="sxs-lookup"><span data-stu-id="b1b37-224">Invert the case of the current character and move to the next one.</span></span>

- <span data-ttu-id="b1b37-225">Mode de commande VI : `<~>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-225">Vi command mode: `<~>`</span></span>

### <a name="killline"></a><span data-ttu-id="b1b37-226">KillLine</span><span class="sxs-lookup"><span data-stu-id="b1b37-226">KillLine</span></span>

<span data-ttu-id="b1b37-227">Effacez l’entrée du curseur jusqu’à la fin de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="b1b37-227">Clear the input from the cursor to the end of the input.</span></span> <span data-ttu-id="b1b37-228">Le texte effacé est placé dans le Kill-Ring.</span><span class="sxs-lookup"><span data-stu-id="b1b37-228">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="b1b37-229">Emacs- `<Ctrl+k>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-229">Emacs: `<Ctrl+k>`</span></span>

### <a name="killregion"></a><span data-ttu-id="b1b37-230">KillRegion</span><span class="sxs-lookup"><span data-stu-id="b1b37-230">KillRegion</span></span>

<span data-ttu-id="b1b37-231">Supprimer le texte situé entre le curseur et la marque.</span><span class="sxs-lookup"><span data-stu-id="b1b37-231">Kill the text between the cursor and the mark.</span></span>

- <span data-ttu-id="b1b37-232">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="b1b37-232">Function is unbound.</span></span>

### <a name="killword"></a><span data-ttu-id="b1b37-233">KillWord</span><span class="sxs-lookup"><span data-stu-id="b1b37-233">KillWord</span></span>

<span data-ttu-id="b1b37-234">Efface l’entrée du curseur jusqu’à la fin du mot actuel.</span><span class="sxs-lookup"><span data-stu-id="b1b37-234">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="b1b37-235">Si le curseur se trouve entre des mots, l’entrée est effacée du curseur jusqu’à la fin du mot suivant.</span><span class="sxs-lookup"><span data-stu-id="b1b37-235">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="b1b37-236">Le texte effacé est placé dans le Kill-Ring.</span><span class="sxs-lookup"><span data-stu-id="b1b37-236">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="b1b37-237">Cmd `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-237">Cmd: `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="b1b37-238">Emacs- `<Alt+d>` , `<Escape,d>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-238">Emacs: `<Alt+d>`, `<Escape,d>`</span></span>
- <span data-ttu-id="b1b37-239">Mode d’insertion VI : `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-239">Vi insert mode: `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="b1b37-240">Mode de commande VI : `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-240">Vi command mode: `<Ctrl+Delete>`</span></span>

### <a name="paste"></a><span data-ttu-id="b1b37-241">Coller</span><span class="sxs-lookup"><span data-stu-id="b1b37-241">Paste</span></span>

<span data-ttu-id="b1b37-242">Collez le texte à partir du presse-papiers du système.</span><span class="sxs-lookup"><span data-stu-id="b1b37-242">Paste text from the system clipboard.</span></span>

- <span data-ttu-id="b1b37-243">Cmd : `<Ctrl+v>` , `<Shift+Insert>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-243">Cmd: `<Ctrl+v>`, `<Shift+Insert>`</span></span>
- <span data-ttu-id="b1b37-244">Mode d’insertion VI : `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-244">Vi insert mode: `<Ctrl+v>`</span></span>
- <span data-ttu-id="b1b37-245">Mode de commande VI : `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-245">Vi command mode: `<Ctrl+v>`</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b1b37-246">Lors de l’utilisation de la fonction **Paste** , le contenu entier de la mémoire tampon du presse-papiers est collé dans la mémoire tampon d’entrée de PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="b1b37-246">When using the **Paste** function, the entire contents of the clipboard buffer is pasted into the input buffer of PSReadLine.</span></span> <span data-ttu-id="b1b37-247">La mémoire tampon d’entrée est ensuite transmise à l’analyseur PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b1b37-247">The input buffer is then passed to the PowerShell parser.</span></span> <span data-ttu-id="b1b37-248">L’entrée collée à l’aide de la méthode de collage **avec le bouton droit** de la console de l’application de console est copiée dans la mémoire tampon d’entrée un caractère à la fois.</span><span class="sxs-lookup"><span data-stu-id="b1b37-248">Input pasted using the console application's **right-click** paste method is copied to the input buffer one character at a time.</span></span> <span data-ttu-id="b1b37-249">La mémoire tampon d’entrée est transmise à l’analyseur lorsqu’un caractère de saut de ligne est copié.</span><span class="sxs-lookup"><span data-stu-id="b1b37-249">The input buffer is passed to the parser when a newline character is copied.</span></span> <span data-ttu-id="b1b37-250">Par conséquent, l’entrée est analysée une ligne à la fois.</span><span class="sxs-lookup"><span data-stu-id="b1b37-250">Therefore, the input is parsed one line at a time.</span></span> <span data-ttu-id="b1b37-251">La différence entre les méthodes de collage entraîne un comportement d’exécution différent.</span><span class="sxs-lookup"><span data-stu-id="b1b37-251">The difference between paste methods results in different execution behavior.</span></span>

### <a name="pasteafter"></a><span data-ttu-id="b1b37-252">PasteAfter</span><span class="sxs-lookup"><span data-stu-id="b1b37-252">PasteAfter</span></span>

<span data-ttu-id="b1b37-253">Collez le presse-papiers après le curseur, en déplaçant le curseur à la fin du texte collé.</span><span class="sxs-lookup"><span data-stu-id="b1b37-253">Paste the clipboard after the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="b1b37-254">Mode de commande VI : `<p>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-254">Vi command mode: `<p>`</span></span>

### <a name="pastebefore"></a><span data-ttu-id="b1b37-255">PasteBefore</span><span class="sxs-lookup"><span data-stu-id="b1b37-255">PasteBefore</span></span>

<span data-ttu-id="b1b37-256">Collez le presse-papiers avant le curseur, en déplaçant le curseur à la fin du texte collé.</span><span class="sxs-lookup"><span data-stu-id="b1b37-256">Paste the clipboard before the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="b1b37-257">Mode de commande VI : `<P>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-257">Vi command mode: `<P>`</span></span>

### <a name="prependandaccept"></a><span data-ttu-id="b1b37-258">PrependAndAccept</span><span class="sxs-lookup"><span data-stu-id="b1b37-258">PrependAndAccept</span></span>

<span data-ttu-id="b1b37-259">Faites précéder un' # 'et acceptez la ligne.</span><span class="sxs-lookup"><span data-stu-id="b1b37-259">Prepend a '#' and accept the line.</span></span>

- <span data-ttu-id="b1b37-260">Mode de commande VI : `<#>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-260">Vi command mode: `<#>`</span></span>

### <a name="redo"></a><span data-ttu-id="b1b37-261">Rétablir</span><span class="sxs-lookup"><span data-stu-id="b1b37-261">Redo</span></span>

<span data-ttu-id="b1b37-262">Annule une annulation.</span><span class="sxs-lookup"><span data-stu-id="b1b37-262">Undo an undo.</span></span>

- <span data-ttu-id="b1b37-263">Cmd `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-263">Cmd: `<Ctrl+y>`</span></span>
- <span data-ttu-id="b1b37-264">Mode d’insertion VI : `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-264">Vi insert mode: `<Ctrl+y>`</span></span>
- <span data-ttu-id="b1b37-265">Mode de commande VI : `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-265">Vi command mode: `<Ctrl+y>`</span></span>

### <a name="repeatlastcommand"></a><span data-ttu-id="b1b37-266">RepeatLastCommand</span><span class="sxs-lookup"><span data-stu-id="b1b37-266">RepeatLastCommand</span></span>

<span data-ttu-id="b1b37-267">Répète la dernière modification de texte.</span><span class="sxs-lookup"><span data-stu-id="b1b37-267">Repeat the last text modification.</span></span>

- <span data-ttu-id="b1b37-268">Mode de commande VI : `<.>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-268">Vi command mode: `<.>`</span></span>

### <a name="revertline"></a><span data-ttu-id="b1b37-269">RevertLine</span><span class="sxs-lookup"><span data-stu-id="b1b37-269">RevertLine</span></span>

<span data-ttu-id="b1b37-270">Rétablit toutes les entrées de l’entrée actuelle.</span><span class="sxs-lookup"><span data-stu-id="b1b37-270">Reverts all of the input to the current input.</span></span>

- <span data-ttu-id="b1b37-271">Cmd `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-271">Cmd: `<Escape>`</span></span>
- <span data-ttu-id="b1b37-272">Emacs- `<Alt+r>` , `<Escape,r>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-272">Emacs: `<Alt+r>`, `<Escape,r>`</span></span>

### <a name="shellbackwardkillword"></a><span data-ttu-id="b1b37-273">ShellBackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="b1b37-273">ShellBackwardKillWord</span></span>

<span data-ttu-id="b1b37-274">Efface l’entrée du début du mot actuel jusqu’au curseur.</span><span class="sxs-lookup"><span data-stu-id="b1b37-274">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="b1b37-275">Si le curseur se trouve entre des mots, l’entrée est effacée du début du mot précédent au curseur.</span><span class="sxs-lookup"><span data-stu-id="b1b37-275">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="b1b37-276">Le texte effacé est placé dans le Kill-Ring.</span><span class="sxs-lookup"><span data-stu-id="b1b37-276">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="b1b37-277">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="b1b37-277">Function is unbound.</span></span>

### <a name="shellkillword"></a><span data-ttu-id="b1b37-278">ShellKillWord</span><span class="sxs-lookup"><span data-stu-id="b1b37-278">ShellKillWord</span></span>

<span data-ttu-id="b1b37-279">Efface l’entrée du curseur jusqu’à la fin du mot actuel.</span><span class="sxs-lookup"><span data-stu-id="b1b37-279">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="b1b37-280">Si le curseur se trouve entre des mots, l’entrée est effacée du curseur jusqu’à la fin du mot suivant.</span><span class="sxs-lookup"><span data-stu-id="b1b37-280">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="b1b37-281">Le texte effacé est placé dans le Kill-Ring.</span><span class="sxs-lookup"><span data-stu-id="b1b37-281">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="b1b37-282">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="b1b37-282">Function is unbound.</span></span>

### <a name="swapcharacters"></a><span data-ttu-id="b1b37-283">SwapCharacters</span><span class="sxs-lookup"><span data-stu-id="b1b37-283">SwapCharacters</span></span>

<span data-ttu-id="b1b37-284">Permuter le caractère actuel et celui qui le précèdent.</span><span class="sxs-lookup"><span data-stu-id="b1b37-284">Swap the current character and the one before it.</span></span>

- <span data-ttu-id="b1b37-285">Emacs- `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-285">Emacs: `<Ctrl+t>`</span></span>
- <span data-ttu-id="b1b37-286">Mode d’insertion VI : `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-286">Vi insert mode: `<Ctrl+t>`</span></span>
- <span data-ttu-id="b1b37-287">Mode de commande VI : `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-287">Vi command mode: `<Ctrl+t>`</span></span>

### <a name="undo"></a><span data-ttu-id="b1b37-288">Annuler</span><span class="sxs-lookup"><span data-stu-id="b1b37-288">Undo</span></span>

<span data-ttu-id="b1b37-289">Annuler une modification précédente.</span><span class="sxs-lookup"><span data-stu-id="b1b37-289">Undo a previous edit.</span></span>

- <span data-ttu-id="b1b37-290">Cmd `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-290">Cmd: `<Ctrl+z>`</span></span>
- <span data-ttu-id="b1b37-291">Emacs- `<Ctrl+_>` , `<Ctrl+x,Ctrl+u>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-291">Emacs: `<Ctrl+_>`, `<Ctrl+x,Ctrl+u>`</span></span>
- <span data-ttu-id="b1b37-292">Mode d’insertion VI : `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-292">Vi insert mode: `<Ctrl+z>`</span></span>
- <span data-ttu-id="b1b37-293">Mode de commande VI : `<Ctrl+z>` , `<u>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-293">Vi command mode: `<Ctrl+z>`, `<u>`</span></span>

### <a name="undoall"></a><span data-ttu-id="b1b37-294">UndoAll</span><span class="sxs-lookup"><span data-stu-id="b1b37-294">UndoAll</span></span>

<span data-ttu-id="b1b37-295">Annule toutes les modifications précédentes pour la ligne.</span><span class="sxs-lookup"><span data-stu-id="b1b37-295">Undo all previous edits for line.</span></span>

- <span data-ttu-id="b1b37-296">Mode de commande VI : `<U>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-296">Vi command mode: `<U>`</span></span>

### <a name="unixwordrubout"></a><span data-ttu-id="b1b37-297">UnixWordRubout</span><span class="sxs-lookup"><span data-stu-id="b1b37-297">UnixWordRubout</span></span>

<span data-ttu-id="b1b37-298">Efface l’entrée du début du mot actuel jusqu’au curseur.</span><span class="sxs-lookup"><span data-stu-id="b1b37-298">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="b1b37-299">Si le curseur se trouve entre des mots, l’entrée est effacée du début du mot précédent au curseur.</span><span class="sxs-lookup"><span data-stu-id="b1b37-299">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="b1b37-300">Le texte effacé est placé dans le Kill-Ring.</span><span class="sxs-lookup"><span data-stu-id="b1b37-300">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="b1b37-301">Emacs- `<Ctrl+w>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-301">Emacs: `<Ctrl+w>`</span></span>

### <a name="validateandacceptline"></a><span data-ttu-id="b1b37-302">ValidateAndAcceptLine</span><span class="sxs-lookup"><span data-stu-id="b1b37-302">ValidateAndAcceptLine</span></span>

<span data-ttu-id="b1b37-303">Tentative d’exécution de l’entrée en cours.</span><span class="sxs-lookup"><span data-stu-id="b1b37-303">Attempt to execute the current input.</span></span> <span data-ttu-id="b1b37-304">Si l’entrée actuelle est incomplète (par exemple, il manque une parenthèse fermante, un crochet ou un guillemet, l’invite de continuation est affichée sur la ligne suivante et PSReadLine attend que les clés modifient l’entrée actuelle.</span><span class="sxs-lookup"><span data-stu-id="b1b37-304">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="b1b37-305">Emacs- `<Ctrl+m>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-305">Emacs: `<Ctrl+m>`</span></span>

### <a name="viacceptline"></a><span data-ttu-id="b1b37-306">ViAcceptLine</span><span class="sxs-lookup"><span data-stu-id="b1b37-306">ViAcceptLine</span></span>

<span data-ttu-id="b1b37-307">Acceptez la ligne et passez en mode insertion.</span><span class="sxs-lookup"><span data-stu-id="b1b37-307">Accept the line and switch to Insert mode.</span></span>

- <span data-ttu-id="b1b37-308">Mode de commande VI : `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-308">Vi command mode: `<Enter>`</span></span>

### <a name="viacceptlineorexit"></a><span data-ttu-id="b1b37-309">ViAcceptLineOrExit</span><span class="sxs-lookup"><span data-stu-id="b1b37-309">ViAcceptLineOrExit</span></span>

<span data-ttu-id="b1b37-310">Comme DeleteCharOrExit en mode emacs, mais accepte la ligne au lieu de supprimer un caractère.</span><span class="sxs-lookup"><span data-stu-id="b1b37-310">Like DeleteCharOrExit in Emacs mode, but accepts the line instead of deleting a character.</span></span>

- <span data-ttu-id="b1b37-311">Mode d’insertion VI : `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-311">Vi insert mode: `<Ctrl+d>`</span></span>
- <span data-ttu-id="b1b37-312">Mode de commande VI : `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-312">Vi command mode: `<Ctrl+d>`</span></span>

### <a name="viappendline"></a><span data-ttu-id="b1b37-313">ViAppendLine</span><span class="sxs-lookup"><span data-stu-id="b1b37-313">ViAppendLine</span></span>

<span data-ttu-id="b1b37-314">Une nouvelle ligne est insérée au-dessous de la ligne active.</span><span class="sxs-lookup"><span data-stu-id="b1b37-314">A new line is inserted below the current line.</span></span>

- <span data-ttu-id="b1b37-315">Mode de commande VI : `<o>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-315">Vi command mode: `<o>`</span></span>

### <a name="vibackwarddeleteglob"></a><span data-ttu-id="b1b37-316">ViBackwardDeleteGlob</span><span class="sxs-lookup"><span data-stu-id="b1b37-316">ViBackwardDeleteGlob</span></span>

<span data-ttu-id="b1b37-317">Supprime le mot précédent, en utilisant uniquement un espace blanc comme délimiteur de mot.</span><span class="sxs-lookup"><span data-stu-id="b1b37-317">Deletes the previous word, using only white space as the word delimiter.</span></span>

- <span data-ttu-id="b1b37-318">Mode de commande VI : `<d,B>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-318">Vi command mode: `<d,B>`</span></span>

### <a name="vibackwardglob"></a><span data-ttu-id="b1b37-319">ViBackwardGlob</span><span class="sxs-lookup"><span data-stu-id="b1b37-319">ViBackwardGlob</span></span>

<span data-ttu-id="b1b37-320">Déplace le curseur au début du mot précédent, en utilisant uniquement des espaces blancs comme délimiteurs.</span><span class="sxs-lookup"><span data-stu-id="b1b37-320">Moves the cursor back to the beginning of the previous word, using only white space as delimiters.</span></span>

- <span data-ttu-id="b1b37-321">Mode de commande VI : `<B>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-321">Vi command mode: `<B>`</span></span>

### <a name="videletebrace"></a><span data-ttu-id="b1b37-322">ViDeleteBrace</span><span class="sxs-lookup"><span data-stu-id="b1b37-322">ViDeleteBrace</span></span>

<span data-ttu-id="b1b37-323">Recherchez l’accolade correspondante, la parenthèse ou le crochet, et supprimez tout le contenu dans, y compris l’accolade.</span><span class="sxs-lookup"><span data-stu-id="b1b37-323">Find the matching brace, parenthesis, or square bracket and delete all contents within, including the brace.</span></span>

- <span data-ttu-id="b1b37-324">Mode de commande VI : `<d,%>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-324">Vi command mode: `<d,%>`</span></span>

### <a name="videleteendofglob"></a><span data-ttu-id="b1b37-325">ViDeleteEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="b1b37-325">ViDeleteEndOfGlob</span></span>

<span data-ttu-id="b1b37-326">Supprimer à la fin du mot.</span><span class="sxs-lookup"><span data-stu-id="b1b37-326">Delete to the end of the word.</span></span>

- <span data-ttu-id="b1b37-327">Mode de commande VI : `<d,E>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-327">Vi command mode: `<d,E>`</span></span>

### <a name="videleteglob"></a><span data-ttu-id="b1b37-328">ViDeleteGlob</span><span class="sxs-lookup"><span data-stu-id="b1b37-328">ViDeleteGlob</span></span>

<span data-ttu-id="b1b37-329">Supprime la glob suivante (mot blanc délimité par des espaces).</span><span class="sxs-lookup"><span data-stu-id="b1b37-329">Delete the next glob (white space delimited word).</span></span>

- <span data-ttu-id="b1b37-330">Mode de commande VI : `<d,W>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-330">Vi command mode: `<d,W>`</span></span>

### <a name="videletetobeforechar"></a><span data-ttu-id="b1b37-331">ViDeleteToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="b1b37-331">ViDeleteToBeforeChar</span></span>

<span data-ttu-id="b1b37-332">Supprime jusqu’au caractère donné.</span><span class="sxs-lookup"><span data-stu-id="b1b37-332">Deletes until given character.</span></span>

- <span data-ttu-id="b1b37-333">Mode de commande VI : `<d,t>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-333">Vi command mode: `<d,t>`</span></span>

### <a name="videletetobeforecharbackward"></a><span data-ttu-id="b1b37-334">ViDeleteToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="b1b37-334">ViDeleteToBeforeCharBackward</span></span>

<span data-ttu-id="b1b37-335">Supprime jusqu’au caractère donné.</span><span class="sxs-lookup"><span data-stu-id="b1b37-335">Deletes until given character.</span></span>

- <span data-ttu-id="b1b37-336">Mode de commande VI : `<d,T>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-336">Vi command mode: `<d,T>`</span></span>

### <a name="videletetochar"></a><span data-ttu-id="b1b37-337">ViDeleteToChar</span><span class="sxs-lookup"><span data-stu-id="b1b37-337">ViDeleteToChar</span></span>

<span data-ttu-id="b1b37-338">Supprime jusqu’au caractère donné.</span><span class="sxs-lookup"><span data-stu-id="b1b37-338">Deletes until given character.</span></span>

- <span data-ttu-id="b1b37-339">Mode de commande VI : `<d,f>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-339">Vi command mode: `<d,f>`</span></span>

### <a name="videletetocharbackward"></a><span data-ttu-id="b1b37-340">ViDeleteToCharBackward</span><span class="sxs-lookup"><span data-stu-id="b1b37-340">ViDeleteToCharBackward</span></span>

<span data-ttu-id="b1b37-341">Supprime vers l’arrière jusqu’au caractère donné.</span><span class="sxs-lookup"><span data-stu-id="b1b37-341">Deletes backwards until given character.</span></span>

- <span data-ttu-id="b1b37-342">Mode de commande VI : `<d,F>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-342">Vi command mode: `<d,F>`</span></span>

### <a name="viinsertatbegining"></a><span data-ttu-id="b1b37-343">ViInsertAtBegining</span><span class="sxs-lookup"><span data-stu-id="b1b37-343">ViInsertAtBegining</span></span>

<span data-ttu-id="b1b37-344">Basculez en mode insertion et positionnez le curseur au début de la ligne.</span><span class="sxs-lookup"><span data-stu-id="b1b37-344">Switch to Insert mode and position the cursor at the beginning of the line.</span></span>

- <span data-ttu-id="b1b37-345">Mode de commande VI : `<I>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-345">Vi command mode: `<I>`</span></span>

### <a name="viinsertatend"></a><span data-ttu-id="b1b37-346">ViInsertAtEnd</span><span class="sxs-lookup"><span data-stu-id="b1b37-346">ViInsertAtEnd</span></span>

<span data-ttu-id="b1b37-347">Basculez en mode insertion et positionnez le curseur à la fin de la ligne.</span><span class="sxs-lookup"><span data-stu-id="b1b37-347">Switch to Insert mode and position the cursor at the end of the line.</span></span>

- <span data-ttu-id="b1b37-348">Mode de commande VI : `<A>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-348">Vi command mode: `<A>`</span></span>

### <a name="viinsertline"></a><span data-ttu-id="b1b37-349">ViInsertLine</span><span class="sxs-lookup"><span data-stu-id="b1b37-349">ViInsertLine</span></span>

<span data-ttu-id="b1b37-350">Une nouvelle ligne est insérée au-dessus de la ligne active.</span><span class="sxs-lookup"><span data-stu-id="b1b37-350">A new line is inserted above the current line.</span></span>

- <span data-ttu-id="b1b37-351">Mode de commande VI : `<O>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-351">Vi command mode: `<O>`</span></span>

### <a name="viinsertwithappend"></a><span data-ttu-id="b1b37-352">ViInsertWithAppend</span><span class="sxs-lookup"><span data-stu-id="b1b37-352">ViInsertWithAppend</span></span>

<span data-ttu-id="b1b37-353">Ajouter à partir de la position de la ligne active.</span><span class="sxs-lookup"><span data-stu-id="b1b37-353">Append from the current line position.</span></span>

- <span data-ttu-id="b1b37-354">Mode de commande VI : `<a>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-354">Vi command mode: `<a>`</span></span>

### <a name="viinsertwithdelete"></a><span data-ttu-id="b1b37-355">ViInsertWithDelete</span><span class="sxs-lookup"><span data-stu-id="b1b37-355">ViInsertWithDelete</span></span>

<span data-ttu-id="b1b37-356">Supprimez le caractère actuel et basculez en mode insertion.</span><span class="sxs-lookup"><span data-stu-id="b1b37-356">Delete the current character and switch to Insert mode.</span></span>

- <span data-ttu-id="b1b37-357">Mode de commande VI : `<s>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-357">Vi command mode: `<s>`</span></span>

### <a name="vijoinlines"></a><span data-ttu-id="b1b37-358">ViJoinLines</span><span class="sxs-lookup"><span data-stu-id="b1b37-358">ViJoinLines</span></span>

<span data-ttu-id="b1b37-359">Joint la ligne active et la ligne suivante.</span><span class="sxs-lookup"><span data-stu-id="b1b37-359">Joins the current line and the next line.</span></span>

- <span data-ttu-id="b1b37-360">Mode de commande VI : `<J>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-360">Vi command mode: `<J>`</span></span>

### <a name="vireplaceline"></a><span data-ttu-id="b1b37-361">ViReplaceLine</span><span class="sxs-lookup"><span data-stu-id="b1b37-361">ViReplaceLine</span></span>

<span data-ttu-id="b1b37-362">Effacez l’intégralité de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="b1b37-362">Erase the entire command line.</span></span>

- <span data-ttu-id="b1b37-363">Mode de commande VI : `<S>` , `<c,c>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-363">Vi command mode: `<S>`, `<c,c>`</span></span>

### <a name="vireplacetobeforechar"></a><span data-ttu-id="b1b37-364">ViReplaceToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="b1b37-364">ViReplaceToBeforeChar</span></span>

<span data-ttu-id="b1b37-365">Remplace jusqu’au caractère donné.</span><span class="sxs-lookup"><span data-stu-id="b1b37-365">Replaces until given character.</span></span>

- <span data-ttu-id="b1b37-366">Mode de commande VI : `<c,t>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-366">Vi command mode: `<c,t>`</span></span>

### <a name="vireplacetobeforecharbackward"></a><span data-ttu-id="b1b37-367">ViReplaceToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="b1b37-367">ViReplaceToBeforeCharBackward</span></span>

<span data-ttu-id="b1b37-368">Remplace jusqu’au caractère donné.</span><span class="sxs-lookup"><span data-stu-id="b1b37-368">Replaces until given character.</span></span>

- <span data-ttu-id="b1b37-369">Mode de commande VI : `<c,T>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-369">Vi command mode: `<c,T>`</span></span>

### <a name="vireplacetochar"></a><span data-ttu-id="b1b37-370">ViReplaceToChar</span><span class="sxs-lookup"><span data-stu-id="b1b37-370">ViReplaceToChar</span></span>

<span data-ttu-id="b1b37-371">Supprime jusqu’au caractère donné.</span><span class="sxs-lookup"><span data-stu-id="b1b37-371">Deletes until given character.</span></span>

- <span data-ttu-id="b1b37-372">Mode de commande VI : `<c,f>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-372">Vi command mode: `<c,f>`</span></span>

### <a name="vireplacetocharbackward"></a><span data-ttu-id="b1b37-373">ViReplaceToCharBackward</span><span class="sxs-lookup"><span data-stu-id="b1b37-373">ViReplaceToCharBackward</span></span>

<span data-ttu-id="b1b37-374">Remplace jusqu’au caractère donné.</span><span class="sxs-lookup"><span data-stu-id="b1b37-374">Replaces until given character.</span></span>

- <span data-ttu-id="b1b37-375">Mode de commande VI : `<c,F>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-375">Vi command mode: `<c,F>`</span></span>

### <a name="viyankbeginningofline"></a><span data-ttu-id="b1b37-376">ViYankBeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="b1b37-376">ViYankBeginningOfLine</span></span>

<span data-ttu-id="b1b37-377">Yank entre le début de la mémoire tampon et le curseur.</span><span class="sxs-lookup"><span data-stu-id="b1b37-377">Yank from the beginning of the buffer to the cursor.</span></span>

- <span data-ttu-id="b1b37-378">Mode de commande VI : `<y,0>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-378">Vi command mode: `<y,0>`</span></span>

### <a name="viyankendofglob"></a><span data-ttu-id="b1b37-379">ViYankEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="b1b37-379">ViYankEndOfGlob</span></span>

<span data-ttu-id="b1b37-380">Yank du curseur jusqu’à la fin du ou des mots.</span><span class="sxs-lookup"><span data-stu-id="b1b37-380">Yank from the cursor to the end of the WORD(s).</span></span>

- <span data-ttu-id="b1b37-381">Mode de commande VI : `<y,E>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-381">Vi command mode: `<y,E>`</span></span>

### <a name="viyankendofword"></a><span data-ttu-id="b1b37-382">ViYankEndOfWord</span><span class="sxs-lookup"><span data-stu-id="b1b37-382">ViYankEndOfWord</span></span>

<span data-ttu-id="b1b37-383">Yank du curseur jusqu’à la fin du ou des mots.</span><span class="sxs-lookup"><span data-stu-id="b1b37-383">Yank from the cursor to the end of the word(s).</span></span>

- <span data-ttu-id="b1b37-384">Mode de commande VI : `<y,e>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-384">Vi command mode: `<y,e>`</span></span>

### <a name="viyankleft"></a><span data-ttu-id="b1b37-385">ViYankLeft</span><span class="sxs-lookup"><span data-stu-id="b1b37-385">ViYankLeft</span></span>

<span data-ttu-id="b1b37-386">Yank caractère (s) à gauche du curseur.</span><span class="sxs-lookup"><span data-stu-id="b1b37-386">Yank character(s) to the left of the cursor.</span></span>

- <span data-ttu-id="b1b37-387">Mode de commande VI : `<y,h>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-387">Vi command mode: `<y,h>`</span></span>

### <a name="viyankline"></a><span data-ttu-id="b1b37-388">ViYankLine</span><span class="sxs-lookup"><span data-stu-id="b1b37-388">ViYankLine</span></span>

<span data-ttu-id="b1b37-389">Yank la mémoire tampon entière.</span><span class="sxs-lookup"><span data-stu-id="b1b37-389">Yank the entire buffer.</span></span>

- <span data-ttu-id="b1b37-390">Mode de commande VI : `<y,y>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-390">Vi command mode: `<y,y>`</span></span>

### <a name="viyanknextglob"></a><span data-ttu-id="b1b37-391">ViYankNextGlob</span><span class="sxs-lookup"><span data-stu-id="b1b37-391">ViYankNextGlob</span></span>

<span data-ttu-id="b1b37-392">Yank à partir d’un curseur jusqu’au début du ou des mots suivants.</span><span class="sxs-lookup"><span data-stu-id="b1b37-392">Yank from cursor to the start of the next WORD(s).</span></span>

- <span data-ttu-id="b1b37-393">Mode de commande VI : `<y,W>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-393">Vi command mode: `<y,W>`</span></span>

### <a name="viyanknextword"></a><span data-ttu-id="b1b37-394">ViYankNextWord</span><span class="sxs-lookup"><span data-stu-id="b1b37-394">ViYankNextWord</span></span>

<span data-ttu-id="b1b37-395">Yank le ou les mots après le curseur.</span><span class="sxs-lookup"><span data-stu-id="b1b37-395">Yank the word(s) after the cursor.</span></span>

- <span data-ttu-id="b1b37-396">Mode de commande VI : `<y,w>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-396">Vi command mode: `<y,w>`</span></span>

### <a name="viyankpercent"></a><span data-ttu-id="b1b37-397">ViYankPercent</span><span class="sxs-lookup"><span data-stu-id="b1b37-397">ViYankPercent</span></span>

<span data-ttu-id="b1b37-398">Yank à/à partir de l’accolade correspondante.</span><span class="sxs-lookup"><span data-stu-id="b1b37-398">Yank to/from matching brace.</span></span>

- <span data-ttu-id="b1b37-399">Mode de commande VI : `<y,%>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-399">Vi command mode: `<y,%>`</span></span>

### <a name="viyankpreviousglob"></a><span data-ttu-id="b1b37-400">ViYankPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="b1b37-400">ViYankPreviousGlob</span></span>

<span data-ttu-id="b1b37-401">Yank entre le début du ou des mots et le curseur.</span><span class="sxs-lookup"><span data-stu-id="b1b37-401">Yank from beginning of the WORD(s) to cursor.</span></span>

- <span data-ttu-id="b1b37-402">Mode de commande VI : `<y,B>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-402">Vi command mode: `<y,B>`</span></span>

### <a name="viyankpreviousword"></a><span data-ttu-id="b1b37-403">ViYankPreviousWord</span><span class="sxs-lookup"><span data-stu-id="b1b37-403">ViYankPreviousWord</span></span>

<span data-ttu-id="b1b37-404">Yank le ou les mots avant le curseur.</span><span class="sxs-lookup"><span data-stu-id="b1b37-404">Yank the word(s) before the cursor.</span></span>

- <span data-ttu-id="b1b37-405">Mode de commande VI : `<y,b>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-405">Vi command mode: `<y,b>`</span></span>

### <a name="viyankright"></a><span data-ttu-id="b1b37-406">ViYankRight</span><span class="sxs-lookup"><span data-stu-id="b1b37-406">ViYankRight</span></span>

<span data-ttu-id="b1b37-407">Yank caractère (s) situé sous et à droite du curseur.</span><span class="sxs-lookup"><span data-stu-id="b1b37-407">Yank character(s) under and to the right of the cursor.</span></span>

- <span data-ttu-id="b1b37-408">Mode de commande VI : `<y,l>` , `<y,Space>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-408">Vi command mode: `<y,l>`, `<y,Space>`</span></span>

### <a name="viyanktoendofline"></a><span data-ttu-id="b1b37-409">ViYankToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="b1b37-409">ViYankToEndOfLine</span></span>

<span data-ttu-id="b1b37-410">Yank du curseur jusqu’à la fin de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="b1b37-410">Yank from the cursor to the end of the buffer.</span></span>

- <span data-ttu-id="b1b37-411">Mode de commande VI : `<y,$>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-411">Vi command mode: `<y,$>`</span></span>

### <a name="viyanktofirstchar"></a><span data-ttu-id="b1b37-412">ViYankToFirstChar</span><span class="sxs-lookup"><span data-stu-id="b1b37-412">ViYankToFirstChar</span></span>

<span data-ttu-id="b1b37-413">Yank du premier caractère autre qu’un espace blanc au curseur.</span><span class="sxs-lookup"><span data-stu-id="b1b37-413">Yank from the first non-whitespace character to the cursor.</span></span>

- <span data-ttu-id="b1b37-414">Mode de commande VI : `<y,^>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-414">Vi command mode: `<y,^>`</span></span>

### <a name="yank"></a><span data-ttu-id="b1b37-415">Yank</span><span class="sxs-lookup"><span data-stu-id="b1b37-415">Yank</span></span>

<span data-ttu-id="b1b37-416">Ajoutez le texte le plus récemment supprimé à l’entrée.</span><span class="sxs-lookup"><span data-stu-id="b1b37-416">Add the most recently killed text to the input.</span></span>

- <span data-ttu-id="b1b37-417">Emacs- `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-417">Emacs: `<Ctrl+y>`</span></span>

### <a name="yanklastarg"></a><span data-ttu-id="b1b37-418">YankLastArg</span><span class="sxs-lookup"><span data-stu-id="b1b37-418">YankLastArg</span></span>

<span data-ttu-id="b1b37-419">Yank le dernier argument de la ligne d’historique précédente.</span><span class="sxs-lookup"><span data-stu-id="b1b37-419">Yank the last argument from the previous history line.</span></span> <span data-ttu-id="b1b37-420">Avec un argument, la première fois qu’il est appelé, se comporte comme YankNthArg.</span><span class="sxs-lookup"><span data-stu-id="b1b37-420">With an argument, the first time it is invoked, behaves just like YankNthArg.</span></span> <span data-ttu-id="b1b37-421">Si elle est appelée plusieurs fois, elle itère au sein de l’historique et ARG définit la direction (négatif inverse la direction).</span><span class="sxs-lookup"><span data-stu-id="b1b37-421">If invoked multiple times, instead it iterates through history and arg sets the direction (negative reverses the direction.)</span></span>

- <span data-ttu-id="b1b37-422">Cmd `<Alt+.>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-422">Cmd: `<Alt+.>`</span></span>
- <span data-ttu-id="b1b37-423">Emacs : `<Alt+.>` , `<Alt+_>` , `<Escape,.>` , `<Escape,_>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-423">Emacs: `<Alt+.>`, `<Alt+_>`, `<Escape,.>`, `<Escape,_>`</span></span>

### <a name="yankntharg"></a><span data-ttu-id="b1b37-424">YankNthArg</span><span class="sxs-lookup"><span data-stu-id="b1b37-424">YankNthArg</span></span>

<span data-ttu-id="b1b37-425">Yank le premier argument (après la commande) à partir de la ligne précédente de l’historique.</span><span class="sxs-lookup"><span data-stu-id="b1b37-425">Yank the first argument (after the command) from the previous history line.</span></span>
<span data-ttu-id="b1b37-426">Avec un argument, Yank le nième argument (à partir de 0), si l’argument est négatif, commencez par le dernier argument.</span><span class="sxs-lookup"><span data-stu-id="b1b37-426">With an argument, yank the nth argument (starting from 0), if the argument is negative, start from the last argument.</span></span>

- <span data-ttu-id="b1b37-427">Emacs- `<Ctrl+Alt+y>` , `<Escape,Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-427">Emacs: `<Ctrl+Alt+y>`, `<Escape,Ctrl+y>`</span></span>

### <a name="yankpop"></a><span data-ttu-id="b1b37-428">YankPop</span><span class="sxs-lookup"><span data-stu-id="b1b37-428">YankPop</span></span>

<span data-ttu-id="b1b37-429">Si l’opération précédente était Yank ou YankPop, remplacez le texte précédemment extrait par le texte supprimé suivant de l’instruction KILL-Ring.</span><span class="sxs-lookup"><span data-stu-id="b1b37-429">If the previous operation was Yank or YankPop, replace the previously yanked text with the next killed text from the kill-ring.</span></span>

- <span data-ttu-id="b1b37-430">Emacs- `<Alt+y>` , `<Escape,y>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-430">Emacs: `<Alt+y>`, `<Escape,y>`</span></span>

## <a name="cursor-movement-functions"></a><span data-ttu-id="b1b37-431">Fonctions de déplacement de curseur</span><span class="sxs-lookup"><span data-stu-id="b1b37-431">Cursor movement functions</span></span>

### <a name="backwardchar"></a><span data-ttu-id="b1b37-432">BackwardChar</span><span class="sxs-lookup"><span data-stu-id="b1b37-432">BackwardChar</span></span>

<span data-ttu-id="b1b37-433">Déplacer le curseur d’un caractère vers la gauche.</span><span class="sxs-lookup"><span data-stu-id="b1b37-433">Move the cursor one character to the left.</span></span> <span data-ttu-id="b1b37-434">Cela peut déplacer le curseur vers la ligne précédente de l’entrée multiligne.</span><span class="sxs-lookup"><span data-stu-id="b1b37-434">This may move the cursor to the previous line of multi-line input.</span></span>

- <span data-ttu-id="b1b37-435">Cmd `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-435">Cmd: `<LeftArrow>`</span></span>
- <span data-ttu-id="b1b37-436">Emacs- `<LeftArrow>` , `<Ctrl+b>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-436">Emacs: `<LeftArrow>`, `<Ctrl+b>`</span></span>
- <span data-ttu-id="b1b37-437">Mode d’insertion VI : `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-437">Vi insert mode: `<LeftArrow>`</span></span>
- <span data-ttu-id="b1b37-438">Mode de commande VI : `<LeftArrow>` , `<Backspace>` , `<h>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-438">Vi command mode: `<LeftArrow>`, `<Backspace>`, `<h>`</span></span>

### <a name="backwardword"></a><span data-ttu-id="b1b37-439">BackwardWord</span><span class="sxs-lookup"><span data-stu-id="b1b37-439">BackwardWord</span></span>

<span data-ttu-id="b1b37-440">Ramener le curseur au début du mot actuel, ou si entre les mots, le début du mot précédent.</span><span class="sxs-lookup"><span data-stu-id="b1b37-440">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="b1b37-441">Les limites de mots sont définies par un jeu de caractères configurable.</span><span class="sxs-lookup"><span data-stu-id="b1b37-441">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="b1b37-442">Cmd `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-442">Cmd: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="b1b37-443">Emacs- `<Alt+b>` , `<Escape,b>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-443">Emacs: `<Alt+b>`, `<Escape,b>`</span></span>
- <span data-ttu-id="b1b37-444">Mode d’insertion VI : `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-444">Vi insert mode: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="b1b37-445">Mode de commande VI : `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-445">Vi command mode: `<Ctrl+LeftArrow>`</span></span>

### <a name="beginningofline"></a><span data-ttu-id="b1b37-446">BeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="b1b37-446">BeginningOfLine</span></span>

<span data-ttu-id="b1b37-447">Si l’entrée comporte plusieurs lignes, se déplacer au début de la ligne active ou, le cas échéant, au début de la ligne, se déplacer au début de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="b1b37-447">If the input has multiple lines, move to the start of the current line, or if already at the start of the line, move to the start of the input.</span></span> <span data-ttu-id="b1b37-448">Si l’entrée comporte une seule ligne, accédez au début de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="b1b37-448">If the input has a single line, move to the start of the input.</span></span>

- <span data-ttu-id="b1b37-449">Cmd `<Home>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-449">Cmd: `<Home>`</span></span>
- <span data-ttu-id="b1b37-450">Emacs- `<Home>` , `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-450">Emacs: `<Home>`, `<Ctrl+a>`</span></span>
- <span data-ttu-id="b1b37-451">Mode d’insertion VI : `<Home>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-451">Vi insert mode: `<Home>`</span></span>
- <span data-ttu-id="b1b37-452">Mode de commande VI : `<Home>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-452">Vi command mode: `<Home>`</span></span>

### <a name="endofline"></a><span data-ttu-id="b1b37-453">EndOfLine</span><span class="sxs-lookup"><span data-stu-id="b1b37-453">EndOfLine</span></span>

<span data-ttu-id="b1b37-454">Si l’entrée comporte plusieurs lignes, passez à la fin de la ligne active ou, si elle se trouve déjà à la fin de la ligne, à la fin de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="b1b37-454">If the input has multiple lines, move to the end of the current line, or if already at the end of the line, move to the end of the input.</span></span> <span data-ttu-id="b1b37-455">Si l’entrée comporte une seule ligne, passez à la fin de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="b1b37-455">If the input has a single line, move to the end of the input.</span></span>

- <span data-ttu-id="b1b37-456">Cmd `<End>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-456">Cmd: `<End>`</span></span>
- <span data-ttu-id="b1b37-457">Emacs- `<End>` , `<Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-457">Emacs: `<End>`, `<Ctrl+e>`</span></span>
- <span data-ttu-id="b1b37-458">Mode d’insertion VI : `<End>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-458">Vi insert mode: `<End>`</span></span>

### <a name="forwardchar"></a><span data-ttu-id="b1b37-459">ForwardChar</span><span class="sxs-lookup"><span data-stu-id="b1b37-459">ForwardChar</span></span>

<span data-ttu-id="b1b37-460">Déplacer le curseur d’un caractère vers la droite.</span><span class="sxs-lookup"><span data-stu-id="b1b37-460">Move the cursor one character to the right.</span></span> <span data-ttu-id="b1b37-461">Cela peut déplacer le curseur à la ligne suivante de l’entrée multiligne.</span><span class="sxs-lookup"><span data-stu-id="b1b37-461">This may move the cursor to the next line of multi-line input.</span></span>

- <span data-ttu-id="b1b37-462">Cmd `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-462">Cmd: `<RightArrow>`</span></span>
- <span data-ttu-id="b1b37-463">Emacs- `<RightArrow>` , `<Ctrl+f>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-463">Emacs: `<RightArrow>`, `<Ctrl+f>`</span></span>
- <span data-ttu-id="b1b37-464">Mode d’insertion VI : `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-464">Vi insert mode: `<RightArrow>`</span></span>
- <span data-ttu-id="b1b37-465">Mode de commande VI : `<RightArrow>` , `<Space>` , `<l>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-465">Vi command mode: `<RightArrow>`, `<Space>`, `<l>`</span></span>

### <a name="forwardword"></a><span data-ttu-id="b1b37-466">ForwardWord</span><span class="sxs-lookup"><span data-stu-id="b1b37-466">ForwardWord</span></span>

<span data-ttu-id="b1b37-467">Déplacer le curseur vers l’avant jusqu’à la fin du mot actuel, ou si entre les mots, à la fin du mot suivant.</span><span class="sxs-lookup"><span data-stu-id="b1b37-467">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="b1b37-468">Les limites de mots sont définies par un jeu de caractères configurable.</span><span class="sxs-lookup"><span data-stu-id="b1b37-468">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="b1b37-469">Emacs- `<Alt+f>` , `<Escape,f>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-469">Emacs: `<Alt+f>`, `<Escape,f>`</span></span>

### <a name="gotobrace"></a><span data-ttu-id="b1b37-470">GotoBrace</span><span class="sxs-lookup"><span data-stu-id="b1b37-470">GotoBrace</span></span>

<span data-ttu-id="b1b37-471">Atteindre l’accolade correspondante, les parenthèses ou les crochets.</span><span class="sxs-lookup"><span data-stu-id="b1b37-471">Go to the matching brace, parenthesis, or square bracket.</span></span>

- <span data-ttu-id="b1b37-472">Cmd `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-472">Cmd: `<Ctrl+]>`</span></span>
- <span data-ttu-id="b1b37-473">Mode d’insertion VI : `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-473">Vi insert mode: `<Ctrl+]>`</span></span>
- <span data-ttu-id="b1b37-474">Mode de commande VI : `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-474">Vi command mode: `<Ctrl+]>`</span></span>

### <a name="gotocolumn"></a><span data-ttu-id="b1b37-475">GotoColumn</span><span class="sxs-lookup"><span data-stu-id="b1b37-475">GotoColumn</span></span>

<span data-ttu-id="b1b37-476">Accédez à la colonne indiquée par arg.</span><span class="sxs-lookup"><span data-stu-id="b1b37-476">Move to the column indicated by arg.</span></span>

- <span data-ttu-id="b1b37-477">Mode de commande VI : `<|>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-477">Vi command mode: `<|>`</span></span>

### <a name="gotofirstnonblankofline"></a><span data-ttu-id="b1b37-478">GotoFirstNonBlankOfLine</span><span class="sxs-lookup"><span data-stu-id="b1b37-478">GotoFirstNonBlankOfLine</span></span>

<span data-ttu-id="b1b37-479">Placez le curseur sur le premier caractère non vide de la ligne.</span><span class="sxs-lookup"><span data-stu-id="b1b37-479">Move the cursor to the first non-blank character in the line.</span></span>

- <span data-ttu-id="b1b37-480">Mode de commande VI : `<^>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-480">Vi command mode: `<^>`</span></span>

### <a name="movetoendofline"></a><span data-ttu-id="b1b37-481">MoveToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="b1b37-481">MoveToEndOfLine</span></span>

<span data-ttu-id="b1b37-482">Placez le curseur à la fin de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="b1b37-482">Move the cursor to the end of the input.</span></span>

- <span data-ttu-id="b1b37-483">Mode de commande VI : `<End>` , `<$>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-483">Vi command mode: `<End>`, `<$>`</span></span>

### <a name="nextline"></a><span data-ttu-id="b1b37-484">NextLine</span><span class="sxs-lookup"><span data-stu-id="b1b37-484">NextLine</span></span>

<span data-ttu-id="b1b37-485">Déplacer le curseur sur la ligne suivante.</span><span class="sxs-lookup"><span data-stu-id="b1b37-485">Move the cursor to the next line.</span></span>

- <span data-ttu-id="b1b37-486">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="b1b37-486">Function is unbound.</span></span>

### <a name="nextword"></a><span data-ttu-id="b1b37-487">NextWord</span><span class="sxs-lookup"><span data-stu-id="b1b37-487">NextWord</span></span>

<span data-ttu-id="b1b37-488">Déplacer le curseur vers l’avant jusqu’au début du mot suivant.</span><span class="sxs-lookup"><span data-stu-id="b1b37-488">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="b1b37-489">Les limites de mots sont définies par un jeu de caractères configurable.</span><span class="sxs-lookup"><span data-stu-id="b1b37-489">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="b1b37-490">Cmd `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-490">Cmd: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="b1b37-491">Mode d’insertion VI : `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-491">Vi insert mode: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="b1b37-492">Mode de commande VI : `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-492">Vi command mode: `<Ctrl+RightArrow>`</span></span>

### <a name="nextwordend"></a><span data-ttu-id="b1b37-493">NextWordEnd</span><span class="sxs-lookup"><span data-stu-id="b1b37-493">NextWordEnd</span></span>

<span data-ttu-id="b1b37-494">Déplacer le curseur vers l’avant jusqu’à la fin du mot actuel, ou si entre les mots, à la fin du mot suivant.</span><span class="sxs-lookup"><span data-stu-id="b1b37-494">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="b1b37-495">Les limites de mots sont définies par un jeu de caractères configurable.</span><span class="sxs-lookup"><span data-stu-id="b1b37-495">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="b1b37-496">Mode de commande VI : `<e>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-496">Vi command mode: `<e>`</span></span>

### <a name="previousline"></a><span data-ttu-id="b1b37-497">PreviousLine</span><span class="sxs-lookup"><span data-stu-id="b1b37-497">PreviousLine</span></span>

<span data-ttu-id="b1b37-498">Placez le curseur sur la ligne précédente.</span><span class="sxs-lookup"><span data-stu-id="b1b37-498">Move the cursor to the previous line.</span></span>

- <span data-ttu-id="b1b37-499">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="b1b37-499">Function is unbound.</span></span>

### <a name="shellbackwardword"></a><span data-ttu-id="b1b37-500">ShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="b1b37-500">ShellBackwardWord</span></span>

<span data-ttu-id="b1b37-501">Ramener le curseur au début du mot actuel, ou si entre les mots, le début du mot précédent.</span><span class="sxs-lookup"><span data-stu-id="b1b37-501">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="b1b37-502">Les limites de mots sont définies par les jetons PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b1b37-502">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="b1b37-503">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="b1b37-503">Function is unbound.</span></span>

### <a name="shellforwardword"></a><span data-ttu-id="b1b37-504">ShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="b1b37-504">ShellForwardWord</span></span>

<span data-ttu-id="b1b37-505">Déplacer le curseur vers l’avant jusqu’au début du mot suivant.</span><span class="sxs-lookup"><span data-stu-id="b1b37-505">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="b1b37-506">Les limites de mots sont définies par les jetons PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b1b37-506">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="b1b37-507">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="b1b37-507">Function is unbound.</span></span>

### <a name="shellnextword"></a><span data-ttu-id="b1b37-508">ShellNextWord</span><span class="sxs-lookup"><span data-stu-id="b1b37-508">ShellNextWord</span></span>

<span data-ttu-id="b1b37-509">Déplacer le curseur vers l’avant jusqu’à la fin du mot actuel, ou si entre les mots, à la fin du mot suivant.</span><span class="sxs-lookup"><span data-stu-id="b1b37-509">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="b1b37-510">Les limites de mots sont définies par les jetons PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b1b37-510">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="b1b37-511">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="b1b37-511">Function is unbound.</span></span>

### <a name="vibackwardword"></a><span data-ttu-id="b1b37-512">ViBackwardWord</span><span class="sxs-lookup"><span data-stu-id="b1b37-512">ViBackwardWord</span></span>

<span data-ttu-id="b1b37-513">Ramener le curseur au début du mot actuel, ou si entre les mots, le début du mot précédent.</span><span class="sxs-lookup"><span data-stu-id="b1b37-513">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="b1b37-514">Les limites de mots sont définies par un jeu de caractères configurable.</span><span class="sxs-lookup"><span data-stu-id="b1b37-514">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="b1b37-515">Mode de commande VI : `<b>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-515">Vi command mode: `<b>`</span></span>

### <a name="viendofglob"></a><span data-ttu-id="b1b37-516">ViEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="b1b37-516">ViEndOfGlob</span></span>

<span data-ttu-id="b1b37-517">Déplace le curseur à la fin du mot, en utilisant uniquement des espaces blancs comme délimiteurs.</span><span class="sxs-lookup"><span data-stu-id="b1b37-517">Moves the cursor to the end of the word, using only white space as delimiters.</span></span>

- <span data-ttu-id="b1b37-518">Mode de commande VI : `<E>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-518">Vi command mode: `<E>`</span></span>

### <a name="viendofpreviousglob"></a><span data-ttu-id="b1b37-519">ViEndOfPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="b1b37-519">ViEndOfPreviousGlob</span></span>

<span data-ttu-id="b1b37-520">Passe à la fin du mot précédent, en utilisant uniquement un espace blanc comme délimiteur de mot.</span><span class="sxs-lookup"><span data-stu-id="b1b37-520">Moves to the end of the previous word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="b1b37-521">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="b1b37-521">Function is unbound.</span></span>

### <a name="vigotobrace"></a><span data-ttu-id="b1b37-522">ViGotoBrace</span><span class="sxs-lookup"><span data-stu-id="b1b37-522">ViGotoBrace</span></span>

<span data-ttu-id="b1b37-523">Semblable à GotoBrace, mais est basé sur un caractère et non sur un jeton.</span><span class="sxs-lookup"><span data-stu-id="b1b37-523">Similar to GotoBrace, but is character based instead of token based.</span></span>

- <span data-ttu-id="b1b37-524">Mode de commande VI : `<%>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-524">Vi command mode: `<%>`</span></span>

### <a name="vinextglob"></a><span data-ttu-id="b1b37-525">ViNextGlob</span><span class="sxs-lookup"><span data-stu-id="b1b37-525">ViNextGlob</span></span>

<span data-ttu-id="b1b37-526">Passe au mot suivant, en utilisant uniquement un espace blanc comme délimiteur de mot.</span><span class="sxs-lookup"><span data-stu-id="b1b37-526">Moves to the next word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="b1b37-527">Mode de commande VI : `<W>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-527">Vi command mode: `<W>`</span></span>

### <a name="vinextword"></a><span data-ttu-id="b1b37-528">ViNextWord</span><span class="sxs-lookup"><span data-stu-id="b1b37-528">ViNextWord</span></span>

<span data-ttu-id="b1b37-529">Déplacer le curseur vers l’avant jusqu’au début du mot suivant.</span><span class="sxs-lookup"><span data-stu-id="b1b37-529">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="b1b37-530">Les limites de mots sont définies par un jeu de caractères configurable.</span><span class="sxs-lookup"><span data-stu-id="b1b37-530">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="b1b37-531">Mode de commande VI : `<w>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-531">Vi command mode: `<w>`</span></span>

## <a name="history-functions"></a><span data-ttu-id="b1b37-532">Fonctions d’historique</span><span class="sxs-lookup"><span data-stu-id="b1b37-532">History functions</span></span>

### <a name="beginningofhistory"></a><span data-ttu-id="b1b37-533">BeginningOfHistory</span><span class="sxs-lookup"><span data-stu-id="b1b37-533">BeginningOfHistory</span></span>

<span data-ttu-id="b1b37-534">Accéder au premier élément de l’historique.</span><span class="sxs-lookup"><span data-stu-id="b1b37-534">Move to the first item in the history.</span></span>

- <span data-ttu-id="b1b37-535">Emacs- `<Alt+`<>\`</span><span class="sxs-lookup"><span data-stu-id="b1b37-535">Emacs: `<Alt+`<>\`</span></span>

### <a name="clearhistory"></a><span data-ttu-id="b1b37-536">ClearHistory</span><span class="sxs-lookup"><span data-stu-id="b1b37-536">ClearHistory</span></span>

<span data-ttu-id="b1b37-537">Efface l’historique dans PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="b1b37-537">Clears history in PSReadLine.</span></span> <span data-ttu-id="b1b37-538">Cela n’affecte pas l’historique PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b1b37-538">This does not affect PowerShell history.</span></span>

- <span data-ttu-id="b1b37-539">Cmd `<Alt+F7>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-539">Cmd: `<Alt+F7>`</span></span>

### <a name="endofhistory"></a><span data-ttu-id="b1b37-540">EndOfHistory</span><span class="sxs-lookup"><span data-stu-id="b1b37-540">EndOfHistory</span></span>

<span data-ttu-id="b1b37-541">Accéder au dernier élément (l’entrée en cours) dans l’historique.</span><span class="sxs-lookup"><span data-stu-id="b1b37-541">Move to the last item (the current input) in the history.</span></span>

- <span data-ttu-id="b1b37-542">Emacs- `<Alt+>>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-542">Emacs: `<Alt+>>`</span></span>

### <a name="forwardsearchhistory"></a><span data-ttu-id="b1b37-543">ForwardSearchHistory</span><span class="sxs-lookup"><span data-stu-id="b1b37-543">ForwardSearchHistory</span></span>

<span data-ttu-id="b1b37-544">Effectuer une recherche incrémentielle par progression dans l’historique.</span><span class="sxs-lookup"><span data-stu-id="b1b37-544">Perform an incremental forward search through history.</span></span>

- <span data-ttu-id="b1b37-545">Cmd `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-545">Cmd: `<Ctrl+s>`</span></span>
- <span data-ttu-id="b1b37-546">Emacs- `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-546">Emacs: `<Ctrl+s>`</span></span>

### <a name="historysearchbackward"></a><span data-ttu-id="b1b37-547">HistorySearchBackward</span><span class="sxs-lookup"><span data-stu-id="b1b37-547">HistorySearchBackward</span></span>

<span data-ttu-id="b1b37-548">Remplacez l’entrée actuelle par l’élément « Previous » de l’historique PSReadLine qui correspond aux caractères entre le début et l’entrée et le curseur.</span><span class="sxs-lookup"><span data-stu-id="b1b37-548">Replace the current input with the 'previous' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="b1b37-549">Cmd `<F8>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-549">Cmd: `<F8>`</span></span>

### <a name="historysearchforward"></a><span data-ttu-id="b1b37-550">HistorySearchForward</span><span class="sxs-lookup"><span data-stu-id="b1b37-550">HistorySearchForward</span></span>

<span data-ttu-id="b1b37-551">Remplacez l’entrée actuelle par l’élément « Next » de l’historique PSReadLine qui correspond aux caractères entre le début et l’entrée et le curseur.</span><span class="sxs-lookup"><span data-stu-id="b1b37-551">Replace the current input with the 'next' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="b1b37-552">Cmd `<Shift+F8>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-552">Cmd: `<Shift+F8>`</span></span>

### <a name="nexthistory"></a><span data-ttu-id="b1b37-553">NextHistory</span><span class="sxs-lookup"><span data-stu-id="b1b37-553">NextHistory</span></span>

<span data-ttu-id="b1b37-554">Remplacez l’entrée actuelle par l’élément « Next » de l’historique PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="b1b37-554">Replace the current input with the 'next' item from PSReadLine history.</span></span>

- <span data-ttu-id="b1b37-555">Cmd `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-555">Cmd: `<DownArrow>`</span></span>
- <span data-ttu-id="b1b37-556">Emacs- `<DownArrow>` , `<Ctrl+n>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-556">Emacs: `<DownArrow>`, `<Ctrl+n>`</span></span>
- <span data-ttu-id="b1b37-557">Mode d’insertion VI : `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-557">Vi insert mode: `<DownArrow>`</span></span>
- <span data-ttu-id="b1b37-558">Mode de commande VI : `<DownArrow>` , `<j>` , `<+>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-558">Vi command mode: `<DownArrow>`, `<j>`, `<+>`</span></span>

### <a name="previoushistory"></a><span data-ttu-id="b1b37-559">PreviousHistory</span><span class="sxs-lookup"><span data-stu-id="b1b37-559">PreviousHistory</span></span>

<span data-ttu-id="b1b37-560">Remplacez l’entrée actuelle par l’élément « Previous » de l’historique PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="b1b37-560">Replace the current input with the 'previous' item from PSReadLine history.</span></span>

- <span data-ttu-id="b1b37-561">Cmd `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-561">Cmd: `<UpArrow>`</span></span>
- <span data-ttu-id="b1b37-562">Emacs- `<UpArrow>` , `<Ctrl+p>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-562">Emacs: `<UpArrow>`, `<Ctrl+p>`</span></span>
- <span data-ttu-id="b1b37-563">Mode d’insertion VI : `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-563">Vi insert mode: `<UpArrow>`</span></span>
- <span data-ttu-id="b1b37-564">Mode de commande VI : `<UpArrow>` , `<k>` , `<->`</span><span class="sxs-lookup"><span data-stu-id="b1b37-564">Vi command mode: `<UpArrow>`, `<k>`, `<->`</span></span>

### <a name="reversesearchhistory"></a><span data-ttu-id="b1b37-565">ReverseSearchHistory</span><span class="sxs-lookup"><span data-stu-id="b1b37-565">ReverseSearchHistory</span></span>

<span data-ttu-id="b1b37-566">Effectuer une recherche incrémentielle incrémentielle dans l’historique.</span><span class="sxs-lookup"><span data-stu-id="b1b37-566">Perform an incremental backward search through history.</span></span>

- <span data-ttu-id="b1b37-567">Cmd `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-567">Cmd: `<Ctrl+r>`</span></span>
- <span data-ttu-id="b1b37-568">Emacs- `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-568">Emacs: `<Ctrl+r>`</span></span>

### <a name="visearchhistorybackward"></a><span data-ttu-id="b1b37-569">ViSearchHistoryBackward</span><span class="sxs-lookup"><span data-stu-id="b1b37-569">ViSearchHistoryBackward</span></span>

<span data-ttu-id="b1b37-570">Demande une chaîne de recherche et lance la recherche sur AcceptLine.</span><span class="sxs-lookup"><span data-stu-id="b1b37-570">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="b1b37-571">Mode d’insertion VI : `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-571">Vi insert mode: `<Ctrl+r>`</span></span>
- <span data-ttu-id="b1b37-572">Mode de commande VI : `</>` , `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-572">Vi command mode: `</>`, `<Ctrl+r>`</span></span>

## <a name="completion-functions"></a><span data-ttu-id="b1b37-573">Fonctions d’achèvement</span><span class="sxs-lookup"><span data-stu-id="b1b37-573">Completion functions</span></span>

### <a name="complete"></a><span data-ttu-id="b1b37-574">Terminé</span><span class="sxs-lookup"><span data-stu-id="b1b37-574">Complete</span></span>

<span data-ttu-id="b1b37-575">Tentative d’exécution de l’opération sur le texte entourant le curseur.</span><span class="sxs-lookup"><span data-stu-id="b1b37-575">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="b1b37-576">S’il existe plusieurs saisies semi-automatiques possibles, le plus long préfixe non ambigu est utilisé pour la finalisation.</span><span class="sxs-lookup"><span data-stu-id="b1b37-576">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="b1b37-577">Si vous essayez de terminer la saisie semi-automatique la plus longue, une liste des saisies semi-automatiques possibles s’affiche.</span><span class="sxs-lookup"><span data-stu-id="b1b37-577">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="b1b37-578">Emacs- `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-578">Emacs: `<Tab>`</span></span>

### <a name="menucomplete"></a><span data-ttu-id="b1b37-579">MenuComplete</span><span class="sxs-lookup"><span data-stu-id="b1b37-579">MenuComplete</span></span>

<span data-ttu-id="b1b37-580">Tentative d’exécution de l’opération sur le texte entourant le curseur.</span><span class="sxs-lookup"><span data-stu-id="b1b37-580">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="b1b37-581">S’il existe plusieurs saisies semi-automatiques possibles, le plus long préfixe non ambigu est utilisé pour la finalisation.</span><span class="sxs-lookup"><span data-stu-id="b1b37-581">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="b1b37-582">Si vous essayez de terminer la saisie semi-automatique la plus longue, une liste des saisies semi-automatiques possibles s’affiche.</span><span class="sxs-lookup"><span data-stu-id="b1b37-582">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="b1b37-583">Cmd `<Ctrl+Space>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-583">Cmd: `<Ctrl+Space>`</span></span>
- <span data-ttu-id="b1b37-584">Emacs- `<Ctrl+Space>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-584">Emacs: `<Ctrl+Space>`</span></span>

### <a name="possiblecompletions"></a><span data-ttu-id="b1b37-585">PossibleCompletions</span><span class="sxs-lookup"><span data-stu-id="b1b37-585">PossibleCompletions</span></span>

<span data-ttu-id="b1b37-586">Affiche la liste des saisies semi-automatiques possibles.</span><span class="sxs-lookup"><span data-stu-id="b1b37-586">Display the list of possible completions.</span></span>

- <span data-ttu-id="b1b37-587">Emacs- `<Alt+=>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-587">Emacs: `<Alt+=>`</span></span>
- <span data-ttu-id="b1b37-588">Mode d’insertion VI : `<Ctrl+Space>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-588">Vi insert mode: `<Ctrl+Space>`</span></span>
- <span data-ttu-id="b1b37-589">Mode de commande VI : `<Ctrl+Space>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-589">Vi command mode: `<Ctrl+Space>`</span></span>

### <a name="tabcompletenext"></a><span data-ttu-id="b1b37-590">TabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="b1b37-590">TabCompleteNext</span></span>

<span data-ttu-id="b1b37-591">Tente de terminer le texte entourant le curseur avec la prochaine saisie semi-automatique disponible.</span><span class="sxs-lookup"><span data-stu-id="b1b37-591">Attempt to complete the text surrounding the cursor with the next available completion.</span></span>

- <span data-ttu-id="b1b37-592">Cmd `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-592">Cmd: `<Tab>`</span></span>
- <span data-ttu-id="b1b37-593">Mode de commande VI : `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-593">Vi command mode: `<Tab>`</span></span>

### <a name="tabcompleteprevious"></a><span data-ttu-id="b1b37-594">TabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="b1b37-594">TabCompletePrevious</span></span>

<span data-ttu-id="b1b37-595">Tente de terminer le texte entourant le curseur avec l’achèvement disponible précédent.</span><span class="sxs-lookup"><span data-stu-id="b1b37-595">Attempt to complete the text surrounding the cursor with the previous available completion.</span></span>

- <span data-ttu-id="b1b37-596">Cmd `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-596">Cmd: `<Shift+Tab>`</span></span>
- <span data-ttu-id="b1b37-597">Mode de commande VI : `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-597">Vi command mode: `<Shift+Tab>`</span></span>

### <a name="vitabcompletenext"></a><span data-ttu-id="b1b37-598">ViTabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="b1b37-598">ViTabCompleteNext</span></span>

<span data-ttu-id="b1b37-599">Met fin au groupe d’édition actuel, si nécessaire, et appelle TabCompleteNext.</span><span class="sxs-lookup"><span data-stu-id="b1b37-599">Ends the current edit group, if needed, and invokes TabCompleteNext.</span></span>

- <span data-ttu-id="b1b37-600">Mode d’insertion VI : `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-600">Vi insert mode: `<Tab>`</span></span>

### <a name="vitabcompleteprevious"></a><span data-ttu-id="b1b37-601">ViTabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="b1b37-601">ViTabCompletePrevious</span></span>

<span data-ttu-id="b1b37-602">Met fin au groupe d’édition actuel, si nécessaire, et appelle TabCompletePrevious.</span><span class="sxs-lookup"><span data-stu-id="b1b37-602">Ends the current edit group, if needed, and invokes TabCompletePrevious.</span></span>

- <span data-ttu-id="b1b37-603">Mode d’insertion VI : `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-603">Vi insert mode: `<Shift+Tab>`</span></span>

## <a name="miscellaneous-functions"></a><span data-ttu-id="b1b37-604">Fonctions diverses</span><span class="sxs-lookup"><span data-stu-id="b1b37-604">Miscellaneous functions</span></span>

### <a name="capturescreen"></a><span data-ttu-id="b1b37-605">CaptureScreen</span><span class="sxs-lookup"><span data-stu-id="b1b37-605">CaptureScreen</span></span>

<span data-ttu-id="b1b37-606">Démarrer la capture d’écran interactive-flèches haut et bas sélectionnez lignes, entrez copie le texte sélectionné dans le presse-papiers en tant que texte et html.</span><span class="sxs-lookup"><span data-stu-id="b1b37-606">Start interactive screen capture - up/down arrows select lines, enter copies selected text to clipboard as text and html.</span></span>

- <span data-ttu-id="b1b37-607">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="b1b37-607">Function is unbound.</span></span>

### <a name="clearscreen"></a><span data-ttu-id="b1b37-608">ClearScreen</span><span class="sxs-lookup"><span data-stu-id="b1b37-608">ClearScreen</span></span>

<span data-ttu-id="b1b37-609">Effacez l’écran et dessinez la ligne active en haut de l’écran.</span><span class="sxs-lookup"><span data-stu-id="b1b37-609">Clear the screen and draw the current line at the top of the screen.</span></span>

- <span data-ttu-id="b1b37-610">Cmd `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-610">Cmd: `<Ctrl+l>`</span></span>
- <span data-ttu-id="b1b37-611">Emacs- `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-611">Emacs: `<Ctrl+l>`</span></span>
- <span data-ttu-id="b1b37-612">Mode d’insertion VI : `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-612">Vi insert mode: `<Ctrl+l>`</span></span>
- <span data-ttu-id="b1b37-613">Mode de commande VI : `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-613">Vi command mode: `<Ctrl+l>`</span></span>

### <a name="digitargument"></a><span data-ttu-id="b1b37-614">DigitArgument</span><span class="sxs-lookup"><span data-stu-id="b1b37-614">DigitArgument</span></span>

<span data-ttu-id="b1b37-615">Démarrez un nouvel argument digit à passer à d’autres fonctions.</span><span class="sxs-lookup"><span data-stu-id="b1b37-615">Start a new digit argument to pass to other functions.</span></span>

- <span data-ttu-id="b1b37-616">Cmd : `<Alt+0>` ,,,,, `<Alt+1>` `<Alt+2>` `<Alt+3>` `<Alt+4>` `<Alt+5>` , `<Alt+6>` , `<Alt+7>` , `<Alt+8>` , `<Alt+9>` , `<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="b1b37-616">Cmd: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="b1b37-617">Emacs-,,,,,,,,, `<Alt+0>` `<Alt+1>` `<Alt+2>` `<Alt+3>` `<Alt+4>` `<Alt+5>` `<Alt+6>` `<Alt+7>` `<Alt+8>` , `<Alt+9>` , `<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="b1b37-617">Emacs: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="b1b37-618">Mode de commande VI : `<0>` , `<1>` ,, `<2>` `<3>` , `<4>` , `<5>` , `<6>` , `<7>` , `<8>` , `<9>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-618">Vi command mode: `<0>`, `<1>`, `<2>`, `<3>`, `<4>`, `<5>`, `<6>`, `<7>`, `<8>`, `<9>`</span></span>

### <a name="invokeprompt"></a><span data-ttu-id="b1b37-619">InvokePrompt</span><span class="sxs-lookup"><span data-stu-id="b1b37-619">InvokePrompt</span></span>

<span data-ttu-id="b1b37-620">Efface l’invite en cours et appelle la fonction prompt pour réafficher l’invite.</span><span class="sxs-lookup"><span data-stu-id="b1b37-620">Erases the current prompt and calls the prompt function to redisplay the prompt.</span></span> <span data-ttu-id="b1b37-621">Utile pour les gestionnaires de clés personnalisés qui changent d’État, par exemple modifier le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="b1b37-621">Useful for custom key handlers that change state, e.g. change the current directory.</span></span>

- <span data-ttu-id="b1b37-622">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="b1b37-622">Function is unbound.</span></span>

### <a name="scrolldisplaydown"></a><span data-ttu-id="b1b37-623">ScrollDisplayDown</span><span class="sxs-lookup"><span data-stu-id="b1b37-623">ScrollDisplayDown</span></span>

<span data-ttu-id="b1b37-624">Faites défiler l’écran vers le volet d’affichage.</span><span class="sxs-lookup"><span data-stu-id="b1b37-624">Scroll the display down one screen.</span></span>

- <span data-ttu-id="b1b37-625">Cmd `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-625">Cmd: `<PageDown>`</span></span>
- <span data-ttu-id="b1b37-626">Emacs- `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-626">Emacs: `<PageDown>`</span></span>

### <a name="scrolldisplaydownline"></a><span data-ttu-id="b1b37-627">ScrollDisplayDownLine</span><span class="sxs-lookup"><span data-stu-id="b1b37-627">ScrollDisplayDownLine</span></span>

<span data-ttu-id="b1b37-628">Faites défiler l’affichage d’une ligne vers le dessous.</span><span class="sxs-lookup"><span data-stu-id="b1b37-628">Scroll the display down one line.</span></span>

- <span data-ttu-id="b1b37-629">Cmd `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-629">Cmd: `<Ctrl+PageDown>`</span></span>
- <span data-ttu-id="b1b37-630">Emacs- `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-630">Emacs: `<Ctrl+PageDown>`</span></span>

### <a name="scrolldisplaytocursor"></a><span data-ttu-id="b1b37-631">ScrollDisplayToCursor</span><span class="sxs-lookup"><span data-stu-id="b1b37-631">ScrollDisplayToCursor</span></span>

<span data-ttu-id="b1b37-632">Faites défiler l’affichage jusqu’au curseur.</span><span class="sxs-lookup"><span data-stu-id="b1b37-632">Scroll the display to the cursor.</span></span>

- <span data-ttu-id="b1b37-633">Emacs- `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-633">Emacs: `<Ctrl+End>`</span></span>

### <a name="scrolldisplaytop"></a><span data-ttu-id="b1b37-634">ScrollDisplayTop</span><span class="sxs-lookup"><span data-stu-id="b1b37-634">ScrollDisplayTop</span></span>

<span data-ttu-id="b1b37-635">Faites défiler l’affichage vers le haut.</span><span class="sxs-lookup"><span data-stu-id="b1b37-635">Scroll the display to the top.</span></span>

- <span data-ttu-id="b1b37-636">Emacs- `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-636">Emacs: `<Ctrl+Home>`</span></span>

### <a name="scrolldisplayup"></a><span data-ttu-id="b1b37-637">ScrollDisplayUp</span><span class="sxs-lookup"><span data-stu-id="b1b37-637">ScrollDisplayUp</span></span>

<span data-ttu-id="b1b37-638">Faites défiler l’écran afficher vers le haut.</span><span class="sxs-lookup"><span data-stu-id="b1b37-638">Scroll the display up one screen.</span></span>

- <span data-ttu-id="b1b37-639">Cmd `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-639">Cmd: `<PageUp>`</span></span>
- <span data-ttu-id="b1b37-640">Emacs- `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-640">Emacs: `<PageUp>`</span></span>

### <a name="scrolldisplayupline"></a><span data-ttu-id="b1b37-641">ScrollDisplayUpLine</span><span class="sxs-lookup"><span data-stu-id="b1b37-641">ScrollDisplayUpLine</span></span>

<span data-ttu-id="b1b37-642">Faites défiler l’affichage d’une ligne vers le haut.</span><span class="sxs-lookup"><span data-stu-id="b1b37-642">Scroll the display up one line.</span></span>

- <span data-ttu-id="b1b37-643">Cmd `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-643">Cmd: `<Ctrl+PageUp>`</span></span>
- <span data-ttu-id="b1b37-644">Emacs- `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-644">Emacs: `<Ctrl+PageUp>`</span></span>

### <a name="selfinsert"></a><span data-ttu-id="b1b37-645">SelfInsert</span><span class="sxs-lookup"><span data-stu-id="b1b37-645">SelfInsert</span></span>

<span data-ttu-id="b1b37-646">Insérez la clé.</span><span class="sxs-lookup"><span data-stu-id="b1b37-646">Insert the key.</span></span>

- <span data-ttu-id="b1b37-647">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="b1b37-647">Function is unbound.</span></span>

### <a name="showkeybindings"></a><span data-ttu-id="b1b37-648">ShowKeyBindings</span><span class="sxs-lookup"><span data-stu-id="b1b37-648">ShowKeyBindings</span></span>

<span data-ttu-id="b1b37-649">Affiche toutes les clés liées.</span><span class="sxs-lookup"><span data-stu-id="b1b37-649">Show all bound keys.</span></span>

- <span data-ttu-id="b1b37-650">Cmd `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-650">Cmd: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="b1b37-651">Emacs- `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-651">Emacs: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="b1b37-652">Mode d’insertion VI : `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-652">Vi insert mode: `<Ctrl+Alt+?>`</span></span>

### <a name="vicommandmode"></a><span data-ttu-id="b1b37-653">ViCommandMode</span><span class="sxs-lookup"><span data-stu-id="b1b37-653">ViCommandMode</span></span>

<span data-ttu-id="b1b37-654">Basculez le mode d’opération actuel de Vi-Insert à VI-Command.</span><span class="sxs-lookup"><span data-stu-id="b1b37-654">Switch the current operating mode from Vi-Insert to Vi-Command.</span></span>

- <span data-ttu-id="b1b37-655">Mode d’insertion VI : `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-655">Vi insert mode: `<Escape>`</span></span>

### <a name="vidigitargumentinchord"></a><span data-ttu-id="b1b37-656">ViDigitArgumentInChord</span><span class="sxs-lookup"><span data-stu-id="b1b37-656">ViDigitArgumentInChord</span></span>

<span data-ttu-id="b1b37-657">Démarrez un nouvel argument digit à passer à d’autres fonctions dans l’un des cordes de VI.</span><span class="sxs-lookup"><span data-stu-id="b1b37-657">Start a new digit argument to pass to other functions while in one of vi's chords.</span></span>

- <span data-ttu-id="b1b37-658">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="b1b37-658">Function is unbound.</span></span>

### <a name="vieditvisually"></a><span data-ttu-id="b1b37-659">ViEditVisually</span><span class="sxs-lookup"><span data-stu-id="b1b37-659">ViEditVisually</span></span>

<span data-ttu-id="b1b37-660">Modifiez la ligne de commande dans un éditeur de texte spécifié par $env : EDITOR ou $env : VISUAL.</span><span class="sxs-lookup"><span data-stu-id="b1b37-660">Edit the command line in a text editor specified by $env:EDITOR or $env:VISUAL.</span></span>

- <span data-ttu-id="b1b37-661">Emacs- `<Ctrl+x,Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-661">Emacs: `<Ctrl+x,Ctrl+e>`</span></span>
- <span data-ttu-id="b1b37-662">Mode de commande VI : `<v>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-662">Vi command mode: `<v>`</span></span>

### <a name="viexit"></a><span data-ttu-id="b1b37-663">ViExit</span><span class="sxs-lookup"><span data-stu-id="b1b37-663">ViExit</span></span>

<span data-ttu-id="b1b37-664">Quitte l’interpréteur de commandes.</span><span class="sxs-lookup"><span data-stu-id="b1b37-664">Exits the shell.</span></span>

- <span data-ttu-id="b1b37-665">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="b1b37-665">Function is unbound.</span></span>

### <a name="viinsertmode"></a><span data-ttu-id="b1b37-666">ViInsertMode</span><span class="sxs-lookup"><span data-stu-id="b1b37-666">ViInsertMode</span></span>

<span data-ttu-id="b1b37-667">Basculez en mode insertion.</span><span class="sxs-lookup"><span data-stu-id="b1b37-667">Switch to Insert mode.</span></span>

- <span data-ttu-id="b1b37-668">Mode de commande VI : `<i>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-668">Vi command mode: `<i>`</span></span>

### <a name="whatiskey"></a><span data-ttu-id="b1b37-669">WhatIsKey</span><span class="sxs-lookup"><span data-stu-id="b1b37-669">WhatIsKey</span></span>

<span data-ttu-id="b1b37-670">Lisez une clé et dites-moi à quoi la clé est liée.</span><span class="sxs-lookup"><span data-stu-id="b1b37-670">Read a key and tell me what the key is bound to.</span></span>

- <span data-ttu-id="b1b37-671">Cmd `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-671">Cmd: `<Alt+?>`</span></span>
- <span data-ttu-id="b1b37-672">Emacs- `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-672">Emacs: `<Alt+?>`</span></span>

## <a name="selection-functions"></a><span data-ttu-id="b1b37-673">Fonctions de sélection</span><span class="sxs-lookup"><span data-stu-id="b1b37-673">Selection functions</span></span>

### <a name="exchangepointandmark"></a><span data-ttu-id="b1b37-674">ExchangePointAndMark</span><span class="sxs-lookup"><span data-stu-id="b1b37-674">ExchangePointAndMark</span></span>

<span data-ttu-id="b1b37-675">Le curseur est placé à l’emplacement de la marque et la marque est déplacée vers l’emplacement du curseur.</span><span class="sxs-lookup"><span data-stu-id="b1b37-675">The cursor is placed at the location of the mark and the mark is moved to the location of the cursor.</span></span>

- <span data-ttu-id="b1b37-676">Emacs- `<Ctrl+x,Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-676">Emacs: `<Ctrl+x,Ctrl+x>`</span></span>

### <a name="selectall"></a><span data-ttu-id="b1b37-677">SelectAll</span><span class="sxs-lookup"><span data-stu-id="b1b37-677">SelectAll</span></span>

<span data-ttu-id="b1b37-678">Sélectionnez la ligne entière.</span><span class="sxs-lookup"><span data-stu-id="b1b37-678">Select the entire line.</span></span>

- <span data-ttu-id="b1b37-679">Cmd `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-679">Cmd: `<Ctrl+a>`</span></span>

### <a name="selectbackwardchar"></a><span data-ttu-id="b1b37-680">SelectBackwardChar</span><span class="sxs-lookup"><span data-stu-id="b1b37-680">SelectBackwardChar</span></span>

<span data-ttu-id="b1b37-681">Ajustez la sélection actuelle pour inclure le caractère précédent.</span><span class="sxs-lookup"><span data-stu-id="b1b37-681">Adjust the current selection to include the previous character.</span></span>

- <span data-ttu-id="b1b37-682">Cmd `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-682">Cmd: `<Shift+LeftArrow>`</span></span>
- <span data-ttu-id="b1b37-683">Emacs- `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-683">Emacs: `<Shift+LeftArrow>`</span></span>

### <a name="selectbackwardsline"></a><span data-ttu-id="b1b37-684">SelectBackwardsLine</span><span class="sxs-lookup"><span data-stu-id="b1b37-684">SelectBackwardsLine</span></span>

<span data-ttu-id="b1b37-685">Ajustez la sélection actuelle à inclure à partir du curseur jusqu’au début de la ligne.</span><span class="sxs-lookup"><span data-stu-id="b1b37-685">Adjust the current selection to include from the cursor to the start of the line.</span></span>

- <span data-ttu-id="b1b37-686">Cmd `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-686">Cmd: `<Shift+Home>`</span></span>
- <span data-ttu-id="b1b37-687">Emacs- `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-687">Emacs: `<Shift+Home>`</span></span>

### <a name="selectbackwardword"></a><span data-ttu-id="b1b37-688">SelectBackwardWord</span><span class="sxs-lookup"><span data-stu-id="b1b37-688">SelectBackwardWord</span></span>

<span data-ttu-id="b1b37-689">Ajustez la sélection actuelle pour inclure le mot précédent.</span><span class="sxs-lookup"><span data-stu-id="b1b37-689">Adjust the current selection to include the previous word.</span></span>

- <span data-ttu-id="b1b37-690">Cmd `<Shift+Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-690">Cmd: `<Shift+Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="b1b37-691">Emacs- `<Alt+B>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-691">Emacs: `<Alt+B>`</span></span>

### <a name="selectforwardchar"></a><span data-ttu-id="b1b37-692">SelectForwardChar</span><span class="sxs-lookup"><span data-stu-id="b1b37-692">SelectForwardChar</span></span>

<span data-ttu-id="b1b37-693">Ajustez la sélection actuelle pour inclure le caractère suivant.</span><span class="sxs-lookup"><span data-stu-id="b1b37-693">Adjust the current selection to include the next character.</span></span>

- <span data-ttu-id="b1b37-694">Cmd `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-694">Cmd: `<Shift+RightArrow>`</span></span>
- <span data-ttu-id="b1b37-695">Emacs- `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-695">Emacs: `<Shift+RightArrow>`</span></span>

### <a name="selectforwardword"></a><span data-ttu-id="b1b37-696">SelectForwardWord</span><span class="sxs-lookup"><span data-stu-id="b1b37-696">SelectForwardWord</span></span>

<span data-ttu-id="b1b37-697">Ajustez la sélection actuelle pour inclure le mot suivant à l’aide de ForwardWord.</span><span class="sxs-lookup"><span data-stu-id="b1b37-697">Adjust the current selection to include the next word using ForwardWord.</span></span>

- <span data-ttu-id="b1b37-698">Emacs- `<Alt+F>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-698">Emacs: `<Alt+F>`</span></span>

### <a name="selectline"></a><span data-ttu-id="b1b37-699">SelectLine</span><span class="sxs-lookup"><span data-stu-id="b1b37-699">SelectLine</span></span>

<span data-ttu-id="b1b37-700">Ajustez la sélection actuelle à inclure à partir du curseur jusqu’à la fin de la ligne.</span><span class="sxs-lookup"><span data-stu-id="b1b37-700">Adjust the current selection to include from the cursor to the end of the line.</span></span>

- <span data-ttu-id="b1b37-701">Cmd `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-701">Cmd: `<Shift+End>`</span></span>
- <span data-ttu-id="b1b37-702">Emacs- `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-702">Emacs: `<Shift+End>`</span></span>

### <a name="selectnextword"></a><span data-ttu-id="b1b37-703">SelectNextWord</span><span class="sxs-lookup"><span data-stu-id="b1b37-703">SelectNextWord</span></span>

<span data-ttu-id="b1b37-704">Ajustez la sélection actuelle pour inclure le mot suivant.</span><span class="sxs-lookup"><span data-stu-id="b1b37-704">Adjust the current selection to include the next word.</span></span>

- <span data-ttu-id="b1b37-705">Cmd `<Shift+Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-705">Cmd: `<Shift+Ctrl+RightArrow>`</span></span>

### <a name="selectshellbackwardword"></a><span data-ttu-id="b1b37-706">SelectShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="b1b37-706">SelectShellBackwardWord</span></span>

<span data-ttu-id="b1b37-707">Ajustez la sélection actuelle pour inclure le mot précédent à l’aide de ShellBackwardWord.</span><span class="sxs-lookup"><span data-stu-id="b1b37-707">Adjust the current selection to include the previous word using ShellBackwardWord.</span></span>

- <span data-ttu-id="b1b37-708">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="b1b37-708">Function is unbound.</span></span>

### <a name="selectshellforwardword"></a><span data-ttu-id="b1b37-709">SelectShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="b1b37-709">SelectShellForwardWord</span></span>

<span data-ttu-id="b1b37-710">Ajustez la sélection actuelle pour inclure le mot suivant à l’aide de ShellForwardWord.</span><span class="sxs-lookup"><span data-stu-id="b1b37-710">Adjust the current selection to include the next word using ShellForwardWord.</span></span>

- <span data-ttu-id="b1b37-711">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="b1b37-711">Function is unbound.</span></span>

### <a name="selectshellnextword"></a><span data-ttu-id="b1b37-712">SelectShellNextWord</span><span class="sxs-lookup"><span data-stu-id="b1b37-712">SelectShellNextWord</span></span>

<span data-ttu-id="b1b37-713">Ajustez la sélection actuelle pour inclure le mot suivant à l’aide de ShellNextWord.</span><span class="sxs-lookup"><span data-stu-id="b1b37-713">Adjust the current selection to include the next word using ShellNextWord.</span></span>

- <span data-ttu-id="b1b37-714">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="b1b37-714">Function is unbound.</span></span>

### <a name="setmark"></a><span data-ttu-id="b1b37-715">SetMark</span><span class="sxs-lookup"><span data-stu-id="b1b37-715">SetMark</span></span>

<span data-ttu-id="b1b37-716">Marquez l’emplacement actuel du curseur pour une utilisation dans une commande d’édition suivante.</span><span class="sxs-lookup"><span data-stu-id="b1b37-716">Mark the current location of the cursor for use in a subsequent editing command.</span></span>

- <span data-ttu-id="b1b37-717">Emacs- `<Ctrl+`>\`</span><span class="sxs-lookup"><span data-stu-id="b1b37-717">Emacs: `<Ctrl+`>\`</span></span>

## <a name="search-functions"></a><span data-ttu-id="b1b37-718">Fonctions de recherche</span><span class="sxs-lookup"><span data-stu-id="b1b37-718">Search functions</span></span>

### <a name="charactersearch"></a><span data-ttu-id="b1b37-719">CharacterSearch</span><span class="sxs-lookup"><span data-stu-id="b1b37-719">CharacterSearch</span></span>

<span data-ttu-id="b1b37-720">Lisez un caractère et recherchez l’occurrence suivante de ce caractère.</span><span class="sxs-lookup"><span data-stu-id="b1b37-720">Read a character and search forward for the next occurrence of that character.</span></span>
<span data-ttu-id="b1b37-721">Si un argument est spécifié, effectuez une recherche vers l’avant (ou vers l’arrière si négatif) pour la nième occurrence.</span><span class="sxs-lookup"><span data-stu-id="b1b37-721">If an argument is specified, search forward (or backward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="b1b37-722">Cmd `<F3>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-722">Cmd: `<F3>`</span></span>
- <span data-ttu-id="b1b37-723">Emacs- `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-723">Emacs: `<Ctrl+]>`</span></span>
- <span data-ttu-id="b1b37-724">Mode d’insertion VI : `<F3>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-724">Vi insert mode: `<F3>`</span></span>
- <span data-ttu-id="b1b37-725">Mode de commande VI : `<F3>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-725">Vi command mode: `<F3>`</span></span>

### <a name="charactersearchbackward"></a><span data-ttu-id="b1b37-726">CharacterSearchBackward</span><span class="sxs-lookup"><span data-stu-id="b1b37-726">CharacterSearchBackward</span></span>

<span data-ttu-id="b1b37-727">Lisez un caractère et recherchez l’occurrence suivante de ce caractère.</span><span class="sxs-lookup"><span data-stu-id="b1b37-727">Read a character and search backward for the next occurrence of that character.</span></span> <span data-ttu-id="b1b37-728">Si un argument est spécifié, effectuez une recherche vers l’arrière (ou vers l’avant si négatif) pour la nième occurrence.</span><span class="sxs-lookup"><span data-stu-id="b1b37-728">If an argument is specified, search backward (or forward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="b1b37-729">Cmd `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-729">Cmd: `<Shift+F3>`</span></span>
- <span data-ttu-id="b1b37-730">Emacs- `<Ctrl+Alt+]>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-730">Emacs: `<Ctrl+Alt+]>`</span></span>
- <span data-ttu-id="b1b37-731">Mode d’insertion VI : `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-731">Vi insert mode: `<Shift+F3>`</span></span>
- <span data-ttu-id="b1b37-732">Mode de commande VI : `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-732">Vi command mode: `<Shift+F3>`</span></span>

### <a name="repeatlastcharsearch"></a><span data-ttu-id="b1b37-733">RepeatLastCharSearch</span><span class="sxs-lookup"><span data-stu-id="b1b37-733">RepeatLastCharSearch</span></span>

<span data-ttu-id="b1b37-734">Répète la dernière recherche de caractères enregistrée.</span><span class="sxs-lookup"><span data-stu-id="b1b37-734">Repeat the last recorded character search.</span></span>

- <span data-ttu-id="b1b37-735">Mode de commande VI : `<;>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-735">Vi command mode: `<;>`</span></span>

### <a name="repeatlastcharsearchbackwards"></a><span data-ttu-id="b1b37-736">RepeatLastCharSearchBackwards</span><span class="sxs-lookup"><span data-stu-id="b1b37-736">RepeatLastCharSearchBackwards</span></span>

<span data-ttu-id="b1b37-737">Répète la dernière recherche de caractères enregistrée, mais dans la direction opposée.</span><span class="sxs-lookup"><span data-stu-id="b1b37-737">Repeat the last recorded character search, but in the opposite direction.</span></span>

- <span data-ttu-id="b1b37-738">Mode de commande VI : `<,>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-738">Vi command mode: `<,>`</span></span>

### <a name="repeatsearch"></a><span data-ttu-id="b1b37-739">RepeatSearch</span><span class="sxs-lookup"><span data-stu-id="b1b37-739">RepeatSearch</span></span>

<span data-ttu-id="b1b37-740">Répétez la dernière recherche dans la même direction que précédemment.</span><span class="sxs-lookup"><span data-stu-id="b1b37-740">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="b1b37-741">Mode de commande VI : `<n>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-741">Vi command mode: `<n>`</span></span>

### <a name="repeatsearchbackward"></a><span data-ttu-id="b1b37-742">RepeatSearchBackward</span><span class="sxs-lookup"><span data-stu-id="b1b37-742">RepeatSearchBackward</span></span>

<span data-ttu-id="b1b37-743">Répétez la dernière recherche dans la même direction que précédemment.</span><span class="sxs-lookup"><span data-stu-id="b1b37-743">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="b1b37-744">Mode de commande VI : `<N>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-744">Vi command mode: `<N>`</span></span>

### <a name="searchchar"></a><span data-ttu-id="b1b37-745">SearchChar</span><span class="sxs-lookup"><span data-stu-id="b1b37-745">SearchChar</span></span>

<span data-ttu-id="b1b37-746">Lisez le caractère suivant, puis recherchez-le, à l’avenir, puis annulez un caractère.</span><span class="sxs-lookup"><span data-stu-id="b1b37-746">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="b1b37-747">Il s’agit de la fonctionnalité’t'.</span><span class="sxs-lookup"><span data-stu-id="b1b37-747">This is for 't' functionality.</span></span>

- <span data-ttu-id="b1b37-748">Mode de commande VI : `<f>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-748">Vi command mode: `<f>`</span></span>

### <a name="searchcharbackward"></a><span data-ttu-id="b1b37-749">SearchCharBackward</span><span class="sxs-lookup"><span data-stu-id="b1b37-749">SearchCharBackward</span></span>

<span data-ttu-id="b1b37-750">Lisez le caractère suivant, puis recherchez-le, en accédant à l’arrière, puis en annulant un caractère.</span><span class="sxs-lookup"><span data-stu-id="b1b37-750">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="b1b37-751">Il s’agit de la fonctionnalité’t'.</span><span class="sxs-lookup"><span data-stu-id="b1b37-751">This is for 'T' functionality.</span></span>

- <span data-ttu-id="b1b37-752">Mode de commande VI : `<F>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-752">Vi command mode: `<F>`</span></span>

### <a name="searchcharbackwardwithbackoff"></a><span data-ttu-id="b1b37-753">SearchCharBackwardWithBackoff</span><span class="sxs-lookup"><span data-stu-id="b1b37-753">SearchCharBackwardWithBackoff</span></span>

<span data-ttu-id="b1b37-754">Lisez le caractère suivant, puis recherchez-le, en accédant à l’arrière, puis en annulant un caractère.</span><span class="sxs-lookup"><span data-stu-id="b1b37-754">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="b1b37-755">Il s’agit de la fonctionnalité’t'.</span><span class="sxs-lookup"><span data-stu-id="b1b37-755">This is for 'T' functionality.</span></span>

- <span data-ttu-id="b1b37-756">Mode de commande VI : `<T>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-756">Vi command mode: `<T>`</span></span>

### <a name="searchcharwithbackoff"></a><span data-ttu-id="b1b37-757">SearchCharWithBackoff</span><span class="sxs-lookup"><span data-stu-id="b1b37-757">SearchCharWithBackoff</span></span>

<span data-ttu-id="b1b37-758">Lisez le caractère suivant, puis recherchez-le, à l’avenir, puis annulez un caractère.</span><span class="sxs-lookup"><span data-stu-id="b1b37-758">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="b1b37-759">Il s’agit de la fonctionnalité’t'.</span><span class="sxs-lookup"><span data-stu-id="b1b37-759">This is for 't' functionality.</span></span>

- <span data-ttu-id="b1b37-760">Mode de commande VI : `<t>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-760">Vi command mode: `<t>`</span></span>

### <a name="searchforward"></a><span data-ttu-id="b1b37-761">SearchForward</span><span class="sxs-lookup"><span data-stu-id="b1b37-761">SearchForward</span></span>

<span data-ttu-id="b1b37-762">Demande une chaîne de recherche et lance la recherche sur AcceptLine.</span><span class="sxs-lookup"><span data-stu-id="b1b37-762">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="b1b37-763">Mode d’insertion VI : `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-763">Vi insert mode: `<Ctrl+s>`</span></span>
- <span data-ttu-id="b1b37-764">Mode de commande VI : `<?>` , `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="b1b37-764">Vi command mode: `<?>`, `<Ctrl+s>`</span></span>

## <a name="custom-key-bindings"></a><span data-ttu-id="b1b37-765">Combinaisons de touches personnalisées</span><span class="sxs-lookup"><span data-stu-id="b1b37-765">Custom Key Bindings</span></span>

<span data-ttu-id="b1b37-766">PSReadLine prend en charge les combinaisons de touches personnalisées à l’aide de l’applet de commande `Set-PSReadLineKeyHandler` .</span><span class="sxs-lookup"><span data-stu-id="b1b37-766">PSReadLine supports custom key bindings using the cmdlet `Set-PSReadLineKeyHandler`.</span></span> <span data-ttu-id="b1b37-767">La plupart des combinaisons de touches personnalisées appellent l’une des fonctions ci-dessus, par exemple</span><span class="sxs-lookup"><span data-stu-id="b1b37-767">Most custom key bindings call one of the above functions, for example</span></span>

```powershell
Set-PSReadLineKeyHandler -Key UpArrow -Function HistorySearchBackward
```

<span data-ttu-id="b1b37-768">Vous pouvez lier un ScriptBlock à une clé.</span><span class="sxs-lookup"><span data-stu-id="b1b37-768">You can bind a ScriptBlock to a key.</span></span> <span data-ttu-id="b1b37-769">Le ScriptBlock peut faire à peu près tout ce que vous voulez.</span><span class="sxs-lookup"><span data-stu-id="b1b37-769">The ScriptBlock can do pretty much anything you want.</span></span> <span data-ttu-id="b1b37-770">Voici quelques exemples utiles :</span><span class="sxs-lookup"><span data-stu-id="b1b37-770">Some useful examples include</span></span>

- <span data-ttu-id="b1b37-771">modifier la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="b1b37-771">edit the command line</span></span>
- <span data-ttu-id="b1b37-772">ouverture d’une nouvelle fenêtre (par exemple, aide)</span><span class="sxs-lookup"><span data-stu-id="b1b37-772">opening a new window (e.g. help)</span></span>
- <span data-ttu-id="b1b37-773">modifier les répertoires sans modifier la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="b1b37-773">change directories without changing the command line</span></span>

<span data-ttu-id="b1b37-774">Le ScriptBlock reçoit deux arguments :</span><span class="sxs-lookup"><span data-stu-id="b1b37-774">The ScriptBlock receives two arguments:</span></span>

- <span data-ttu-id="b1b37-775">`$key` -Objet **[ConsoleKeyInfo]** qui est la clé qui a déclenché la liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="b1b37-775">`$key` - A **[ConsoleKeyInfo]** object that is the key that triggered the custom binding.</span></span> <span data-ttu-id="b1b37-776">Si vous liez le même ScriptBlock à plusieurs clés et que vous devez effectuer des actions différentes en fonction de la clé, vous pouvez vérifier $key.</span><span class="sxs-lookup"><span data-stu-id="b1b37-776">If you bind the same ScriptBlock to multiple keys and need to perform different actions depending on the key, you can check $key.</span></span> <span data-ttu-id="b1b37-777">De nombreuses liaisons personnalisées ignorent cet argument.</span><span class="sxs-lookup"><span data-stu-id="b1b37-777">Many custom bindings ignore this argument.</span></span>

- <span data-ttu-id="b1b37-778">`$arg` : Argument arbitraire.</span><span class="sxs-lookup"><span data-stu-id="b1b37-778">`$arg` - An arbitrary argument.</span></span> <span data-ttu-id="b1b37-779">Le plus souvent, il s’agit d’un argument entier que l’utilisateur passe à partir des combinaisons de touches DigitArgument.</span><span class="sxs-lookup"><span data-stu-id="b1b37-779">Most often, this would be an integer argument that the user passes from the key bindings DigitArgument.</span></span> <span data-ttu-id="b1b37-780">Si votre liaison n’accepte pas d’arguments, il est raisonnable d’ignorer cet argument.</span><span class="sxs-lookup"><span data-stu-id="b1b37-780">If your binding doesn't accept arguments, it's reasonable to ignore this argument.</span></span>

<span data-ttu-id="b1b37-781">Jetons un coup d’œil à un exemple qui ajoute une ligne de commande à l’historique sans l’exécuter.</span><span class="sxs-lookup"><span data-stu-id="b1b37-781">Let's take a look at an example that adds a command line to history without executing it.</span></span> <span data-ttu-id="b1b37-782">Cela est utile lorsque vous vous rendez compte que vous avez oublié d’effectuer une opération, mais que vous ne voulez pas entrer à nouveau la ligne de commande que vous avez déjà entrée.</span><span class="sxs-lookup"><span data-stu-id="b1b37-782">This is useful when you realize you forgot to do something, but don't want to re-enter the command line you've already entered.</span></span>

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

<span data-ttu-id="b1b37-783">Vous pouvez voir beaucoup plus d’exemples dans le fichier `SamplePSReadLineProfile.ps1` qui est installé dans le dossier du module PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="b1b37-783">You can see many more examples in the file `SamplePSReadLineProfile.ps1` which is installed in the PSReadLine module folder.</span></span>

<span data-ttu-id="b1b37-784">La plupart des combinaisons de touches utilisent des fonctions d’assistance pour la modification de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="b1b37-784">Most key bindings use some helper functions for editing the command line.</span></span>
<span data-ttu-id="b1b37-785">Ces API sont documentées dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="b1b37-785">Those APIs are documented in the next section.</span></span>

## <a name="custom-key-binding-support-apis"></a><span data-ttu-id="b1b37-786">API de prise en charge de la liaison de clé personnalisée</span><span class="sxs-lookup"><span data-stu-id="b1b37-786">Custom Key Binding Support APIs</span></span>

<span data-ttu-id="b1b37-787">Les fonctions suivantes sont publiques dans Microsoft. PowerShell. PSConsoleReadLine, mais ne peuvent pas être directement liées à une clé.</span><span class="sxs-lookup"><span data-stu-id="b1b37-787">The following functions are public in Microsoft.PowerShell.PSConsoleReadLine, but cannot be directly bound to a key.</span></span> <span data-ttu-id="b1b37-788">La plupart sont utiles dans les combinaisons de touches personnalisées.</span><span class="sxs-lookup"><span data-stu-id="b1b37-788">Most are useful in custom key bindings.</span></span>

```csharp
void AddToHistory(string command)
```

<span data-ttu-id="b1b37-789">Ajoutez une ligne de commande à l’historique sans l’exécuter.</span><span class="sxs-lookup"><span data-stu-id="b1b37-789">Add a command line to history without executing it.</span></span>

```csharp
void ClearKillRing()
```

<span data-ttu-id="b1b37-790">Effacez le point d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="b1b37-790">Clear the kill-ring.</span></span>  <span data-ttu-id="b1b37-791">Cela est principalement utilisé pour les tests.</span><span class="sxs-lookup"><span data-stu-id="b1b37-791">This is mostly used for testing.</span></span>

```csharp
void Delete(int start, int length)
```

<span data-ttu-id="b1b37-792">Supprimer les caractères de longueur du début.</span><span class="sxs-lookup"><span data-stu-id="b1b37-792">Delete length characters from start.</span></span>  <span data-ttu-id="b1b37-793">Cette opération prend en charge les opérations d’annulation et de rétablissement.</span><span class="sxs-lookup"><span data-stu-id="b1b37-793">This operation supports undo/redo.</span></span>

```csharp
void Ding()
```

<span data-ttu-id="b1b37-794">Effectuez l’action Ding en fonction des préférences de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b1b37-794">Perform the Ding action based on the users preference.</span></span>

```csharp
void GetBufferState([ref] string input, [ref] int cursor)
void GetBufferState([ref] Ast ast, [ref] Token[] tokens,
  [ref] ParseError[] parseErrors, [ref] int cursor)
```

<span data-ttu-id="b1b37-795">Ces deux fonctions récupèrent des informations utiles sur l’état actuel de la mémoire tampon d’entrée.</span><span class="sxs-lookup"><span data-stu-id="b1b37-795">These two functions retrieve useful information about the current state of the input buffer.</span></span>  <span data-ttu-id="b1b37-796">La première est plus couramment utilisée dans les cas simples.</span><span class="sxs-lookup"><span data-stu-id="b1b37-796">The first is more commonly used for simple cases.</span></span>  <span data-ttu-id="b1b37-797">Le second est utilisé si votre liaison fait une opération plus avancée avec l’AST.</span><span class="sxs-lookup"><span data-stu-id="b1b37-797">The second is used if your binding is doing something more advanced with the Ast.</span></span>

```csharp
IEnumerable[Microsoft.PowerShell.KeyHandler]
  GetKeyHandlers(bool includeBound, bool includeUnbound)

```

<span data-ttu-id="b1b37-798">Cette fonction est utilisée par Get-PSReadLineKeyHandler et n’est probablement pas utile dans une combinaison de touches personnalisée.</span><span class="sxs-lookup"><span data-stu-id="b1b37-798">This function is used by Get-PSReadLineKeyHandler and probably isn't useful in a custom key binding.</span></span>

```csharp
Microsoft.PowerShell.PSConsoleReadLineOptions GetOptions()
```

<span data-ttu-id="b1b37-799">Cette fonction est utilisée par Get-PSReadLineOption et n’est probablement pas trop utile dans une liaison de clé personnalisée.</span><span class="sxs-lookup"><span data-stu-id="b1b37-799">This function is used by Get-PSReadLineOption and probably isn't too useful in a custom key binding.</span></span>

```csharp
void GetSelectionState([ref] int start, [ref] int length)
```

<span data-ttu-id="b1b37-800">Si aucune sélection n’est effectuée sur la ligne de commande,-1 est retourné à la fois en début et en longueur.</span><span class="sxs-lookup"><span data-stu-id="b1b37-800">If there is no selection on the command line, -1 will be returned in both start and length.</span></span> <span data-ttu-id="b1b37-801">Si une sélection est effectuée sur la ligne de commande, le début et la longueur de la sélection sont retournés.</span><span class="sxs-lookup"><span data-stu-id="b1b37-801">If there is a selection on the command line, the start and length of the selection are returned.</span></span>

```csharp
void Insert(char c)
void Insert(string s)
```

<span data-ttu-id="b1b37-802">Insérez un caractère ou une chaîne au niveau du curseur.</span><span class="sxs-lookup"><span data-stu-id="b1b37-802">Insert a character or string at the cursor.</span></span>  <span data-ttu-id="b1b37-803">Cette opération prend en charge les opérations d’annulation et de rétablissement.</span><span class="sxs-lookup"><span data-stu-id="b1b37-803">This operation supports undo/redo.</span></span>

```csharp
string ReadLine(runspace remoteRunspace,
  System.Management.Automation.EngineIntrinsics engineIntrinsics)
```

<span data-ttu-id="b1b37-804">Il s’agit du point d’entrée principal de PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="b1b37-804">This is the main entry point to PSReadLine.</span></span> <span data-ttu-id="b1b37-805">Comme il ne prend pas en charge la récursivité, il n’est pas utile dans une liaison de clé personnalisée.</span><span class="sxs-lookup"><span data-stu-id="b1b37-805">It does not support recursion, so is not useful in a custom key binding.</span></span>

```csharp
void RemoveKeyHandler(string[] key)
```

<span data-ttu-id="b1b37-806">Cette fonction est utilisée par Remove-PSReadLineKeyHandler et n’est probablement pas trop utile dans une liaison de clé personnalisée.</span><span class="sxs-lookup"><span data-stu-id="b1b37-806">This function is used by Remove-PSReadLineKeyHandler and probably isn't too useful in a custom key binding.</span></span>

```csharp
void Replace(int start, int length, string replacement)
```

<span data-ttu-id="b1b37-807">Remplacez une partie de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="b1b37-807">Replace some of the input.</span></span> <span data-ttu-id="b1b37-808">Cette opération prend en charge les opérations d’annulation et de rétablissement.</span><span class="sxs-lookup"><span data-stu-id="b1b37-808">This operation supports undo/redo.</span></span> <span data-ttu-id="b1b37-809">C’est préférable à Delete, suivi de Insert, car il est traité comme une action unique pour Undo.</span><span class="sxs-lookup"><span data-stu-id="b1b37-809">This is preferred over Delete followed by Insert because it is treated as a single action for undo.</span></span>

```csharp
void SetCursorPosition(int cursor)
```

<span data-ttu-id="b1b37-810">Déplacer le curseur vers l’offset donné.</span><span class="sxs-lookup"><span data-stu-id="b1b37-810">Move the cursor to the given offset.</span></span> <span data-ttu-id="b1b37-811">Le déplacement du curseur n’est pas suivi pour l’annulation.</span><span class="sxs-lookup"><span data-stu-id="b1b37-811">Cursor movement is not tracked for undo.</span></span>

```csharp
void SetOptions(Microsoft.PowerShell.SetPSReadLineOption options)
```

<span data-ttu-id="b1b37-812">Cette fonction est une méthode d’assistance utilisée par l’applet de commande Set-PSReadLineOption, mais peut être utile pour une combinaison de touches personnalisée qui souhaite modifier temporairement un paramètre.</span><span class="sxs-lookup"><span data-stu-id="b1b37-812">This function is a helper method used by the cmdlet Set-PSReadLineOption, but might be useful to a custom key binding that wants to temporarily change a setting.</span></span>

```csharp
bool TryGetArgAsInt(System.Object arg, [ref] int numericArg,
  int defaultNumericArg)
```

<span data-ttu-id="b1b37-813">Cette méthode d’assistance est utilisée pour les liaisons personnalisées qui respectent DigitArgument.</span><span class="sxs-lookup"><span data-stu-id="b1b37-813">This helper method is used for custom bindings that honor DigitArgument.</span></span> <span data-ttu-id="b1b37-814">Un appel classique ressemble à ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="b1b37-814">A typical call looks like</span></span>

```powershell
[int]$numericArg = 0
[Microsoft.PowerShell.PSConsoleReadLine]::TryGetArgAsInt($arg,
  [ref]$numericArg, 1)
```

## <a name="note"></a><span data-ttu-id="b1b37-815">Notes</span><span class="sxs-lookup"><span data-stu-id="b1b37-815">Note</span></span>

### <a name="command-history"></a><span data-ttu-id="b1b37-816">Historique des commandes</span><span class="sxs-lookup"><span data-stu-id="b1b37-816">Command History</span></span>

<span data-ttu-id="b1b37-817">PSReadLine gère un fichier d’historique contenant toutes les commandes et données que vous avez entrées à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="b1b37-817">PSReadLine maintains a history file containing all the commands and data you have entered from the command line.</span></span> <span data-ttu-id="b1b37-818">Cela peut contenir des données sensibles, y compris des mots de passe.</span><span class="sxs-lookup"><span data-stu-id="b1b37-818">This may contain sensitive data including passwords.</span></span> <span data-ttu-id="b1b37-819">Par exemple, si vous utilisez l’applet de commande, `ConvertTo-SecureString` le mot de passe est enregistré dans le fichier d’historique sous forme de texte brut.</span><span class="sxs-lookup"><span data-stu-id="b1b37-819">For example, if you use the `ConvertTo-SecureString` cmdlet the password is logged in the history file as plain text.</span></span> <span data-ttu-id="b1b37-820">Les fichiers d’historique sont un fichier nommé `$($host.Name)_history.txt` .</span><span class="sxs-lookup"><span data-stu-id="b1b37-820">The history files is a file named `$($host.Name)_history.txt`.</span></span> <span data-ttu-id="b1b37-821">Sur les systèmes Windows, le fichier d’historique est stocké à l’adresse `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine` .</span><span class="sxs-lookup"><span data-stu-id="b1b37-821">On Windows systems the history file is stored at `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine`.</span></span>

### <a name="feedback--contributing-to-psreadline"></a><span data-ttu-id="b1b37-822">Commentaires & contribution à PSReadLine</span><span class="sxs-lookup"><span data-stu-id="b1b37-822">Feedback & Contributing To PSReadLine</span></span>

[<span data-ttu-id="b1b37-823">PSReadLine sur GitHub</span><span class="sxs-lookup"><span data-stu-id="b1b37-823">PSReadLine on GitHub</span></span>](https://github.com/PowerShell/PSReadLine)

<span data-ttu-id="b1b37-824">N’hésitez pas à envoyer une demande de tirage ou à envoyer des commentaires sur la page GitHub.</span><span class="sxs-lookup"><span data-stu-id="b1b37-824">Feel free to submit a pull request or submit feedback on the GitHub page.</span></span>

## <a name="see-also"></a><span data-ttu-id="b1b37-825">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b1b37-825">See Also</span></span>

<span data-ttu-id="b1b37-826">PSReadLine est fortement influencé par la bibliothèque GNU [ReadLine](https://tiswww.case.edu/php/chet/readline/rltop.html) .</span><span class="sxs-lookup"><span data-stu-id="b1b37-826">PSReadLine is heavily influenced by the GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) library.</span></span>
