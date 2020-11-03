---
description: PSReadLine fournit une expérience d’édition de ligne de commande améliorée dans la console PowerShell.
keywords: powershell
Locale: en-US
ms.date: 02/10/2020
online version: https://docs.microsoft.com/powershell/module/psreadline/about/about_psreadline?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: À propos de PSReadLine
ms.openlocfilehash: ad6e85a30f866cb332c89a4c36f42231f511f5ae
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2020
ms.locfileid: "93208746"
---
# <a name="psreadline"></a><span data-ttu-id="ffb17-104">PSReadLine</span><span class="sxs-lookup"><span data-stu-id="ffb17-104">PSReadLine</span></span>

## <a name="about_psreadline"></a><span data-ttu-id="ffb17-105">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="ffb17-105">about_PSReadLine</span></span>

## <a name="short-description"></a><span data-ttu-id="ffb17-106">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="ffb17-106">SHORT DESCRIPTION</span></span>

<span data-ttu-id="ffb17-107">PSReadLine fournit une expérience d’édition de ligne de commande améliorée dans la console PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ffb17-107">PSReadLine provides an improved command-line editing experience in the PowerShell console.</span></span>

## <a name="long-description"></a><span data-ttu-id="ffb17-108">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="ffb17-108">LONG DESCRIPTION</span></span>

<span data-ttu-id="ffb17-109">PSReadLine 2,0 fournit une expérience d’édition de ligne de commande puissante pour la console PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ffb17-109">PSReadLine 2.0 provides a powerful command-line editing experience for the PowerShell console.</span></span> <span data-ttu-id="ffb17-110">Elle offre les possibilités suivantes :</span><span class="sxs-lookup"><span data-stu-id="ffb17-110">It provides:</span></span>

- <span data-ttu-id="ffb17-111">Coloration de la syntaxe de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="ffb17-111">Syntax coloring of the command line</span></span>
- <span data-ttu-id="ffb17-112">Indication visuelle des erreurs de syntaxe</span><span class="sxs-lookup"><span data-stu-id="ffb17-112">A visual indication of syntax errors</span></span>
- <span data-ttu-id="ffb17-113">Une meilleure expérience multi-ligne (modification et historique)</span><span class="sxs-lookup"><span data-stu-id="ffb17-113">A better multi-line experience (both editing and history)</span></span>
- <span data-ttu-id="ffb17-114">Combinaisons de touches personnalisables</span><span class="sxs-lookup"><span data-stu-id="ffb17-114">Customizable key bindings</span></span>
- <span data-ttu-id="ffb17-115">Modes cmd et Emacs</span><span class="sxs-lookup"><span data-stu-id="ffb17-115">Cmd and Emacs modes</span></span>
- <span data-ttu-id="ffb17-116">Nombreuses options de configuration</span><span class="sxs-lookup"><span data-stu-id="ffb17-116">Many configuration options</span></span>
- <span data-ttu-id="ffb17-117">Saisie semi-automatique du style bash (facultatif en mode cmd, par défaut en mode emacs)</span><span class="sxs-lookup"><span data-stu-id="ffb17-117">Bash style completion (optional in Cmd mode, default in Emacs mode)</span></span>
- <span data-ttu-id="ffb17-118">Emacs-Yank/Kill-Ring</span><span class="sxs-lookup"><span data-stu-id="ffb17-118">Emacs yank/kill-ring</span></span>
- <span data-ttu-id="ffb17-119">Mouvement « mot » basé sur un jeton PowerShell et Kill</span><span class="sxs-lookup"><span data-stu-id="ffb17-119">PowerShell token based "word" movement and kill</span></span>

<span data-ttu-id="ffb17-120">Les fonctions suivantes sont disponibles dans la classe **[Microsoft. PowerShell. PSConsoleReadLine]** .</span><span class="sxs-lookup"><span data-stu-id="ffb17-120">The following functions are available in the class **[Microsoft.PowerShell.PSConsoleReadLine]** .</span></span>

## <a name="basic-editing-functions"></a><span data-ttu-id="ffb17-121">Fonctions d’édition de base</span><span class="sxs-lookup"><span data-stu-id="ffb17-121">Basic editing functions</span></span>

### <a name="abort"></a><span data-ttu-id="ffb17-122">Abandon</span><span class="sxs-lookup"><span data-stu-id="ffb17-122">Abort</span></span>

<span data-ttu-id="ffb17-123">Annuler l’action en cours, par exemple, recherche de l’historique incrémentiel.</span><span class="sxs-lookup"><span data-stu-id="ffb17-123">Abort current action, e.g. incremental history search.</span></span>

- <span data-ttu-id="ffb17-124">Emacs- `<Ctrl+g>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-124">Emacs: `<Ctrl+g>`</span></span>

### <a name="acceptandgetnext"></a><span data-ttu-id="ffb17-125">AcceptAndGetNext</span><span class="sxs-lookup"><span data-stu-id="ffb17-125">AcceptAndGetNext</span></span>

<span data-ttu-id="ffb17-126">Tentative d’exécution de l’entrée en cours.</span><span class="sxs-lookup"><span data-stu-id="ffb17-126">Attempt to execute the current input.</span></span> <span data-ttu-id="ffb17-127">Si elle peut être exécutée (par exemple, AcceptLine), rappelez l’élément suivant de l’historique la prochaine fois que ReadLine est appelé.</span><span class="sxs-lookup"><span data-stu-id="ffb17-127">If it can be executed (like AcceptLine), then recall the next item from history the next time ReadLine is called.</span></span>

- <span data-ttu-id="ffb17-128">Emacs- `<Ctrl+o>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-128">Emacs: `<Ctrl+o>`</span></span>

### <a name="acceptline"></a><span data-ttu-id="ffb17-129">AcceptLine</span><span class="sxs-lookup"><span data-stu-id="ffb17-129">AcceptLine</span></span>

<span data-ttu-id="ffb17-130">Tentative d’exécution de l’entrée en cours.</span><span class="sxs-lookup"><span data-stu-id="ffb17-130">Attempt to execute the current input.</span></span> <span data-ttu-id="ffb17-131">Si l’entrée actuelle est incomplète (par exemple, il manque une parenthèse fermante, un crochet ou un guillemet, l’invite de continuation est affichée sur la ligne suivante et PSReadLine attend que les clés modifient l’entrée actuelle.</span><span class="sxs-lookup"><span data-stu-id="ffb17-131">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="ffb17-132">Cmd `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-132">Cmd: `<Enter>`</span></span>
- <span data-ttu-id="ffb17-133">Emacs- `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-133">Emacs: `<Enter>`</span></span>
- <span data-ttu-id="ffb17-134">Mode d’insertion VI : `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-134">Vi insert mode: `<Enter>`</span></span>

### <a name="addline"></a><span data-ttu-id="ffb17-135">AddLine</span><span class="sxs-lookup"><span data-stu-id="ffb17-135">AddLine</span></span>

<span data-ttu-id="ffb17-136">L’invite de continuation est affichée sur la ligne suivante et PSReadLine attend que les clés modifient l’entrée actuelle.</span><span class="sxs-lookup"><span data-stu-id="ffb17-136">The continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span> <span data-ttu-id="ffb17-137">Cela est utile pour entrer une entrée multiligne sous la forme d’une commande unique, même lorsqu’une seule ligne est complète en entrée.</span><span class="sxs-lookup"><span data-stu-id="ffb17-137">This is useful to enter multi-line input as a single command even when a single line is complete input by itself.</span></span>

- <span data-ttu-id="ffb17-138">Cmd `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-138">Cmd: `<Shift+Enter>`</span></span>
- <span data-ttu-id="ffb17-139">Emacs- `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-139">Emacs: `<Shift+Enter>`</span></span>
- <span data-ttu-id="ffb17-140">Mode d’insertion VI : `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-140">Vi insert mode: `<Shift+Enter>`</span></span>
- <span data-ttu-id="ffb17-141">Mode de commande VI : `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-141">Vi command mode: `<Shift+Enter>`</span></span>

### <a name="backwarddeletechar"></a><span data-ttu-id="ffb17-142">BackwardDeleteChar</span><span class="sxs-lookup"><span data-stu-id="ffb17-142">BackwardDeleteChar</span></span>

<span data-ttu-id="ffb17-143">Supprimez le caractère avant le curseur.</span><span class="sxs-lookup"><span data-stu-id="ffb17-143">Delete the character before the cursor.</span></span>

- <span data-ttu-id="ffb17-144">Cmd : `<Backspace>` , `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-144">Cmd: `<Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="ffb17-145">Emacs : `<Backspace>` , `<Ctrl+Backspace>` , `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-145">Emacs: `<Backspace>`, `<Ctrl+Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="ffb17-146">Mode d’insertion VI : `<Backspace>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-146">Vi insert mode: `<Backspace>`</span></span>
- <span data-ttu-id="ffb17-147">Mode de commande VI : `<X>` , `<d,h>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-147">Vi command mode: `<X>`, `<d,h>`</span></span>

### <a name="backwarddeleteline"></a><span data-ttu-id="ffb17-148">BackwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="ffb17-148">BackwardDeleteLine</span></span>

<span data-ttu-id="ffb17-149">Comme BackwardKillLine-supprime le texte du point jusqu’au début de la ligne, mais ne place pas le texte supprimé dans l’anneau d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="ffb17-149">Like BackwardKillLine - deletes text from the point to the start of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="ffb17-150">Cmd `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-150">Cmd: `<Ctrl+Home>`</span></span>
- <span data-ttu-id="ffb17-151">Mode d’insertion VI : `<Ctrl+u>` , `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-151">Vi insert mode: `<Ctrl+u>`, `<Ctrl+Home>`</span></span>
- <span data-ttu-id="ffb17-152">Mode de commande VI : `<Ctrl+u>` , `<Ctrl+Home>` , `<d,0>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-152">Vi command mode: `<Ctrl+u>`, `<Ctrl+Home>`, `<d,0>`</span></span>

### <a name="backwarddeleteword"></a><span data-ttu-id="ffb17-153">BackwardDeleteWord</span><span class="sxs-lookup"><span data-stu-id="ffb17-153">BackwardDeleteWord</span></span>

<span data-ttu-id="ffb17-154">Supprime le mot précédent.</span><span class="sxs-lookup"><span data-stu-id="ffb17-154">Deletes the previous word.</span></span>

- <span data-ttu-id="ffb17-155">Mode de commande VI : `<Ctrl+w>` , `<d,b>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-155">Vi command mode: `<Ctrl+w>`, `<d,b>`</span></span>

### <a name="backwardkillline"></a><span data-ttu-id="ffb17-156">BackwardKillLine</span><span class="sxs-lookup"><span data-stu-id="ffb17-156">BackwardKillLine</span></span>

<span data-ttu-id="ffb17-157">Effacez l’entrée à partir du début de l’entrée jusqu’au curseur.</span><span class="sxs-lookup"><span data-stu-id="ffb17-157">Clear the input from the start of the input to the cursor.</span></span> <span data-ttu-id="ffb17-158">Le texte effacé est placé dans le Kill-Ring.</span><span class="sxs-lookup"><span data-stu-id="ffb17-158">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="ffb17-159">Emacs- `<Ctrl+u>` , `<Ctrl+x,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-159">Emacs: `<Ctrl+u>`, `<Ctrl+x,Backspace>`</span></span>

### <a name="backwardkillword"></a><span data-ttu-id="ffb17-160">BackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="ffb17-160">BackwardKillWord</span></span>

<span data-ttu-id="ffb17-161">Efface l’entrée du début du mot actuel jusqu’au curseur.</span><span class="sxs-lookup"><span data-stu-id="ffb17-161">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="ffb17-162">Si le curseur se trouve entre des mots, l’entrée est effacée du début du mot précédent au curseur.</span><span class="sxs-lookup"><span data-stu-id="ffb17-162">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="ffb17-163">Le texte effacé est placé dans le Kill-Ring.</span><span class="sxs-lookup"><span data-stu-id="ffb17-163">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="ffb17-164">Cmd `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-164">Cmd: `<Ctrl+Backspace>`</span></span>
- <span data-ttu-id="ffb17-165">Emacs- `<Alt+Backspace>` , `<Escape,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-165">Emacs: `<Alt+Backspace>`, `<Escape,Backspace>`</span></span>
- <span data-ttu-id="ffb17-166">Mode d’insertion VI : `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-166">Vi insert mode: `<Ctrl+Backspace>`</span></span>
- <span data-ttu-id="ffb17-167">Mode de commande VI : `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-167">Vi command mode: `<Ctrl+Backspace>`</span></span>

### <a name="cancelline"></a><span data-ttu-id="ffb17-168">CancelLine</span><span class="sxs-lookup"><span data-stu-id="ffb17-168">CancelLine</span></span>

<span data-ttu-id="ffb17-169">Annule l’entrée actuelle, en laissant l’entrée à l’écran, mais retourne à l’hôte afin que l’invite soit de nouveau évaluée.</span><span class="sxs-lookup"><span data-stu-id="ffb17-169">Cancel the current input, leaving the input on the screen, but returns back to the host so the prompt is evaluated again.</span></span>

- <span data-ttu-id="ffb17-170">Mode d’insertion VI : `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-170">Vi insert mode: `<Ctrl+c>`</span></span>
- <span data-ttu-id="ffb17-171">Mode de commande VI : `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-171">Vi command mode: `<Ctrl+c>`</span></span>

### <a name="copy"></a><span data-ttu-id="ffb17-172">Copier</span><span class="sxs-lookup"><span data-stu-id="ffb17-172">Copy</span></span>

<span data-ttu-id="ffb17-173">Copier la région sélectionnée dans le presse-papiers du système.</span><span class="sxs-lookup"><span data-stu-id="ffb17-173">Copy selected region to the system clipboard.</span></span> <span data-ttu-id="ffb17-174">Si aucune région n’est sélectionnée, copiez la ligne entière.</span><span class="sxs-lookup"><span data-stu-id="ffb17-174">If no region is selected, copy the whole line.</span></span>

- <span data-ttu-id="ffb17-175">Cmd `<Ctrl+C>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-175">Cmd: `<Ctrl+C>`</span></span>

### <a name="copyorcancelline"></a><span data-ttu-id="ffb17-176">CopyOrCancelLine</span><span class="sxs-lookup"><span data-stu-id="ffb17-176">CopyOrCancelLine</span></span>

<span data-ttu-id="ffb17-177">Si le texte est sélectionné, copiez-le dans le presse-papiers, sinon, annulez la ligne.</span><span class="sxs-lookup"><span data-stu-id="ffb17-177">If text is selected, copy to the clipboard, otherwise cancel the line.</span></span>

- <span data-ttu-id="ffb17-178">Cmd `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-178">Cmd: `<Ctrl+c>`</span></span>
- <span data-ttu-id="ffb17-179">Emacs- `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-179">Emacs: `<Ctrl+c>`</span></span>

### <a name="cut"></a><span data-ttu-id="ffb17-180">Couper</span><span class="sxs-lookup"><span data-stu-id="ffb17-180">Cut</span></span>

<span data-ttu-id="ffb17-181">Supprimer la zone sélectionnée en plaçant le texte supprimé dans le presse-papiers du système.</span><span class="sxs-lookup"><span data-stu-id="ffb17-181">Delete selected region placing deleted text in the system clipboard.</span></span>

- <span data-ttu-id="ffb17-182">Cmd `<Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-182">Cmd: `<Ctrl+x>`</span></span>

### <a name="deletechar"></a><span data-ttu-id="ffb17-183">DeleteChar</span><span class="sxs-lookup"><span data-stu-id="ffb17-183">DeleteChar</span></span>

<span data-ttu-id="ffb17-184">Supprimez le caractère sous le curseur.</span><span class="sxs-lookup"><span data-stu-id="ffb17-184">Delete the character under the cursor.</span></span>

- <span data-ttu-id="ffb17-185">Cmd `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-185">Cmd: `<Delete>`</span></span>
- <span data-ttu-id="ffb17-186">Emacs- `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-186">Emacs: `<Delete>`</span></span>
- <span data-ttu-id="ffb17-187">Mode d’insertion VI : `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-187">Vi insert mode: `<Delete>`</span></span>
- <span data-ttu-id="ffb17-188">Mode de commande VI : `<Delete>` , `<x>` , `<d,l>` , `<d,Space>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-188">Vi command mode: `<Delete>`, `<x>`, `<d,l>`, `<d,Space>`</span></span>

### <a name="deletecharorexit"></a><span data-ttu-id="ffb17-189">DeleteCharOrExit</span><span class="sxs-lookup"><span data-stu-id="ffb17-189">DeleteCharOrExit</span></span>

<span data-ttu-id="ffb17-190">Supprimez le caractère sous le curseur, ou si la ligne est vide, quittez le processus.</span><span class="sxs-lookup"><span data-stu-id="ffb17-190">Delete the character under the cursor, or if the line is empty, exit the process.</span></span>

- <span data-ttu-id="ffb17-191">Emacs- `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-191">Emacs: `<Ctrl+d>`</span></span>

### <a name="deleteendofword"></a><span data-ttu-id="ffb17-192">DeleteEndOfWord</span><span class="sxs-lookup"><span data-stu-id="ffb17-192">DeleteEndOfWord</span></span>

<span data-ttu-id="ffb17-193">Supprimer à la fin du mot.</span><span class="sxs-lookup"><span data-stu-id="ffb17-193">Delete to the end of the word.</span></span>

- <span data-ttu-id="ffb17-194">Mode de commande VI : `<d,e>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-194">Vi command mode: `<d,e>`</span></span>

### <a name="deleteline"></a><span data-ttu-id="ffb17-195">DeleteLine</span><span class="sxs-lookup"><span data-stu-id="ffb17-195">DeleteLine</span></span>

<span data-ttu-id="ffb17-196">Supprime la ligne active, en activant l’annulation.</span><span class="sxs-lookup"><span data-stu-id="ffb17-196">Deletes the current line, enabling undo.</span></span>

- <span data-ttu-id="ffb17-197">Mode de commande VI : `<d,d>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-197">Vi command mode: `<d,d>`</span></span>

### <a name="deletelinetofirstchar"></a><span data-ttu-id="ffb17-198">DeleteLineToFirstChar</span><span class="sxs-lookup"><span data-stu-id="ffb17-198">DeleteLineToFirstChar</span></span>

<span data-ttu-id="ffb17-199">Supprime le texte du curseur jusqu’au premier caractère non vide de la ligne.</span><span class="sxs-lookup"><span data-stu-id="ffb17-199">Deletes text from the cursor to the first non-blank character of the line.</span></span>

- <span data-ttu-id="ffb17-200">Mode de commande VI : `<d,^>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-200">Vi command mode: `<d,^>`</span></span>

### <a name="deletetoend"></a><span data-ttu-id="ffb17-201">DeleteToEnd</span><span class="sxs-lookup"><span data-stu-id="ffb17-201">DeleteToEnd</span></span>

<span data-ttu-id="ffb17-202">Supprimer à la fin de la ligne.</span><span class="sxs-lookup"><span data-stu-id="ffb17-202">Delete to the end of the line.</span></span>

- <span data-ttu-id="ffb17-203">Mode de commande VI : `<D>` , `<d,$>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-203">Vi command mode: `<D>`, `<d,$>`</span></span>

### <a name="deleteword"></a><span data-ttu-id="ffb17-204">DeleteWord</span><span class="sxs-lookup"><span data-stu-id="ffb17-204">DeleteWord</span></span>

<span data-ttu-id="ffb17-205">Supprimer le mot suivant.</span><span class="sxs-lookup"><span data-stu-id="ffb17-205">Delete the next word.</span></span>

- <span data-ttu-id="ffb17-206">Mode de commande VI : `<d,w>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-206">Vi command mode: `<d,w>`</span></span>

### <a name="forwarddeleteline"></a><span data-ttu-id="ffb17-207">ForwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="ffb17-207">ForwardDeleteLine</span></span>

<span data-ttu-id="ffb17-208">Comme ForwardKillLine-supprime le texte du point jusqu’à la fin de la ligne, mais ne place pas le texte supprimé dans l’anneau Kill.</span><span class="sxs-lookup"><span data-stu-id="ffb17-208">Like ForwardKillLine - deletes text from the point to the end of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="ffb17-209">Cmd `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-209">Cmd: `<Ctrl+End>`</span></span>
- <span data-ttu-id="ffb17-210">Mode d’insertion VI : `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-210">Vi insert mode: `<Ctrl+End>`</span></span>
- <span data-ttu-id="ffb17-211">Mode de commande VI : `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-211">Vi command mode: `<Ctrl+End>`</span></span>

### <a name="insertlineabove"></a><span data-ttu-id="ffb17-212">InsertLineAbove</span><span class="sxs-lookup"><span data-stu-id="ffb17-212">InsertLineAbove</span></span>

<span data-ttu-id="ffb17-213">Une nouvelle ligne vide est créée au-dessus de la ligne active, quel que soit l’endroit où se trouve le curseur sur la ligne active.</span><span class="sxs-lookup"><span data-stu-id="ffb17-213">A new empty line is created above the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="ffb17-214">Le curseur se déplace au début de la nouvelle ligne.</span><span class="sxs-lookup"><span data-stu-id="ffb17-214">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="ffb17-215">Cmd `<Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-215">Cmd: `<Ctrl+Enter>`</span></span>

### <a name="insertlinebelow"></a><span data-ttu-id="ffb17-216">InsertLineBelow</span><span class="sxs-lookup"><span data-stu-id="ffb17-216">InsertLineBelow</span></span>

<span data-ttu-id="ffb17-217">Une nouvelle ligne vide est créée sous la ligne active, quel que soit l’endroit où se trouve le curseur sur la ligne active.</span><span class="sxs-lookup"><span data-stu-id="ffb17-217">A new empty line is created below the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="ffb17-218">Le curseur se déplace au début de la nouvelle ligne.</span><span class="sxs-lookup"><span data-stu-id="ffb17-218">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="ffb17-219">Cmd `<Shift+Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-219">Cmd: `<Shift+Ctrl+Enter>`</span></span>

### <a name="invertcase"></a><span data-ttu-id="ffb17-220">InvertCase</span><span class="sxs-lookup"><span data-stu-id="ffb17-220">InvertCase</span></span>

<span data-ttu-id="ffb17-221">Inverser la casse du caractère actuel et passer au suivant.</span><span class="sxs-lookup"><span data-stu-id="ffb17-221">Invert the case of the current character and move to the next one.</span></span>

- <span data-ttu-id="ffb17-222">Mode de commande VI : `<~>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-222">Vi command mode: `<~>`</span></span>

### <a name="killline"></a><span data-ttu-id="ffb17-223">KillLine</span><span class="sxs-lookup"><span data-stu-id="ffb17-223">KillLine</span></span>

<span data-ttu-id="ffb17-224">Effacez l’entrée du curseur jusqu’à la fin de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="ffb17-224">Clear the input from the cursor to the end of the input.</span></span> <span data-ttu-id="ffb17-225">Le texte effacé est placé dans le Kill-Ring.</span><span class="sxs-lookup"><span data-stu-id="ffb17-225">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="ffb17-226">Emacs- `<Ctrl+k>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-226">Emacs: `<Ctrl+k>`</span></span>

### <a name="killregion"></a><span data-ttu-id="ffb17-227">KillRegion</span><span class="sxs-lookup"><span data-stu-id="ffb17-227">KillRegion</span></span>

<span data-ttu-id="ffb17-228">Supprimer le texte situé entre le curseur et la marque.</span><span class="sxs-lookup"><span data-stu-id="ffb17-228">Kill the text between the cursor and the mark.</span></span>

- <span data-ttu-id="ffb17-229">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="ffb17-229">Function is unbound.</span></span>

### <a name="killword"></a><span data-ttu-id="ffb17-230">KillWord</span><span class="sxs-lookup"><span data-stu-id="ffb17-230">KillWord</span></span>

<span data-ttu-id="ffb17-231">Efface l’entrée du curseur jusqu’à la fin du mot actuel.</span><span class="sxs-lookup"><span data-stu-id="ffb17-231">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="ffb17-232">Si le curseur se trouve entre des mots, l’entrée est effacée du curseur jusqu’à la fin du mot suivant.</span><span class="sxs-lookup"><span data-stu-id="ffb17-232">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="ffb17-233">Le texte effacé est placé dans le Kill-Ring.</span><span class="sxs-lookup"><span data-stu-id="ffb17-233">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="ffb17-234">Cmd `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-234">Cmd: `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="ffb17-235">Emacs- `<Alt+d>` , `<Escape,d>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-235">Emacs: `<Alt+d>`, `<Escape,d>`</span></span>
- <span data-ttu-id="ffb17-236">Mode d’insertion VI : `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-236">Vi insert mode: `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="ffb17-237">Mode de commande VI : `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-237">Vi command mode: `<Ctrl+Delete>`</span></span>

### <a name="paste"></a><span data-ttu-id="ffb17-238">Coller</span><span class="sxs-lookup"><span data-stu-id="ffb17-238">Paste</span></span>

<span data-ttu-id="ffb17-239">Collez le texte à partir du presse-papiers du système.</span><span class="sxs-lookup"><span data-stu-id="ffb17-239">Paste text from the system clipboard.</span></span>

- <span data-ttu-id="ffb17-240">Cmd : `<Ctrl+v>` , `<Shift+Insert>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-240">Cmd: `<Ctrl+v>`, `<Shift+Insert>`</span></span>
- <span data-ttu-id="ffb17-241">Mode d’insertion VI : `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-241">Vi insert mode: `<Ctrl+v>`</span></span>
- <span data-ttu-id="ffb17-242">Mode de commande VI : `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-242">Vi command mode: `<Ctrl+v>`</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ffb17-243">Lors de l’utilisation de la fonction **Paste** , le contenu entier de la mémoire tampon du presse-papiers est collé dans la mémoire tampon d’entrée de PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="ffb17-243">When using the **Paste** function, the entire contents of the clipboard buffer is pasted into the input buffer of PSReadLine.</span></span> <span data-ttu-id="ffb17-244">La mémoire tampon d’entrée est ensuite transmise à l’analyseur PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ffb17-244">The input buffer is then passed to the PowerShell parser.</span></span> <span data-ttu-id="ffb17-245">L’entrée collée à l’aide de la méthode de collage **avec le bouton droit** de la console de l’application de console est copiée dans la mémoire tampon d’entrée un caractère à la fois.</span><span class="sxs-lookup"><span data-stu-id="ffb17-245">Input pasted using the console application's **right-click** paste method is copied to the input buffer one character at a time.</span></span> <span data-ttu-id="ffb17-246">La mémoire tampon d’entrée est transmise à l’analyseur lorsqu’un caractère de saut de ligne est copié.</span><span class="sxs-lookup"><span data-stu-id="ffb17-246">The input buffer is passed to the parser when a newline character is copied.</span></span> <span data-ttu-id="ffb17-247">Par conséquent, l’entrée est analysée une ligne à la fois.</span><span class="sxs-lookup"><span data-stu-id="ffb17-247">Therefore, the input is parsed one line at a time.</span></span> <span data-ttu-id="ffb17-248">La différence entre les méthodes de collage entraîne un comportement d’exécution différent.</span><span class="sxs-lookup"><span data-stu-id="ffb17-248">The difference between paste methods results in different execution behavior.</span></span>

### <a name="pasteafter"></a><span data-ttu-id="ffb17-249">PasteAfter</span><span class="sxs-lookup"><span data-stu-id="ffb17-249">PasteAfter</span></span>

<span data-ttu-id="ffb17-250">Collez le presse-papiers après le curseur, en déplaçant le curseur à la fin du texte collé.</span><span class="sxs-lookup"><span data-stu-id="ffb17-250">Paste the clipboard after the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="ffb17-251">Mode de commande VI : `<p>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-251">Vi command mode: `<p>`</span></span>

### <a name="pastebefore"></a><span data-ttu-id="ffb17-252">PasteBefore</span><span class="sxs-lookup"><span data-stu-id="ffb17-252">PasteBefore</span></span>

<span data-ttu-id="ffb17-253">Collez le presse-papiers avant le curseur, en déplaçant le curseur à la fin du texte collé.</span><span class="sxs-lookup"><span data-stu-id="ffb17-253">Paste the clipboard before the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="ffb17-254">Mode de commande VI : `<P>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-254">Vi command mode: `<P>`</span></span>

### <a name="prependandaccept"></a><span data-ttu-id="ffb17-255">PrependAndAccept</span><span class="sxs-lookup"><span data-stu-id="ffb17-255">PrependAndAccept</span></span>

<span data-ttu-id="ffb17-256">Faites précéder un' # 'et acceptez la ligne.</span><span class="sxs-lookup"><span data-stu-id="ffb17-256">Prepend a '#' and accept the line.</span></span>

- <span data-ttu-id="ffb17-257">Mode de commande VI : `<#>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-257">Vi command mode: `<#>`</span></span>

### <a name="redo"></a><span data-ttu-id="ffb17-258">Rétablir</span><span class="sxs-lookup"><span data-stu-id="ffb17-258">Redo</span></span>

<span data-ttu-id="ffb17-259">Annule une annulation.</span><span class="sxs-lookup"><span data-stu-id="ffb17-259">Undo an undo.</span></span>

- <span data-ttu-id="ffb17-260">Cmd `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-260">Cmd: `<Ctrl+y>`</span></span>
- <span data-ttu-id="ffb17-261">Mode d’insertion VI : `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-261">Vi insert mode: `<Ctrl+y>`</span></span>
- <span data-ttu-id="ffb17-262">Mode de commande VI : `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-262">Vi command mode: `<Ctrl+y>`</span></span>

### <a name="repeatlastcommand"></a><span data-ttu-id="ffb17-263">RepeatLastCommand</span><span class="sxs-lookup"><span data-stu-id="ffb17-263">RepeatLastCommand</span></span>

<span data-ttu-id="ffb17-264">Répète la dernière modification de texte.</span><span class="sxs-lookup"><span data-stu-id="ffb17-264">Repeat the last text modification.</span></span>

- <span data-ttu-id="ffb17-265">Mode de commande VI : `<.>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-265">Vi command mode: `<.>`</span></span>

### <a name="revertline"></a><span data-ttu-id="ffb17-266">RevertLine</span><span class="sxs-lookup"><span data-stu-id="ffb17-266">RevertLine</span></span>

<span data-ttu-id="ffb17-267">Rétablit toutes les entrées de l’entrée actuelle.</span><span class="sxs-lookup"><span data-stu-id="ffb17-267">Reverts all of the input to the current input.</span></span>

- <span data-ttu-id="ffb17-268">Cmd `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-268">Cmd: `<Escape>`</span></span>
- <span data-ttu-id="ffb17-269">Emacs- `<Alt+r>` , `<Escape,r>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-269">Emacs: `<Alt+r>`, `<Escape,r>`</span></span>

### <a name="shellbackwardkillword"></a><span data-ttu-id="ffb17-270">ShellBackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="ffb17-270">ShellBackwardKillWord</span></span>

<span data-ttu-id="ffb17-271">Efface l’entrée du début du mot actuel jusqu’au curseur.</span><span class="sxs-lookup"><span data-stu-id="ffb17-271">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="ffb17-272">Si le curseur se trouve entre des mots, l’entrée est effacée du début du mot précédent au curseur.</span><span class="sxs-lookup"><span data-stu-id="ffb17-272">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="ffb17-273">Le texte effacé est placé dans le Kill-Ring.</span><span class="sxs-lookup"><span data-stu-id="ffb17-273">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="ffb17-274">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="ffb17-274">Function is unbound.</span></span>

### <a name="shellkillword"></a><span data-ttu-id="ffb17-275">ShellKillWord</span><span class="sxs-lookup"><span data-stu-id="ffb17-275">ShellKillWord</span></span>

<span data-ttu-id="ffb17-276">Efface l’entrée du curseur jusqu’à la fin du mot actuel.</span><span class="sxs-lookup"><span data-stu-id="ffb17-276">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="ffb17-277">Si le curseur se trouve entre des mots, l’entrée est effacée du curseur jusqu’à la fin du mot suivant.</span><span class="sxs-lookup"><span data-stu-id="ffb17-277">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="ffb17-278">Le texte effacé est placé dans le Kill-Ring.</span><span class="sxs-lookup"><span data-stu-id="ffb17-278">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="ffb17-279">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="ffb17-279">Function is unbound.</span></span>

### <a name="swapcharacters"></a><span data-ttu-id="ffb17-280">SwapCharacters</span><span class="sxs-lookup"><span data-stu-id="ffb17-280">SwapCharacters</span></span>

<span data-ttu-id="ffb17-281">Permuter le caractère actuel et celui qui le précèdent.</span><span class="sxs-lookup"><span data-stu-id="ffb17-281">Swap the current character and the one before it.</span></span>

- <span data-ttu-id="ffb17-282">Emacs- `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-282">Emacs: `<Ctrl+t>`</span></span>
- <span data-ttu-id="ffb17-283">Mode d’insertion VI : `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-283">Vi insert mode: `<Ctrl+t>`</span></span>
- <span data-ttu-id="ffb17-284">Mode de commande VI : `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-284">Vi command mode: `<Ctrl+t>`</span></span>

### <a name="undo"></a><span data-ttu-id="ffb17-285">Annuler</span><span class="sxs-lookup"><span data-stu-id="ffb17-285">Undo</span></span>

<span data-ttu-id="ffb17-286">Annuler une modification précédente.</span><span class="sxs-lookup"><span data-stu-id="ffb17-286">Undo a previous edit.</span></span>

- <span data-ttu-id="ffb17-287">Cmd `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-287">Cmd: `<Ctrl+z>`</span></span>
- <span data-ttu-id="ffb17-288">Emacs- `<Ctrl+_>` , `<Ctrl+x,Ctrl+u>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-288">Emacs: `<Ctrl+_>`, `<Ctrl+x,Ctrl+u>`</span></span>
- <span data-ttu-id="ffb17-289">Mode d’insertion VI : `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-289">Vi insert mode: `<Ctrl+z>`</span></span>
- <span data-ttu-id="ffb17-290">Mode de commande VI : `<Ctrl+z>` , `<u>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-290">Vi command mode: `<Ctrl+z>`, `<u>`</span></span>

### <a name="undoall"></a><span data-ttu-id="ffb17-291">UndoAll</span><span class="sxs-lookup"><span data-stu-id="ffb17-291">UndoAll</span></span>

<span data-ttu-id="ffb17-292">Annule toutes les modifications précédentes pour la ligne.</span><span class="sxs-lookup"><span data-stu-id="ffb17-292">Undo all previous edits for line.</span></span>

- <span data-ttu-id="ffb17-293">Mode de commande VI : `<U>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-293">Vi command mode: `<U>`</span></span>

### <a name="unixwordrubout"></a><span data-ttu-id="ffb17-294">UnixWordRubout</span><span class="sxs-lookup"><span data-stu-id="ffb17-294">UnixWordRubout</span></span>

<span data-ttu-id="ffb17-295">Efface l’entrée du début du mot actuel jusqu’au curseur.</span><span class="sxs-lookup"><span data-stu-id="ffb17-295">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="ffb17-296">Si le curseur se trouve entre des mots, l’entrée est effacée du début du mot précédent au curseur.</span><span class="sxs-lookup"><span data-stu-id="ffb17-296">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="ffb17-297">Le texte effacé est placé dans le Kill-Ring.</span><span class="sxs-lookup"><span data-stu-id="ffb17-297">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="ffb17-298">Emacs- `<Ctrl+w>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-298">Emacs: `<Ctrl+w>`</span></span>

### <a name="validateandacceptline"></a><span data-ttu-id="ffb17-299">ValidateAndAcceptLine</span><span class="sxs-lookup"><span data-stu-id="ffb17-299">ValidateAndAcceptLine</span></span>

<span data-ttu-id="ffb17-300">Tentative d’exécution de l’entrée en cours.</span><span class="sxs-lookup"><span data-stu-id="ffb17-300">Attempt to execute the current input.</span></span> <span data-ttu-id="ffb17-301">Si l’entrée actuelle est incomplète (par exemple, il manque une parenthèse fermante, un crochet ou un guillemet, l’invite de continuation est affichée sur la ligne suivante et PSReadLine attend que les clés modifient l’entrée actuelle.</span><span class="sxs-lookup"><span data-stu-id="ffb17-301">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="ffb17-302">Emacs- `<Ctrl+m>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-302">Emacs: `<Ctrl+m>`</span></span>

### <a name="viacceptline"></a><span data-ttu-id="ffb17-303">ViAcceptLine</span><span class="sxs-lookup"><span data-stu-id="ffb17-303">ViAcceptLine</span></span>

<span data-ttu-id="ffb17-304">Acceptez la ligne et passez en mode insertion.</span><span class="sxs-lookup"><span data-stu-id="ffb17-304">Accept the line and switch to Insert mode.</span></span>

- <span data-ttu-id="ffb17-305">Mode de commande VI : `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-305">Vi command mode: `<Enter>`</span></span>

### <a name="viacceptlineorexit"></a><span data-ttu-id="ffb17-306">ViAcceptLineOrExit</span><span class="sxs-lookup"><span data-stu-id="ffb17-306">ViAcceptLineOrExit</span></span>

<span data-ttu-id="ffb17-307">Comme DeleteCharOrExit en mode emacs, mais accepte la ligne au lieu de supprimer un caractère.</span><span class="sxs-lookup"><span data-stu-id="ffb17-307">Like DeleteCharOrExit in Emacs mode, but accepts the line instead of deleting a character.</span></span>

- <span data-ttu-id="ffb17-308">Mode d’insertion VI : `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-308">Vi insert mode: `<Ctrl+d>`</span></span>
- <span data-ttu-id="ffb17-309">Mode de commande VI : `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-309">Vi command mode: `<Ctrl+d>`</span></span>

### <a name="viappendline"></a><span data-ttu-id="ffb17-310">ViAppendLine</span><span class="sxs-lookup"><span data-stu-id="ffb17-310">ViAppendLine</span></span>

<span data-ttu-id="ffb17-311">Une nouvelle ligne est insérée au-dessous de la ligne active.</span><span class="sxs-lookup"><span data-stu-id="ffb17-311">A new line is inserted below the current line.</span></span>

- <span data-ttu-id="ffb17-312">Mode de commande VI : `<o>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-312">Vi command mode: `<o>`</span></span>

### <a name="vibackwarddeleteglob"></a><span data-ttu-id="ffb17-313">ViBackwardDeleteGlob</span><span class="sxs-lookup"><span data-stu-id="ffb17-313">ViBackwardDeleteGlob</span></span>

<span data-ttu-id="ffb17-314">Supprime le mot précédent, en utilisant uniquement un espace blanc comme délimiteur de mot.</span><span class="sxs-lookup"><span data-stu-id="ffb17-314">Deletes the previous word, using only white space as the word delimiter.</span></span>

- <span data-ttu-id="ffb17-315">Mode de commande VI : `<d,B>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-315">Vi command mode: `<d,B>`</span></span>

### <a name="vibackwardglob"></a><span data-ttu-id="ffb17-316">ViBackwardGlob</span><span class="sxs-lookup"><span data-stu-id="ffb17-316">ViBackwardGlob</span></span>

<span data-ttu-id="ffb17-317">Déplace le curseur au début du mot précédent, en utilisant uniquement des espaces blancs comme délimiteurs.</span><span class="sxs-lookup"><span data-stu-id="ffb17-317">Moves the cursor back to the beginning of the previous word, using only white space as delimiters.</span></span>

- <span data-ttu-id="ffb17-318">Mode de commande VI : `<B>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-318">Vi command mode: `<B>`</span></span>

### <a name="videletebrace"></a><span data-ttu-id="ffb17-319">ViDeleteBrace</span><span class="sxs-lookup"><span data-stu-id="ffb17-319">ViDeleteBrace</span></span>

<span data-ttu-id="ffb17-320">Recherchez l’accolade correspondante, la parenthèse ou le crochet, et supprimez tout le contenu dans, y compris l’accolade.</span><span class="sxs-lookup"><span data-stu-id="ffb17-320">Find the matching brace, parenthesis, or square bracket and delete all contents within, including the brace.</span></span>

- <span data-ttu-id="ffb17-321">Mode de commande VI : `<d,%>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-321">Vi command mode: `<d,%>`</span></span>

### <a name="videleteendofglob"></a><span data-ttu-id="ffb17-322">ViDeleteEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="ffb17-322">ViDeleteEndOfGlob</span></span>

<span data-ttu-id="ffb17-323">Supprimer à la fin du mot.</span><span class="sxs-lookup"><span data-stu-id="ffb17-323">Delete to the end of the word.</span></span>

- <span data-ttu-id="ffb17-324">Mode de commande VI : `<d,E>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-324">Vi command mode: `<d,E>`</span></span>

### <a name="videleteglob"></a><span data-ttu-id="ffb17-325">ViDeleteGlob</span><span class="sxs-lookup"><span data-stu-id="ffb17-325">ViDeleteGlob</span></span>

<span data-ttu-id="ffb17-326">Supprime la glob suivante (mot blanc délimité par des espaces).</span><span class="sxs-lookup"><span data-stu-id="ffb17-326">Delete the next glob (white space delimited word).</span></span>

- <span data-ttu-id="ffb17-327">Mode de commande VI : `<d,W>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-327">Vi command mode: `<d,W>`</span></span>

### <a name="videletetobeforechar"></a><span data-ttu-id="ffb17-328">ViDeleteToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="ffb17-328">ViDeleteToBeforeChar</span></span>

<span data-ttu-id="ffb17-329">Supprime jusqu’au caractère donné.</span><span class="sxs-lookup"><span data-stu-id="ffb17-329">Deletes until given character.</span></span>

- <span data-ttu-id="ffb17-330">Mode de commande VI : `<d,t>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-330">Vi command mode: `<d,t>`</span></span>

### <a name="videletetobeforecharbackward"></a><span data-ttu-id="ffb17-331">ViDeleteToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="ffb17-331">ViDeleteToBeforeCharBackward</span></span>

<span data-ttu-id="ffb17-332">Supprime jusqu’au caractère donné.</span><span class="sxs-lookup"><span data-stu-id="ffb17-332">Deletes until given character.</span></span>

- <span data-ttu-id="ffb17-333">Mode de commande VI : `<d,T>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-333">Vi command mode: `<d,T>`</span></span>

### <a name="videletetochar"></a><span data-ttu-id="ffb17-334">ViDeleteToChar</span><span class="sxs-lookup"><span data-stu-id="ffb17-334">ViDeleteToChar</span></span>

<span data-ttu-id="ffb17-335">Supprime jusqu’au caractère donné.</span><span class="sxs-lookup"><span data-stu-id="ffb17-335">Deletes until given character.</span></span>

- <span data-ttu-id="ffb17-336">Mode de commande VI : `<d,f>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-336">Vi command mode: `<d,f>`</span></span>

### <a name="videletetocharbackward"></a><span data-ttu-id="ffb17-337">ViDeleteToCharBackward</span><span class="sxs-lookup"><span data-stu-id="ffb17-337">ViDeleteToCharBackward</span></span>

<span data-ttu-id="ffb17-338">Supprime vers l’arrière jusqu’au caractère donné.</span><span class="sxs-lookup"><span data-stu-id="ffb17-338">Deletes backwards until given character.</span></span>

- <span data-ttu-id="ffb17-339">Mode de commande VI : `<d,F>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-339">Vi command mode: `<d,F>`</span></span>

### <a name="viinsertatbegining"></a><span data-ttu-id="ffb17-340">ViInsertAtBegining</span><span class="sxs-lookup"><span data-stu-id="ffb17-340">ViInsertAtBegining</span></span>

<span data-ttu-id="ffb17-341">Basculez en mode insertion et positionnez le curseur au début de la ligne.</span><span class="sxs-lookup"><span data-stu-id="ffb17-341">Switch to Insert mode and position the cursor at the beginning of the line.</span></span>

- <span data-ttu-id="ffb17-342">Mode de commande VI : `<I>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-342">Vi command mode: `<I>`</span></span>

### <a name="viinsertatend"></a><span data-ttu-id="ffb17-343">ViInsertAtEnd</span><span class="sxs-lookup"><span data-stu-id="ffb17-343">ViInsertAtEnd</span></span>

<span data-ttu-id="ffb17-344">Basculez en mode insertion et positionnez le curseur à la fin de la ligne.</span><span class="sxs-lookup"><span data-stu-id="ffb17-344">Switch to Insert mode and position the cursor at the end of the line.</span></span>

- <span data-ttu-id="ffb17-345">Mode de commande VI : `<A>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-345">Vi command mode: `<A>`</span></span>

### <a name="viinsertline"></a><span data-ttu-id="ffb17-346">ViInsertLine</span><span class="sxs-lookup"><span data-stu-id="ffb17-346">ViInsertLine</span></span>

<span data-ttu-id="ffb17-347">Une nouvelle ligne est insérée au-dessus de la ligne active.</span><span class="sxs-lookup"><span data-stu-id="ffb17-347">A new line is inserted above the current line.</span></span>

- <span data-ttu-id="ffb17-348">Mode de commande VI : `<O>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-348">Vi command mode: `<O>`</span></span>

### <a name="viinsertwithappend"></a><span data-ttu-id="ffb17-349">ViInsertWithAppend</span><span class="sxs-lookup"><span data-stu-id="ffb17-349">ViInsertWithAppend</span></span>

<span data-ttu-id="ffb17-350">Ajouter à partir de la position de la ligne active.</span><span class="sxs-lookup"><span data-stu-id="ffb17-350">Append from the current line position.</span></span>

- <span data-ttu-id="ffb17-351">Mode de commande VI : `<a>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-351">Vi command mode: `<a>`</span></span>

### <a name="viinsertwithdelete"></a><span data-ttu-id="ffb17-352">ViInsertWithDelete</span><span class="sxs-lookup"><span data-stu-id="ffb17-352">ViInsertWithDelete</span></span>

<span data-ttu-id="ffb17-353">Supprimez le caractère actuel et basculez en mode insertion.</span><span class="sxs-lookup"><span data-stu-id="ffb17-353">Delete the current character and switch to Insert mode.</span></span>

- <span data-ttu-id="ffb17-354">Mode de commande VI : `<s>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-354">Vi command mode: `<s>`</span></span>

### <a name="vijoinlines"></a><span data-ttu-id="ffb17-355">ViJoinLines</span><span class="sxs-lookup"><span data-stu-id="ffb17-355">ViJoinLines</span></span>

<span data-ttu-id="ffb17-356">Joint la ligne active et la ligne suivante.</span><span class="sxs-lookup"><span data-stu-id="ffb17-356">Joins the current line and the next line.</span></span>

- <span data-ttu-id="ffb17-357">Mode de commande VI : `<J>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-357">Vi command mode: `<J>`</span></span>

### <a name="vireplaceline"></a><span data-ttu-id="ffb17-358">ViReplaceLine</span><span class="sxs-lookup"><span data-stu-id="ffb17-358">ViReplaceLine</span></span>

<span data-ttu-id="ffb17-359">Effacez l’intégralité de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="ffb17-359">Erase the entire command line.</span></span>

- <span data-ttu-id="ffb17-360">Mode de commande VI : `<S>` , `<c,c>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-360">Vi command mode: `<S>`, `<c,c>`</span></span>

### <a name="vireplacetobeforechar"></a><span data-ttu-id="ffb17-361">ViReplaceToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="ffb17-361">ViReplaceToBeforeChar</span></span>

<span data-ttu-id="ffb17-362">Remplace jusqu’au caractère donné.</span><span class="sxs-lookup"><span data-stu-id="ffb17-362">Replaces until given character.</span></span>

- <span data-ttu-id="ffb17-363">Mode de commande VI : `<c,t>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-363">Vi command mode: `<c,t>`</span></span>

### <a name="vireplacetobeforecharbackward"></a><span data-ttu-id="ffb17-364">ViReplaceToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="ffb17-364">ViReplaceToBeforeCharBackward</span></span>

<span data-ttu-id="ffb17-365">Remplace jusqu’au caractère donné.</span><span class="sxs-lookup"><span data-stu-id="ffb17-365">Replaces until given character.</span></span>

- <span data-ttu-id="ffb17-366">Mode de commande VI : `<c,T>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-366">Vi command mode: `<c,T>`</span></span>

### <a name="vireplacetochar"></a><span data-ttu-id="ffb17-367">ViReplaceToChar</span><span class="sxs-lookup"><span data-stu-id="ffb17-367">ViReplaceToChar</span></span>

<span data-ttu-id="ffb17-368">Supprime jusqu’au caractère donné.</span><span class="sxs-lookup"><span data-stu-id="ffb17-368">Deletes until given character.</span></span>

- <span data-ttu-id="ffb17-369">Mode de commande VI : `<c,f>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-369">Vi command mode: `<c,f>`</span></span>

### <a name="vireplacetocharbackward"></a><span data-ttu-id="ffb17-370">ViReplaceToCharBackward</span><span class="sxs-lookup"><span data-stu-id="ffb17-370">ViReplaceToCharBackward</span></span>

<span data-ttu-id="ffb17-371">Remplace jusqu’au caractère donné.</span><span class="sxs-lookup"><span data-stu-id="ffb17-371">Replaces until given character.</span></span>

- <span data-ttu-id="ffb17-372">Mode de commande VI : `<c,F>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-372">Vi command mode: `<c,F>`</span></span>

### <a name="viyankbeginningofline"></a><span data-ttu-id="ffb17-373">ViYankBeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="ffb17-373">ViYankBeginningOfLine</span></span>

<span data-ttu-id="ffb17-374">Yank entre le début de la mémoire tampon et le curseur.</span><span class="sxs-lookup"><span data-stu-id="ffb17-374">Yank from the beginning of the buffer to the cursor.</span></span>

- <span data-ttu-id="ffb17-375">Mode de commande VI : `<y,0>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-375">Vi command mode: `<y,0>`</span></span>

### <a name="viyankendofglob"></a><span data-ttu-id="ffb17-376">ViYankEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="ffb17-376">ViYankEndOfGlob</span></span>

<span data-ttu-id="ffb17-377">Yank du curseur jusqu’à la fin du ou des mots.</span><span class="sxs-lookup"><span data-stu-id="ffb17-377">Yank from the cursor to the end of the WORD(s).</span></span>

- <span data-ttu-id="ffb17-378">Mode de commande VI : `<y,E>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-378">Vi command mode: `<y,E>`</span></span>

### <a name="viyankendofword"></a><span data-ttu-id="ffb17-379">ViYankEndOfWord</span><span class="sxs-lookup"><span data-stu-id="ffb17-379">ViYankEndOfWord</span></span>

<span data-ttu-id="ffb17-380">Yank du curseur jusqu’à la fin du ou des mots.</span><span class="sxs-lookup"><span data-stu-id="ffb17-380">Yank from the cursor to the end of the word(s).</span></span>

- <span data-ttu-id="ffb17-381">Mode de commande VI : `<y,e>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-381">Vi command mode: `<y,e>`</span></span>

### <a name="viyankleft"></a><span data-ttu-id="ffb17-382">ViYankLeft</span><span class="sxs-lookup"><span data-stu-id="ffb17-382">ViYankLeft</span></span>

<span data-ttu-id="ffb17-383">Yank caractère (s) à gauche du curseur.</span><span class="sxs-lookup"><span data-stu-id="ffb17-383">Yank character(s) to the left of the cursor.</span></span>

- <span data-ttu-id="ffb17-384">Mode de commande VI : `<y,h>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-384">Vi command mode: `<y,h>`</span></span>

### <a name="viyankline"></a><span data-ttu-id="ffb17-385">ViYankLine</span><span class="sxs-lookup"><span data-stu-id="ffb17-385">ViYankLine</span></span>

<span data-ttu-id="ffb17-386">Yank la mémoire tampon entière.</span><span class="sxs-lookup"><span data-stu-id="ffb17-386">Yank the entire buffer.</span></span>

- <span data-ttu-id="ffb17-387">Mode de commande VI : `<y,y>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-387">Vi command mode: `<y,y>`</span></span>

### <a name="viyanknextglob"></a><span data-ttu-id="ffb17-388">ViYankNextGlob</span><span class="sxs-lookup"><span data-stu-id="ffb17-388">ViYankNextGlob</span></span>

<span data-ttu-id="ffb17-389">Yank à partir d’un curseur jusqu’au début du ou des mots suivants.</span><span class="sxs-lookup"><span data-stu-id="ffb17-389">Yank from cursor to the start of the next WORD(s).</span></span>

- <span data-ttu-id="ffb17-390">Mode de commande VI : `<y,W>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-390">Vi command mode: `<y,W>`</span></span>

### <a name="viyanknextword"></a><span data-ttu-id="ffb17-391">ViYankNextWord</span><span class="sxs-lookup"><span data-stu-id="ffb17-391">ViYankNextWord</span></span>

<span data-ttu-id="ffb17-392">Yank le ou les mots après le curseur.</span><span class="sxs-lookup"><span data-stu-id="ffb17-392">Yank the word(s) after the cursor.</span></span>

- <span data-ttu-id="ffb17-393">Mode de commande VI : `<y,w>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-393">Vi command mode: `<y,w>`</span></span>

### <a name="viyankpercent"></a><span data-ttu-id="ffb17-394">ViYankPercent</span><span class="sxs-lookup"><span data-stu-id="ffb17-394">ViYankPercent</span></span>

<span data-ttu-id="ffb17-395">Yank à/à partir de l’accolade correspondante.</span><span class="sxs-lookup"><span data-stu-id="ffb17-395">Yank to/from matching brace.</span></span>

- <span data-ttu-id="ffb17-396">Mode de commande VI : `<y,%>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-396">Vi command mode: `<y,%>`</span></span>

### <a name="viyankpreviousglob"></a><span data-ttu-id="ffb17-397">ViYankPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="ffb17-397">ViYankPreviousGlob</span></span>

<span data-ttu-id="ffb17-398">Yank entre le début du ou des mots et le curseur.</span><span class="sxs-lookup"><span data-stu-id="ffb17-398">Yank from beginning of the WORD(s) to cursor.</span></span>

- <span data-ttu-id="ffb17-399">Mode de commande VI : `<y,B>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-399">Vi command mode: `<y,B>`</span></span>

### <a name="viyankpreviousword"></a><span data-ttu-id="ffb17-400">ViYankPreviousWord</span><span class="sxs-lookup"><span data-stu-id="ffb17-400">ViYankPreviousWord</span></span>

<span data-ttu-id="ffb17-401">Yank le ou les mots avant le curseur.</span><span class="sxs-lookup"><span data-stu-id="ffb17-401">Yank the word(s) before the cursor.</span></span>

- <span data-ttu-id="ffb17-402">Mode de commande VI : `<y,b>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-402">Vi command mode: `<y,b>`</span></span>

### <a name="viyankright"></a><span data-ttu-id="ffb17-403">ViYankRight</span><span class="sxs-lookup"><span data-stu-id="ffb17-403">ViYankRight</span></span>

<span data-ttu-id="ffb17-404">Yank caractère (s) situé sous et à droite du curseur.</span><span class="sxs-lookup"><span data-stu-id="ffb17-404">Yank character(s) under and to the right of the cursor.</span></span>

- <span data-ttu-id="ffb17-405">Mode de commande VI : `<y,l>` , `<y,Space>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-405">Vi command mode: `<y,l>`, `<y,Space>`</span></span>

### <a name="viyanktoendofline"></a><span data-ttu-id="ffb17-406">ViYankToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="ffb17-406">ViYankToEndOfLine</span></span>

<span data-ttu-id="ffb17-407">Yank du curseur jusqu’à la fin de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="ffb17-407">Yank from the cursor to the end of the buffer.</span></span>

- <span data-ttu-id="ffb17-408">Mode de commande VI : `<y,$>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-408">Vi command mode: `<y,$>`</span></span>

### <a name="viyanktofirstchar"></a><span data-ttu-id="ffb17-409">ViYankToFirstChar</span><span class="sxs-lookup"><span data-stu-id="ffb17-409">ViYankToFirstChar</span></span>

<span data-ttu-id="ffb17-410">Yank du premier caractère autre qu’un espace blanc au curseur.</span><span class="sxs-lookup"><span data-stu-id="ffb17-410">Yank from the first non-whitespace character to the cursor.</span></span>

- <span data-ttu-id="ffb17-411">Mode de commande VI : `<y,^>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-411">Vi command mode: `<y,^>`</span></span>

### <a name="yank"></a><span data-ttu-id="ffb17-412">Yank</span><span class="sxs-lookup"><span data-stu-id="ffb17-412">Yank</span></span>

<span data-ttu-id="ffb17-413">Ajoutez le texte le plus récemment supprimé à l’entrée.</span><span class="sxs-lookup"><span data-stu-id="ffb17-413">Add the most recently killed text to the input.</span></span>

- <span data-ttu-id="ffb17-414">Emacs- `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-414">Emacs: `<Ctrl+y>`</span></span>

### <a name="yanklastarg"></a><span data-ttu-id="ffb17-415">YankLastArg</span><span class="sxs-lookup"><span data-stu-id="ffb17-415">YankLastArg</span></span>

<span data-ttu-id="ffb17-416">Yank le dernier argument de la ligne d’historique précédente.</span><span class="sxs-lookup"><span data-stu-id="ffb17-416">Yank the last argument from the previous history line.</span></span> <span data-ttu-id="ffb17-417">Avec un argument, la première fois qu’il est appelé, se comporte comme YankNthArg.</span><span class="sxs-lookup"><span data-stu-id="ffb17-417">With an argument, the first time it is invoked, behaves just like YankNthArg.</span></span> <span data-ttu-id="ffb17-418">Si elle est appelée plusieurs fois, elle itère au sein de l’historique et ARG définit la direction (négatif inverse la direction).</span><span class="sxs-lookup"><span data-stu-id="ffb17-418">If invoked multiple times, instead it iterates through history and arg sets the direction (negative reverses the direction.)</span></span>

- <span data-ttu-id="ffb17-419">Cmd `<Alt+.>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-419">Cmd: `<Alt+.>`</span></span>
- <span data-ttu-id="ffb17-420">Emacs : `<Alt+.>` , `<Alt+_>` , `<Escape,.>` , `<Escape,_>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-420">Emacs: `<Alt+.>`, `<Alt+_>`, `<Escape,.>`, `<Escape,_>`</span></span>

### <a name="yankntharg"></a><span data-ttu-id="ffb17-421">YankNthArg</span><span class="sxs-lookup"><span data-stu-id="ffb17-421">YankNthArg</span></span>

<span data-ttu-id="ffb17-422">Yank le premier argument (après la commande) à partir de la ligne précédente de l’historique.</span><span class="sxs-lookup"><span data-stu-id="ffb17-422">Yank the first argument (after the command) from the previous history line.</span></span>
<span data-ttu-id="ffb17-423">Avec un argument, Yank le nième argument (à partir de 0), si l’argument est négatif, commencez par le dernier argument.</span><span class="sxs-lookup"><span data-stu-id="ffb17-423">With an argument, yank the nth argument (starting from 0), if the argument is negative, start from the last argument.</span></span>

- <span data-ttu-id="ffb17-424">Emacs- `<Ctrl+Alt+y>` , `<Escape,Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-424">Emacs: `<Ctrl+Alt+y>`, `<Escape,Ctrl+y>`</span></span>

### <a name="yankpop"></a><span data-ttu-id="ffb17-425">YankPop</span><span class="sxs-lookup"><span data-stu-id="ffb17-425">YankPop</span></span>

<span data-ttu-id="ffb17-426">Si l’opération précédente était Yank ou YankPop, remplacez le texte précédemment extrait par le texte supprimé suivant de l’instruction KILL-Ring.</span><span class="sxs-lookup"><span data-stu-id="ffb17-426">If the previous operation was Yank or YankPop, replace the previously yanked text with the next killed text from the kill-ring.</span></span>

- <span data-ttu-id="ffb17-427">Emacs- `<Alt+y>` , `<Escape,y>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-427">Emacs: `<Alt+y>`, `<Escape,y>`</span></span>

## <a name="cursor-movement-functions"></a><span data-ttu-id="ffb17-428">Fonctions de déplacement de curseur</span><span class="sxs-lookup"><span data-stu-id="ffb17-428">Cursor movement functions</span></span>

### <a name="backwardchar"></a><span data-ttu-id="ffb17-429">BackwardChar</span><span class="sxs-lookup"><span data-stu-id="ffb17-429">BackwardChar</span></span>

<span data-ttu-id="ffb17-430">Déplacer le curseur d’un caractère vers la gauche.</span><span class="sxs-lookup"><span data-stu-id="ffb17-430">Move the cursor one character to the left.</span></span> <span data-ttu-id="ffb17-431">Cela peut déplacer le curseur vers la ligne précédente de l’entrée multiligne.</span><span class="sxs-lookup"><span data-stu-id="ffb17-431">This may move the cursor to the previous line of multi-line input.</span></span>

- <span data-ttu-id="ffb17-432">Cmd `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-432">Cmd: `<LeftArrow>`</span></span>
- <span data-ttu-id="ffb17-433">Emacs- `<LeftArrow>` , `<Ctrl+b>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-433">Emacs: `<LeftArrow>`, `<Ctrl+b>`</span></span>
- <span data-ttu-id="ffb17-434">Mode d’insertion VI : `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-434">Vi insert mode: `<LeftArrow>`</span></span>
- <span data-ttu-id="ffb17-435">Mode de commande VI : `<LeftArrow>` , `<Backspace>` , `<h>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-435">Vi command mode: `<LeftArrow>`, `<Backspace>`, `<h>`</span></span>

### <a name="backwardword"></a><span data-ttu-id="ffb17-436">BackwardWord</span><span class="sxs-lookup"><span data-stu-id="ffb17-436">BackwardWord</span></span>

<span data-ttu-id="ffb17-437">Ramener le curseur au début du mot actuel, ou si entre les mots, le début du mot précédent.</span><span class="sxs-lookup"><span data-stu-id="ffb17-437">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="ffb17-438">Les limites de mots sont définies par un jeu de caractères configurable.</span><span class="sxs-lookup"><span data-stu-id="ffb17-438">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="ffb17-439">Cmd `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-439">Cmd: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="ffb17-440">Emacs- `<Alt+b>` , `<Escape,b>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-440">Emacs: `<Alt+b>`, `<Escape,b>`</span></span>
- <span data-ttu-id="ffb17-441">Mode d’insertion VI : `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-441">Vi insert mode: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="ffb17-442">Mode de commande VI : `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-442">Vi command mode: `<Ctrl+LeftArrow>`</span></span>

### <a name="beginningofline"></a><span data-ttu-id="ffb17-443">BeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="ffb17-443">BeginningOfLine</span></span>

<span data-ttu-id="ffb17-444">Si l’entrée comporte plusieurs lignes, se déplacer au début de la ligne active ou, le cas échéant, au début de la ligne, se déplacer au début de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="ffb17-444">If the input has multiple lines, move to the start of the current line, or if already at the start of the line, move to the start of the input.</span></span> <span data-ttu-id="ffb17-445">Si l’entrée comporte une seule ligne, accédez au début de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="ffb17-445">If the input has a single line, move to the start of the input.</span></span>

- <span data-ttu-id="ffb17-446">Cmd `<Home>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-446">Cmd: `<Home>`</span></span>
- <span data-ttu-id="ffb17-447">Emacs- `<Home>` , `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-447">Emacs: `<Home>`, `<Ctrl+a>`</span></span>
- <span data-ttu-id="ffb17-448">Mode d’insertion VI : `<Home>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-448">Vi insert mode: `<Home>`</span></span>
- <span data-ttu-id="ffb17-449">Mode de commande VI : `<Home>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-449">Vi command mode: `<Home>`</span></span>

### <a name="endofline"></a><span data-ttu-id="ffb17-450">EndOfLine</span><span class="sxs-lookup"><span data-stu-id="ffb17-450">EndOfLine</span></span>

<span data-ttu-id="ffb17-451">Si l’entrée comporte plusieurs lignes, passez à la fin de la ligne active ou, si elle se trouve déjà à la fin de la ligne, à la fin de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="ffb17-451">If the input has multiple lines, move to the end of the current line, or if already at the end of the line, move to the end of the input.</span></span> <span data-ttu-id="ffb17-452">Si l’entrée comporte une seule ligne, passez à la fin de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="ffb17-452">If the input has a single line, move to the end of the input.</span></span>

- <span data-ttu-id="ffb17-453">Cmd `<End>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-453">Cmd: `<End>`</span></span>
- <span data-ttu-id="ffb17-454">Emacs- `<End>` , `<Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-454">Emacs: `<End>`, `<Ctrl+e>`</span></span>
- <span data-ttu-id="ffb17-455">Mode d’insertion VI : `<End>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-455">Vi insert mode: `<End>`</span></span>

### <a name="forwardchar"></a><span data-ttu-id="ffb17-456">ForwardChar</span><span class="sxs-lookup"><span data-stu-id="ffb17-456">ForwardChar</span></span>

<span data-ttu-id="ffb17-457">Déplacer le curseur d’un caractère vers la droite.</span><span class="sxs-lookup"><span data-stu-id="ffb17-457">Move the cursor one character to the right.</span></span> <span data-ttu-id="ffb17-458">Cela peut déplacer le curseur à la ligne suivante de l’entrée multiligne.</span><span class="sxs-lookup"><span data-stu-id="ffb17-458">This may move the cursor to the next line of multi-line input.</span></span>

- <span data-ttu-id="ffb17-459">Cmd `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-459">Cmd: `<RightArrow>`</span></span>
- <span data-ttu-id="ffb17-460">Emacs- `<RightArrow>` , `<Ctrl+f>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-460">Emacs: `<RightArrow>`, `<Ctrl+f>`</span></span>
- <span data-ttu-id="ffb17-461">Mode d’insertion VI : `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-461">Vi insert mode: `<RightArrow>`</span></span>
- <span data-ttu-id="ffb17-462">Mode de commande VI : `<RightArrow>` , `<Space>` , `<l>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-462">Vi command mode: `<RightArrow>`, `<Space>`, `<l>`</span></span>

### <a name="forwardword"></a><span data-ttu-id="ffb17-463">ForwardWord</span><span class="sxs-lookup"><span data-stu-id="ffb17-463">ForwardWord</span></span>

<span data-ttu-id="ffb17-464">Déplacer le curseur vers l’avant jusqu’à la fin du mot actuel, ou si entre les mots, à la fin du mot suivant.</span><span class="sxs-lookup"><span data-stu-id="ffb17-464">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="ffb17-465">Les limites de mots sont définies par un jeu de caractères configurable.</span><span class="sxs-lookup"><span data-stu-id="ffb17-465">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="ffb17-466">Emacs- `<Alt+f>` , `<Escape,f>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-466">Emacs: `<Alt+f>`, `<Escape,f>`</span></span>

### <a name="gotobrace"></a><span data-ttu-id="ffb17-467">GotoBrace</span><span class="sxs-lookup"><span data-stu-id="ffb17-467">GotoBrace</span></span>

<span data-ttu-id="ffb17-468">Atteindre l’accolade correspondante, les parenthèses ou les crochets.</span><span class="sxs-lookup"><span data-stu-id="ffb17-468">Go to the matching brace, parenthesis, or square bracket.</span></span>

- <span data-ttu-id="ffb17-469">Cmd `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-469">Cmd: `<Ctrl+]>`</span></span>
- <span data-ttu-id="ffb17-470">Mode d’insertion VI : `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-470">Vi insert mode: `<Ctrl+]>`</span></span>
- <span data-ttu-id="ffb17-471">Mode de commande VI : `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-471">Vi command mode: `<Ctrl+]>`</span></span>

### <a name="gotocolumn"></a><span data-ttu-id="ffb17-472">GotoColumn</span><span class="sxs-lookup"><span data-stu-id="ffb17-472">GotoColumn</span></span>

<span data-ttu-id="ffb17-473">Accédez à la colonne indiquée par arg.</span><span class="sxs-lookup"><span data-stu-id="ffb17-473">Move to the column indicated by arg.</span></span>

- <span data-ttu-id="ffb17-474">Mode de commande VI : `<|>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-474">Vi command mode: `<|>`</span></span>

### <a name="gotofirstnonblankofline"></a><span data-ttu-id="ffb17-475">GotoFirstNonBlankOfLine</span><span class="sxs-lookup"><span data-stu-id="ffb17-475">GotoFirstNonBlankOfLine</span></span>

<span data-ttu-id="ffb17-476">Placez le curseur sur le premier caractère non vide de la ligne.</span><span class="sxs-lookup"><span data-stu-id="ffb17-476">Move the cursor to the first non-blank character in the line.</span></span>

- <span data-ttu-id="ffb17-477">Mode de commande VI : `<^>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-477">Vi command mode: `<^>`</span></span>

### <a name="movetoendofline"></a><span data-ttu-id="ffb17-478">MoveToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="ffb17-478">MoveToEndOfLine</span></span>

<span data-ttu-id="ffb17-479">Placez le curseur à la fin de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="ffb17-479">Move the cursor to the end of the input.</span></span>

- <span data-ttu-id="ffb17-480">Mode de commande VI : `<End>` , `<$>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-480">Vi command mode: `<End>`, `<$>`</span></span>

### <a name="nextline"></a><span data-ttu-id="ffb17-481">NextLine</span><span class="sxs-lookup"><span data-stu-id="ffb17-481">NextLine</span></span>

<span data-ttu-id="ffb17-482">Déplacer le curseur sur la ligne suivante.</span><span class="sxs-lookup"><span data-stu-id="ffb17-482">Move the cursor to the next line.</span></span>

- <span data-ttu-id="ffb17-483">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="ffb17-483">Function is unbound.</span></span>

### <a name="nextword"></a><span data-ttu-id="ffb17-484">NextWord</span><span class="sxs-lookup"><span data-stu-id="ffb17-484">NextWord</span></span>

<span data-ttu-id="ffb17-485">Déplacer le curseur vers l’avant jusqu’au début du mot suivant.</span><span class="sxs-lookup"><span data-stu-id="ffb17-485">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="ffb17-486">Les limites de mots sont définies par un jeu de caractères configurable.</span><span class="sxs-lookup"><span data-stu-id="ffb17-486">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="ffb17-487">Cmd `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-487">Cmd: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="ffb17-488">Mode d’insertion VI : `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-488">Vi insert mode: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="ffb17-489">Mode de commande VI : `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-489">Vi command mode: `<Ctrl+RightArrow>`</span></span>

### <a name="nextwordend"></a><span data-ttu-id="ffb17-490">NextWordEnd</span><span class="sxs-lookup"><span data-stu-id="ffb17-490">NextWordEnd</span></span>

<span data-ttu-id="ffb17-491">Déplacer le curseur vers l’avant jusqu’à la fin du mot actuel, ou si entre les mots, à la fin du mot suivant.</span><span class="sxs-lookup"><span data-stu-id="ffb17-491">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="ffb17-492">Les limites de mots sont définies par un jeu de caractères configurable.</span><span class="sxs-lookup"><span data-stu-id="ffb17-492">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="ffb17-493">Mode de commande VI : `<e>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-493">Vi command mode: `<e>`</span></span>

### <a name="previousline"></a><span data-ttu-id="ffb17-494">PreviousLine</span><span class="sxs-lookup"><span data-stu-id="ffb17-494">PreviousLine</span></span>

<span data-ttu-id="ffb17-495">Placez le curseur sur la ligne précédente.</span><span class="sxs-lookup"><span data-stu-id="ffb17-495">Move the cursor to the previous line.</span></span>

- <span data-ttu-id="ffb17-496">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="ffb17-496">Function is unbound.</span></span>

### <a name="shellbackwardword"></a><span data-ttu-id="ffb17-497">ShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="ffb17-497">ShellBackwardWord</span></span>

<span data-ttu-id="ffb17-498">Ramener le curseur au début du mot actuel, ou si entre les mots, le début du mot précédent.</span><span class="sxs-lookup"><span data-stu-id="ffb17-498">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="ffb17-499">Les limites de mots sont définies par les jetons PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ffb17-499">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="ffb17-500">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="ffb17-500">Function is unbound.</span></span>

### <a name="shellforwardword"></a><span data-ttu-id="ffb17-501">ShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="ffb17-501">ShellForwardWord</span></span>

<span data-ttu-id="ffb17-502">Déplacer le curseur vers l’avant jusqu’au début du mot suivant.</span><span class="sxs-lookup"><span data-stu-id="ffb17-502">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="ffb17-503">Les limites de mots sont définies par les jetons PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ffb17-503">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="ffb17-504">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="ffb17-504">Function is unbound.</span></span>

### <a name="shellnextword"></a><span data-ttu-id="ffb17-505">ShellNextWord</span><span class="sxs-lookup"><span data-stu-id="ffb17-505">ShellNextWord</span></span>

<span data-ttu-id="ffb17-506">Déplacer le curseur vers l’avant jusqu’à la fin du mot actuel, ou si entre les mots, à la fin du mot suivant.</span><span class="sxs-lookup"><span data-stu-id="ffb17-506">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="ffb17-507">Les limites de mots sont définies par les jetons PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ffb17-507">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="ffb17-508">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="ffb17-508">Function is unbound.</span></span>

### <a name="vibackwardword"></a><span data-ttu-id="ffb17-509">ViBackwardWord</span><span class="sxs-lookup"><span data-stu-id="ffb17-509">ViBackwardWord</span></span>

<span data-ttu-id="ffb17-510">Ramener le curseur au début du mot actuel, ou si entre les mots, le début du mot précédent.</span><span class="sxs-lookup"><span data-stu-id="ffb17-510">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="ffb17-511">Les limites de mots sont définies par un jeu de caractères configurable.</span><span class="sxs-lookup"><span data-stu-id="ffb17-511">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="ffb17-512">Mode de commande VI : `<b>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-512">Vi command mode: `<b>`</span></span>

### <a name="viendofglob"></a><span data-ttu-id="ffb17-513">ViEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="ffb17-513">ViEndOfGlob</span></span>

<span data-ttu-id="ffb17-514">Déplace le curseur à la fin du mot, en utilisant uniquement des espaces blancs comme délimiteurs.</span><span class="sxs-lookup"><span data-stu-id="ffb17-514">Moves the cursor to the end of the word, using only white space as delimiters.</span></span>

- <span data-ttu-id="ffb17-515">Mode de commande VI : `<E>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-515">Vi command mode: `<E>`</span></span>

### <a name="viendofpreviousglob"></a><span data-ttu-id="ffb17-516">ViEndOfPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="ffb17-516">ViEndOfPreviousGlob</span></span>

<span data-ttu-id="ffb17-517">Passe à la fin du mot précédent, en utilisant uniquement un espace blanc comme délimiteur de mot.</span><span class="sxs-lookup"><span data-stu-id="ffb17-517">Moves to the end of the previous word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="ffb17-518">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="ffb17-518">Function is unbound.</span></span>

### <a name="vigotobrace"></a><span data-ttu-id="ffb17-519">ViGotoBrace</span><span class="sxs-lookup"><span data-stu-id="ffb17-519">ViGotoBrace</span></span>

<span data-ttu-id="ffb17-520">Semblable à GotoBrace, mais est basé sur un caractère et non sur un jeton.</span><span class="sxs-lookup"><span data-stu-id="ffb17-520">Similar to GotoBrace, but is character based instead of token based.</span></span>

- <span data-ttu-id="ffb17-521">Mode de commande VI : `<%>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-521">Vi command mode: `<%>`</span></span>

### <a name="vinextglob"></a><span data-ttu-id="ffb17-522">ViNextGlob</span><span class="sxs-lookup"><span data-stu-id="ffb17-522">ViNextGlob</span></span>

<span data-ttu-id="ffb17-523">Passe au mot suivant, en utilisant uniquement un espace blanc comme délimiteur de mot.</span><span class="sxs-lookup"><span data-stu-id="ffb17-523">Moves to the next word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="ffb17-524">Mode de commande VI : `<W>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-524">Vi command mode: `<W>`</span></span>

### <a name="vinextword"></a><span data-ttu-id="ffb17-525">ViNextWord</span><span class="sxs-lookup"><span data-stu-id="ffb17-525">ViNextWord</span></span>

<span data-ttu-id="ffb17-526">Déplacer le curseur vers l’avant jusqu’au début du mot suivant.</span><span class="sxs-lookup"><span data-stu-id="ffb17-526">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="ffb17-527">Les limites de mots sont définies par un jeu de caractères configurable.</span><span class="sxs-lookup"><span data-stu-id="ffb17-527">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="ffb17-528">Mode de commande VI : `<w>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-528">Vi command mode: `<w>`</span></span>

## <a name="history-functions"></a><span data-ttu-id="ffb17-529">Fonctions d’historique</span><span class="sxs-lookup"><span data-stu-id="ffb17-529">History functions</span></span>

### <a name="beginningofhistory"></a><span data-ttu-id="ffb17-530">BeginningOfHistory</span><span class="sxs-lookup"><span data-stu-id="ffb17-530">BeginningOfHistory</span></span>

<span data-ttu-id="ffb17-531">Accéder au premier élément de l’historique.</span><span class="sxs-lookup"><span data-stu-id="ffb17-531">Move to the first item in the history.</span></span>

- <span data-ttu-id="ffb17-532">Emacs- `<Alt+`<>\`</span><span class="sxs-lookup"><span data-stu-id="ffb17-532">Emacs: `<Alt+`<>\`</span></span>

### <a name="clearhistory"></a><span data-ttu-id="ffb17-533">ClearHistory</span><span class="sxs-lookup"><span data-stu-id="ffb17-533">ClearHistory</span></span>

<span data-ttu-id="ffb17-534">Efface l’historique dans PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="ffb17-534">Clears history in PSReadLine.</span></span> <span data-ttu-id="ffb17-535">Cela n’affecte pas l’historique PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ffb17-535">This does not affect PowerShell history.</span></span>

- <span data-ttu-id="ffb17-536">Cmd `<Alt+F7>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-536">Cmd: `<Alt+F7>`</span></span>

### <a name="endofhistory"></a><span data-ttu-id="ffb17-537">EndOfHistory</span><span class="sxs-lookup"><span data-stu-id="ffb17-537">EndOfHistory</span></span>

<span data-ttu-id="ffb17-538">Accéder au dernier élément (l’entrée en cours) dans l’historique.</span><span class="sxs-lookup"><span data-stu-id="ffb17-538">Move to the last item (the current input) in the history.</span></span>

- <span data-ttu-id="ffb17-539">Emacs- `<Alt+>>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-539">Emacs: `<Alt+>>`</span></span>

### <a name="forwardsearchhistory"></a><span data-ttu-id="ffb17-540">ForwardSearchHistory</span><span class="sxs-lookup"><span data-stu-id="ffb17-540">ForwardSearchHistory</span></span>

<span data-ttu-id="ffb17-541">Effectuer une recherche incrémentielle par progression dans l’historique.</span><span class="sxs-lookup"><span data-stu-id="ffb17-541">Perform an incremental forward search through history.</span></span>

- <span data-ttu-id="ffb17-542">Cmd `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-542">Cmd: `<Ctrl+s>`</span></span>
- <span data-ttu-id="ffb17-543">Emacs- `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-543">Emacs: `<Ctrl+s>`</span></span>

### <a name="historysearchbackward"></a><span data-ttu-id="ffb17-544">HistorySearchBackward</span><span class="sxs-lookup"><span data-stu-id="ffb17-544">HistorySearchBackward</span></span>

<span data-ttu-id="ffb17-545">Remplacez l’entrée actuelle par l’élément « Previous » de l’historique PSReadLine qui correspond aux caractères entre le début et l’entrée et le curseur.</span><span class="sxs-lookup"><span data-stu-id="ffb17-545">Replace the current input with the 'previous' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="ffb17-546">Cmd `<F8>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-546">Cmd: `<F8>`</span></span>

### <a name="historysearchforward"></a><span data-ttu-id="ffb17-547">HistorySearchForward</span><span class="sxs-lookup"><span data-stu-id="ffb17-547">HistorySearchForward</span></span>

<span data-ttu-id="ffb17-548">Remplacez l’entrée actuelle par l’élément « Next » de l’historique PSReadLine qui correspond aux caractères entre le début et l’entrée et le curseur.</span><span class="sxs-lookup"><span data-stu-id="ffb17-548">Replace the current input with the 'next' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="ffb17-549">Cmd `<Shift+F8>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-549">Cmd: `<Shift+F8>`</span></span>

### <a name="nexthistory"></a><span data-ttu-id="ffb17-550">NextHistory</span><span class="sxs-lookup"><span data-stu-id="ffb17-550">NextHistory</span></span>

<span data-ttu-id="ffb17-551">Remplacez l’entrée actuelle par l’élément « Next » de l’historique PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="ffb17-551">Replace the current input with the 'next' item from PSReadLine history.</span></span>

- <span data-ttu-id="ffb17-552">Cmd `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-552">Cmd: `<DownArrow>`</span></span>
- <span data-ttu-id="ffb17-553">Emacs- `<DownArrow>` , `<Ctrl+n>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-553">Emacs: `<DownArrow>`, `<Ctrl+n>`</span></span>
- <span data-ttu-id="ffb17-554">Mode d’insertion VI : `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-554">Vi insert mode: `<DownArrow>`</span></span>
- <span data-ttu-id="ffb17-555">Mode de commande VI : `<DownArrow>` , `<j>` , `<+>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-555">Vi command mode: `<DownArrow>`, `<j>`, `<+>`</span></span>

### <a name="previoushistory"></a><span data-ttu-id="ffb17-556">PreviousHistory</span><span class="sxs-lookup"><span data-stu-id="ffb17-556">PreviousHistory</span></span>

<span data-ttu-id="ffb17-557">Remplacez l’entrée actuelle par l’élément « Previous » de l’historique PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="ffb17-557">Replace the current input with the 'previous' item from PSReadLine history.</span></span>

- <span data-ttu-id="ffb17-558">Cmd `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-558">Cmd: `<UpArrow>`</span></span>
- <span data-ttu-id="ffb17-559">Emacs- `<UpArrow>` , `<Ctrl+p>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-559">Emacs: `<UpArrow>`, `<Ctrl+p>`</span></span>
- <span data-ttu-id="ffb17-560">Mode d’insertion VI : `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-560">Vi insert mode: `<UpArrow>`</span></span>
- <span data-ttu-id="ffb17-561">Mode de commande VI : `<UpArrow>` , `<k>` , `<->`</span><span class="sxs-lookup"><span data-stu-id="ffb17-561">Vi command mode: `<UpArrow>`, `<k>`, `<->`</span></span>

### <a name="reversesearchhistory"></a><span data-ttu-id="ffb17-562">ReverseSearchHistory</span><span class="sxs-lookup"><span data-stu-id="ffb17-562">ReverseSearchHistory</span></span>

<span data-ttu-id="ffb17-563">Effectuer une recherche incrémentielle incrémentielle dans l’historique.</span><span class="sxs-lookup"><span data-stu-id="ffb17-563">Perform an incremental backward search through history.</span></span>

- <span data-ttu-id="ffb17-564">Cmd `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-564">Cmd: `<Ctrl+r>`</span></span>
- <span data-ttu-id="ffb17-565">Emacs- `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-565">Emacs: `<Ctrl+r>`</span></span>

### <a name="visearchhistorybackward"></a><span data-ttu-id="ffb17-566">ViSearchHistoryBackward</span><span class="sxs-lookup"><span data-stu-id="ffb17-566">ViSearchHistoryBackward</span></span>

<span data-ttu-id="ffb17-567">Demande une chaîne de recherche et lance la recherche sur AcceptLine.</span><span class="sxs-lookup"><span data-stu-id="ffb17-567">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="ffb17-568">Mode d’insertion VI : `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-568">Vi insert mode: `<Ctrl+r>`</span></span>
- <span data-ttu-id="ffb17-569">Mode de commande VI : `</>` , `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-569">Vi command mode: `</>`, `<Ctrl+r>`</span></span>

## <a name="completion-functions"></a><span data-ttu-id="ffb17-570">Fonctions d’achèvement</span><span class="sxs-lookup"><span data-stu-id="ffb17-570">Completion functions</span></span>

### <a name="complete"></a><span data-ttu-id="ffb17-571">Terminé</span><span class="sxs-lookup"><span data-stu-id="ffb17-571">Complete</span></span>

<span data-ttu-id="ffb17-572">Tentative d’exécution de l’opération sur le texte entourant le curseur.</span><span class="sxs-lookup"><span data-stu-id="ffb17-572">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="ffb17-573">S’il existe plusieurs saisies semi-automatiques possibles, le plus long préfixe non ambigu est utilisé pour la finalisation.</span><span class="sxs-lookup"><span data-stu-id="ffb17-573">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="ffb17-574">Si vous essayez de terminer la saisie semi-automatique la plus longue, une liste des saisies semi-automatiques possibles s’affiche.</span><span class="sxs-lookup"><span data-stu-id="ffb17-574">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="ffb17-575">Emacs- `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-575">Emacs: `<Tab>`</span></span>

### <a name="menucomplete"></a><span data-ttu-id="ffb17-576">MenuComplete</span><span class="sxs-lookup"><span data-stu-id="ffb17-576">MenuComplete</span></span>

<span data-ttu-id="ffb17-577">Tentative d’exécution de l’opération sur le texte entourant le curseur.</span><span class="sxs-lookup"><span data-stu-id="ffb17-577">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="ffb17-578">S’il existe plusieurs saisies semi-automatiques possibles, le plus long préfixe non ambigu est utilisé pour la finalisation.</span><span class="sxs-lookup"><span data-stu-id="ffb17-578">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="ffb17-579">Si vous essayez de terminer la saisie semi-automatique la plus longue, une liste des saisies semi-automatiques possibles s’affiche.</span><span class="sxs-lookup"><span data-stu-id="ffb17-579">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="ffb17-580">Cmd `<Ctrl+Space>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-580">Cmd: `<Ctrl+Space>`</span></span>
- <span data-ttu-id="ffb17-581">Emacs- `<Ctrl+Space>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-581">Emacs: `<Ctrl+Space>`</span></span>

### <a name="possiblecompletions"></a><span data-ttu-id="ffb17-582">PossibleCompletions</span><span class="sxs-lookup"><span data-stu-id="ffb17-582">PossibleCompletions</span></span>

<span data-ttu-id="ffb17-583">Affiche la liste des saisies semi-automatiques possibles.</span><span class="sxs-lookup"><span data-stu-id="ffb17-583">Display the list of possible completions.</span></span>

- <span data-ttu-id="ffb17-584">Emacs- `<Alt+=>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-584">Emacs: `<Alt+=>`</span></span>
- <span data-ttu-id="ffb17-585">Mode d’insertion VI : `<Ctrl+Space>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-585">Vi insert mode: `<Ctrl+Space>`</span></span>
- <span data-ttu-id="ffb17-586">Mode de commande VI : `<Ctrl+Space>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-586">Vi command mode: `<Ctrl+Space>`</span></span>

### <a name="tabcompletenext"></a><span data-ttu-id="ffb17-587">TabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="ffb17-587">TabCompleteNext</span></span>

<span data-ttu-id="ffb17-588">Tente de terminer le texte entourant le curseur avec la prochaine saisie semi-automatique disponible.</span><span class="sxs-lookup"><span data-stu-id="ffb17-588">Attempt to complete the text surrounding the cursor with the next available completion.</span></span>

- <span data-ttu-id="ffb17-589">Cmd `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-589">Cmd: `<Tab>`</span></span>
- <span data-ttu-id="ffb17-590">Mode de commande VI : `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-590">Vi command mode: `<Tab>`</span></span>

### <a name="tabcompleteprevious"></a><span data-ttu-id="ffb17-591">TabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="ffb17-591">TabCompletePrevious</span></span>

<span data-ttu-id="ffb17-592">Tente de terminer le texte entourant le curseur avec l’achèvement disponible précédent.</span><span class="sxs-lookup"><span data-stu-id="ffb17-592">Attempt to complete the text surrounding the cursor with the previous available completion.</span></span>

- <span data-ttu-id="ffb17-593">Cmd `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-593">Cmd: `<Shift+Tab>`</span></span>
- <span data-ttu-id="ffb17-594">Mode de commande VI : `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-594">Vi command mode: `<Shift+Tab>`</span></span>

### <a name="vitabcompletenext"></a><span data-ttu-id="ffb17-595">ViTabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="ffb17-595">ViTabCompleteNext</span></span>

<span data-ttu-id="ffb17-596">Met fin au groupe d’édition actuel, si nécessaire, et appelle TabCompleteNext.</span><span class="sxs-lookup"><span data-stu-id="ffb17-596">Ends the current edit group, if needed, and invokes TabCompleteNext.</span></span>

- <span data-ttu-id="ffb17-597">Mode d’insertion VI : `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-597">Vi insert mode: `<Tab>`</span></span>

### <a name="vitabcompleteprevious"></a><span data-ttu-id="ffb17-598">ViTabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="ffb17-598">ViTabCompletePrevious</span></span>

<span data-ttu-id="ffb17-599">Met fin au groupe d’édition actuel, si nécessaire, et appelle TabCompletePrevious.</span><span class="sxs-lookup"><span data-stu-id="ffb17-599">Ends the current edit group, if needed, and invokes TabCompletePrevious.</span></span>

- <span data-ttu-id="ffb17-600">Mode d’insertion VI : `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-600">Vi insert mode: `<Shift+Tab>`</span></span>

## <a name="miscellaneous-functions"></a><span data-ttu-id="ffb17-601">Fonctions diverses</span><span class="sxs-lookup"><span data-stu-id="ffb17-601">Miscellaneous functions</span></span>

### <a name="capturescreen"></a><span data-ttu-id="ffb17-602">CaptureScreen</span><span class="sxs-lookup"><span data-stu-id="ffb17-602">CaptureScreen</span></span>

<span data-ttu-id="ffb17-603">Démarrer la capture d’écran interactive-flèches haut et bas sélectionnez lignes, entrez copie le texte sélectionné dans le presse-papiers en tant que texte et html.</span><span class="sxs-lookup"><span data-stu-id="ffb17-603">Start interactive screen capture - up/down arrows select lines, enter copies selected text to clipboard as text and html.</span></span>

- <span data-ttu-id="ffb17-604">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="ffb17-604">Function is unbound.</span></span>

### <a name="clearscreen"></a><span data-ttu-id="ffb17-605">ClearScreen</span><span class="sxs-lookup"><span data-stu-id="ffb17-605">ClearScreen</span></span>

<span data-ttu-id="ffb17-606">Effacez l’écran et dessinez la ligne active en haut de l’écran.</span><span class="sxs-lookup"><span data-stu-id="ffb17-606">Clear the screen and draw the current line at the top of the screen.</span></span>

- <span data-ttu-id="ffb17-607">Cmd `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-607">Cmd: `<Ctrl+l>`</span></span>
- <span data-ttu-id="ffb17-608">Emacs- `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-608">Emacs: `<Ctrl+l>`</span></span>
- <span data-ttu-id="ffb17-609">Mode d’insertion VI : `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-609">Vi insert mode: `<Ctrl+l>`</span></span>
- <span data-ttu-id="ffb17-610">Mode de commande VI : `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-610">Vi command mode: `<Ctrl+l>`</span></span>

### <a name="digitargument"></a><span data-ttu-id="ffb17-611">DigitArgument</span><span class="sxs-lookup"><span data-stu-id="ffb17-611">DigitArgument</span></span>

<span data-ttu-id="ffb17-612">Démarrez un nouvel argument digit à passer à d’autres fonctions.</span><span class="sxs-lookup"><span data-stu-id="ffb17-612">Start a new digit argument to pass to other functions.</span></span>

- <span data-ttu-id="ffb17-613">Cmd : `<Alt+0>` ,,,,, `<Alt+1>` `<Alt+2>` `<Alt+3>` `<Alt+4>` `<Alt+5>` , `<Alt+6>` , `<Alt+7>` , `<Alt+8>` , `<Alt+9>` , `<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="ffb17-613">Cmd: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="ffb17-614">Emacs-,,,,,,,,, `<Alt+0>` `<Alt+1>` `<Alt+2>` `<Alt+3>` `<Alt+4>` `<Alt+5>` `<Alt+6>` `<Alt+7>` `<Alt+8>` , `<Alt+9>` , `<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="ffb17-614">Emacs: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="ffb17-615">Mode de commande VI : `<0>` , `<1>` ,, `<2>` `<3>` , `<4>` , `<5>` , `<6>` , `<7>` , `<8>` , `<9>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-615">Vi command mode: `<0>`, `<1>`, `<2>`, `<3>`, `<4>`, `<5>`, `<6>`, `<7>`, `<8>`, `<9>`</span></span>

### <a name="invokeprompt"></a><span data-ttu-id="ffb17-616">InvokePrompt</span><span class="sxs-lookup"><span data-stu-id="ffb17-616">InvokePrompt</span></span>

<span data-ttu-id="ffb17-617">Efface l’invite en cours et appelle la fonction prompt pour réafficher l’invite.</span><span class="sxs-lookup"><span data-stu-id="ffb17-617">Erases the current prompt and calls the prompt function to redisplay the prompt.</span></span> <span data-ttu-id="ffb17-618">Utile pour les gestionnaires de clés personnalisés qui changent d’État, par exemple modifier le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="ffb17-618">Useful for custom key handlers that change state, e.g. change the current directory.</span></span>

- <span data-ttu-id="ffb17-619">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="ffb17-619">Function is unbound.</span></span>

### <a name="scrolldisplaydown"></a><span data-ttu-id="ffb17-620">ScrollDisplayDown</span><span class="sxs-lookup"><span data-stu-id="ffb17-620">ScrollDisplayDown</span></span>

<span data-ttu-id="ffb17-621">Faites défiler l’écran vers le volet d’affichage.</span><span class="sxs-lookup"><span data-stu-id="ffb17-621">Scroll the display down one screen.</span></span>

- <span data-ttu-id="ffb17-622">Cmd `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-622">Cmd: `<PageDown>`</span></span>
- <span data-ttu-id="ffb17-623">Emacs- `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-623">Emacs: `<PageDown>`</span></span>

### <a name="scrolldisplaydownline"></a><span data-ttu-id="ffb17-624">ScrollDisplayDownLine</span><span class="sxs-lookup"><span data-stu-id="ffb17-624">ScrollDisplayDownLine</span></span>

<span data-ttu-id="ffb17-625">Faites défiler l’affichage d’une ligne vers le dessous.</span><span class="sxs-lookup"><span data-stu-id="ffb17-625">Scroll the display down one line.</span></span>

- <span data-ttu-id="ffb17-626">Cmd `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-626">Cmd: `<Ctrl+PageDown>`</span></span>
- <span data-ttu-id="ffb17-627">Emacs- `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-627">Emacs: `<Ctrl+PageDown>`</span></span>

### <a name="scrolldisplaytocursor"></a><span data-ttu-id="ffb17-628">ScrollDisplayToCursor</span><span class="sxs-lookup"><span data-stu-id="ffb17-628">ScrollDisplayToCursor</span></span>

<span data-ttu-id="ffb17-629">Faites défiler l’affichage jusqu’au curseur.</span><span class="sxs-lookup"><span data-stu-id="ffb17-629">Scroll the display to the cursor.</span></span>

- <span data-ttu-id="ffb17-630">Emacs- `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-630">Emacs: `<Ctrl+End>`</span></span>

### <a name="scrolldisplaytop"></a><span data-ttu-id="ffb17-631">ScrollDisplayTop</span><span class="sxs-lookup"><span data-stu-id="ffb17-631">ScrollDisplayTop</span></span>

<span data-ttu-id="ffb17-632">Faites défiler l’affichage vers le haut.</span><span class="sxs-lookup"><span data-stu-id="ffb17-632">Scroll the display to the top.</span></span>

- <span data-ttu-id="ffb17-633">Emacs- `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-633">Emacs: `<Ctrl+Home>`</span></span>

### <a name="scrolldisplayup"></a><span data-ttu-id="ffb17-634">ScrollDisplayUp</span><span class="sxs-lookup"><span data-stu-id="ffb17-634">ScrollDisplayUp</span></span>

<span data-ttu-id="ffb17-635">Faites défiler l’écran afficher vers le haut.</span><span class="sxs-lookup"><span data-stu-id="ffb17-635">Scroll the display up one screen.</span></span>

- <span data-ttu-id="ffb17-636">Cmd `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-636">Cmd: `<PageUp>`</span></span>
- <span data-ttu-id="ffb17-637">Emacs- `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-637">Emacs: `<PageUp>`</span></span>

### <a name="scrolldisplayupline"></a><span data-ttu-id="ffb17-638">ScrollDisplayUpLine</span><span class="sxs-lookup"><span data-stu-id="ffb17-638">ScrollDisplayUpLine</span></span>

<span data-ttu-id="ffb17-639">Faites défiler l’affichage d’une ligne vers le haut.</span><span class="sxs-lookup"><span data-stu-id="ffb17-639">Scroll the display up one line.</span></span>

- <span data-ttu-id="ffb17-640">Cmd `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-640">Cmd: `<Ctrl+PageUp>`</span></span>
- <span data-ttu-id="ffb17-641">Emacs- `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-641">Emacs: `<Ctrl+PageUp>`</span></span>

### <a name="selfinsert"></a><span data-ttu-id="ffb17-642">SelfInsert</span><span class="sxs-lookup"><span data-stu-id="ffb17-642">SelfInsert</span></span>

<span data-ttu-id="ffb17-643">Insérez la clé.</span><span class="sxs-lookup"><span data-stu-id="ffb17-643">Insert the key.</span></span>

- <span data-ttu-id="ffb17-644">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="ffb17-644">Function is unbound.</span></span>

### <a name="showkeybindings"></a><span data-ttu-id="ffb17-645">ShowKeyBindings</span><span class="sxs-lookup"><span data-stu-id="ffb17-645">ShowKeyBindings</span></span>

<span data-ttu-id="ffb17-646">Affiche toutes les clés liées.</span><span class="sxs-lookup"><span data-stu-id="ffb17-646">Show all bound keys.</span></span>

- <span data-ttu-id="ffb17-647">Cmd `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-647">Cmd: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="ffb17-648">Emacs- `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-648">Emacs: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="ffb17-649">Mode d’insertion VI : `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-649">Vi insert mode: `<Ctrl+Alt+?>`</span></span>

### <a name="vicommandmode"></a><span data-ttu-id="ffb17-650">ViCommandMode</span><span class="sxs-lookup"><span data-stu-id="ffb17-650">ViCommandMode</span></span>

<span data-ttu-id="ffb17-651">Basculez le mode d’opération actuel de Vi-Insert à VI-Command.</span><span class="sxs-lookup"><span data-stu-id="ffb17-651">Switch the current operating mode from Vi-Insert to Vi-Command.</span></span>

- <span data-ttu-id="ffb17-652">Mode d’insertion VI : `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-652">Vi insert mode: `<Escape>`</span></span>

### <a name="vidigitargumentinchord"></a><span data-ttu-id="ffb17-653">ViDigitArgumentInChord</span><span class="sxs-lookup"><span data-stu-id="ffb17-653">ViDigitArgumentInChord</span></span>

<span data-ttu-id="ffb17-654">Démarrez un nouvel argument digit à passer à d’autres fonctions dans l’un des cordes de VI.</span><span class="sxs-lookup"><span data-stu-id="ffb17-654">Start a new digit argument to pass to other functions while in one of vi's chords.</span></span>

- <span data-ttu-id="ffb17-655">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="ffb17-655">Function is unbound.</span></span>

### <a name="vieditvisually"></a><span data-ttu-id="ffb17-656">ViEditVisually</span><span class="sxs-lookup"><span data-stu-id="ffb17-656">ViEditVisually</span></span>

<span data-ttu-id="ffb17-657">Modifiez la ligne de commande dans un éditeur de texte spécifié par $env : EDITOR ou $env : VISUAL.</span><span class="sxs-lookup"><span data-stu-id="ffb17-657">Edit the command line in a text editor specified by $env:EDITOR or $env:VISUAL.</span></span>

- <span data-ttu-id="ffb17-658">Emacs- `<Ctrl+x,Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-658">Emacs: `<Ctrl+x,Ctrl+e>`</span></span>
- <span data-ttu-id="ffb17-659">Mode de commande VI : `<v>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-659">Vi command mode: `<v>`</span></span>

### <a name="viexit"></a><span data-ttu-id="ffb17-660">ViExit</span><span class="sxs-lookup"><span data-stu-id="ffb17-660">ViExit</span></span>

<span data-ttu-id="ffb17-661">Quitte l’interpréteur de commandes.</span><span class="sxs-lookup"><span data-stu-id="ffb17-661">Exits the shell.</span></span>

- <span data-ttu-id="ffb17-662">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="ffb17-662">Function is unbound.</span></span>

### <a name="viinsertmode"></a><span data-ttu-id="ffb17-663">ViInsertMode</span><span class="sxs-lookup"><span data-stu-id="ffb17-663">ViInsertMode</span></span>

<span data-ttu-id="ffb17-664">Basculez en mode insertion.</span><span class="sxs-lookup"><span data-stu-id="ffb17-664">Switch to Insert mode.</span></span>

- <span data-ttu-id="ffb17-665">Mode de commande VI : `<i>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-665">Vi command mode: `<i>`</span></span>

### <a name="whatiskey"></a><span data-ttu-id="ffb17-666">WhatIsKey</span><span class="sxs-lookup"><span data-stu-id="ffb17-666">WhatIsKey</span></span>

<span data-ttu-id="ffb17-667">Lisez une clé et dites-moi à quoi la clé est liée.</span><span class="sxs-lookup"><span data-stu-id="ffb17-667">Read a key and tell me what the key is bound to.</span></span>

- <span data-ttu-id="ffb17-668">Cmd `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-668">Cmd: `<Alt+?>`</span></span>
- <span data-ttu-id="ffb17-669">Emacs- `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-669">Emacs: `<Alt+?>`</span></span>

## <a name="selection-functions"></a><span data-ttu-id="ffb17-670">Fonctions de sélection</span><span class="sxs-lookup"><span data-stu-id="ffb17-670">Selection functions</span></span>

### <a name="exchangepointandmark"></a><span data-ttu-id="ffb17-671">ExchangePointAndMark</span><span class="sxs-lookup"><span data-stu-id="ffb17-671">ExchangePointAndMark</span></span>

<span data-ttu-id="ffb17-672">Le curseur est placé à l’emplacement de la marque et la marque est déplacée vers l’emplacement du curseur.</span><span class="sxs-lookup"><span data-stu-id="ffb17-672">The cursor is placed at the location of the mark and the mark is moved to the location of the cursor.</span></span>

- <span data-ttu-id="ffb17-673">Emacs- `<Ctrl+x,Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-673">Emacs: `<Ctrl+x,Ctrl+x>`</span></span>

### <a name="selectall"></a><span data-ttu-id="ffb17-674">SelectAll</span><span class="sxs-lookup"><span data-stu-id="ffb17-674">SelectAll</span></span>

<span data-ttu-id="ffb17-675">Sélectionnez la ligne entière.</span><span class="sxs-lookup"><span data-stu-id="ffb17-675">Select the entire line.</span></span>

- <span data-ttu-id="ffb17-676">Cmd `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-676">Cmd: `<Ctrl+a>`</span></span>

### <a name="selectbackwardchar"></a><span data-ttu-id="ffb17-677">SelectBackwardChar</span><span class="sxs-lookup"><span data-stu-id="ffb17-677">SelectBackwardChar</span></span>

<span data-ttu-id="ffb17-678">Ajustez la sélection actuelle pour inclure le caractère précédent.</span><span class="sxs-lookup"><span data-stu-id="ffb17-678">Adjust the current selection to include the previous character.</span></span>

- <span data-ttu-id="ffb17-679">Cmd `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-679">Cmd: `<Shift+LeftArrow>`</span></span>
- <span data-ttu-id="ffb17-680">Emacs- `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-680">Emacs: `<Shift+LeftArrow>`</span></span>

### <a name="selectbackwardsline"></a><span data-ttu-id="ffb17-681">SelectBackwardsLine</span><span class="sxs-lookup"><span data-stu-id="ffb17-681">SelectBackwardsLine</span></span>

<span data-ttu-id="ffb17-682">Ajustez la sélection actuelle à inclure à partir du curseur jusqu’au début de la ligne.</span><span class="sxs-lookup"><span data-stu-id="ffb17-682">Adjust the current selection to include from the cursor to the start of the line.</span></span>

- <span data-ttu-id="ffb17-683">Cmd `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-683">Cmd: `<Shift+Home>`</span></span>
- <span data-ttu-id="ffb17-684">Emacs- `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-684">Emacs: `<Shift+Home>`</span></span>

### <a name="selectbackwardword"></a><span data-ttu-id="ffb17-685">SelectBackwardWord</span><span class="sxs-lookup"><span data-stu-id="ffb17-685">SelectBackwardWord</span></span>

<span data-ttu-id="ffb17-686">Ajustez la sélection actuelle pour inclure le mot précédent.</span><span class="sxs-lookup"><span data-stu-id="ffb17-686">Adjust the current selection to include the previous word.</span></span>

- <span data-ttu-id="ffb17-687">Cmd `<Shift+Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-687">Cmd: `<Shift+Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="ffb17-688">Emacs- `<Alt+B>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-688">Emacs: `<Alt+B>`</span></span>

### <a name="selectforwardchar"></a><span data-ttu-id="ffb17-689">SelectForwardChar</span><span class="sxs-lookup"><span data-stu-id="ffb17-689">SelectForwardChar</span></span>

<span data-ttu-id="ffb17-690">Ajustez la sélection actuelle pour inclure le caractère suivant.</span><span class="sxs-lookup"><span data-stu-id="ffb17-690">Adjust the current selection to include the next character.</span></span>

- <span data-ttu-id="ffb17-691">Cmd `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-691">Cmd: `<Shift+RightArrow>`</span></span>
- <span data-ttu-id="ffb17-692">Emacs- `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-692">Emacs: `<Shift+RightArrow>`</span></span>

### <a name="selectforwardword"></a><span data-ttu-id="ffb17-693">SelectForwardWord</span><span class="sxs-lookup"><span data-stu-id="ffb17-693">SelectForwardWord</span></span>

<span data-ttu-id="ffb17-694">Ajustez la sélection actuelle pour inclure le mot suivant à l’aide de ForwardWord.</span><span class="sxs-lookup"><span data-stu-id="ffb17-694">Adjust the current selection to include the next word using ForwardWord.</span></span>

- <span data-ttu-id="ffb17-695">Emacs- `<Alt+F>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-695">Emacs: `<Alt+F>`</span></span>

### <a name="selectline"></a><span data-ttu-id="ffb17-696">SelectLine</span><span class="sxs-lookup"><span data-stu-id="ffb17-696">SelectLine</span></span>

<span data-ttu-id="ffb17-697">Ajustez la sélection actuelle à inclure à partir du curseur jusqu’à la fin de la ligne.</span><span class="sxs-lookup"><span data-stu-id="ffb17-697">Adjust the current selection to include from the cursor to the end of the line.</span></span>

- <span data-ttu-id="ffb17-698">Cmd `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-698">Cmd: `<Shift+End>`</span></span>
- <span data-ttu-id="ffb17-699">Emacs- `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-699">Emacs: `<Shift+End>`</span></span>

### <a name="selectnextword"></a><span data-ttu-id="ffb17-700">SelectNextWord</span><span class="sxs-lookup"><span data-stu-id="ffb17-700">SelectNextWord</span></span>

<span data-ttu-id="ffb17-701">Ajustez la sélection actuelle pour inclure le mot suivant.</span><span class="sxs-lookup"><span data-stu-id="ffb17-701">Adjust the current selection to include the next word.</span></span>

- <span data-ttu-id="ffb17-702">Cmd `<Shift+Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-702">Cmd: `<Shift+Ctrl+RightArrow>`</span></span>

### <a name="selectshellbackwardword"></a><span data-ttu-id="ffb17-703">SelectShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="ffb17-703">SelectShellBackwardWord</span></span>

<span data-ttu-id="ffb17-704">Ajustez la sélection actuelle pour inclure le mot précédent à l’aide de ShellBackwardWord.</span><span class="sxs-lookup"><span data-stu-id="ffb17-704">Adjust the current selection to include the previous word using ShellBackwardWord.</span></span>

- <span data-ttu-id="ffb17-705">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="ffb17-705">Function is unbound.</span></span>

### <a name="selectshellforwardword"></a><span data-ttu-id="ffb17-706">SelectShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="ffb17-706">SelectShellForwardWord</span></span>

<span data-ttu-id="ffb17-707">Ajustez la sélection actuelle pour inclure le mot suivant à l’aide de ShellForwardWord.</span><span class="sxs-lookup"><span data-stu-id="ffb17-707">Adjust the current selection to include the next word using ShellForwardWord.</span></span>

- <span data-ttu-id="ffb17-708">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="ffb17-708">Function is unbound.</span></span>

### <a name="selectshellnextword"></a><span data-ttu-id="ffb17-709">SelectShellNextWord</span><span class="sxs-lookup"><span data-stu-id="ffb17-709">SelectShellNextWord</span></span>

<span data-ttu-id="ffb17-710">Ajustez la sélection actuelle pour inclure le mot suivant à l’aide de ShellNextWord.</span><span class="sxs-lookup"><span data-stu-id="ffb17-710">Adjust the current selection to include the next word using ShellNextWord.</span></span>

- <span data-ttu-id="ffb17-711">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="ffb17-711">Function is unbound.</span></span>

### <a name="setmark"></a><span data-ttu-id="ffb17-712">SetMark</span><span class="sxs-lookup"><span data-stu-id="ffb17-712">SetMark</span></span>

<span data-ttu-id="ffb17-713">Marquez l’emplacement actuel du curseur pour une utilisation dans une commande d’édition suivante.</span><span class="sxs-lookup"><span data-stu-id="ffb17-713">Mark the current location of the cursor for use in a subsequent editing command.</span></span>

- <span data-ttu-id="ffb17-714">Emacs- `<Ctrl+`>\`</span><span class="sxs-lookup"><span data-stu-id="ffb17-714">Emacs: `<Ctrl+`>\`</span></span>

## <a name="search-functions"></a><span data-ttu-id="ffb17-715">Fonctions de recherche</span><span class="sxs-lookup"><span data-stu-id="ffb17-715">Search functions</span></span>

### <a name="charactersearch"></a><span data-ttu-id="ffb17-716">CharacterSearch</span><span class="sxs-lookup"><span data-stu-id="ffb17-716">CharacterSearch</span></span>

<span data-ttu-id="ffb17-717">Lisez un caractère et recherchez l’occurrence suivante de ce caractère.</span><span class="sxs-lookup"><span data-stu-id="ffb17-717">Read a character and search forward for the next occurrence of that character.</span></span>
<span data-ttu-id="ffb17-718">Si un argument est spécifié, effectuez une recherche vers l’avant (ou vers l’arrière si négatif) pour la nième occurrence.</span><span class="sxs-lookup"><span data-stu-id="ffb17-718">If an argument is specified, search forward (or backward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="ffb17-719">Cmd `<F3>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-719">Cmd: `<F3>`</span></span>
- <span data-ttu-id="ffb17-720">Emacs- `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-720">Emacs: `<Ctrl+]>`</span></span>
- <span data-ttu-id="ffb17-721">Mode d’insertion VI : `<F3>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-721">Vi insert mode: `<F3>`</span></span>
- <span data-ttu-id="ffb17-722">Mode de commande VI : `<F3>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-722">Vi command mode: `<F3>`</span></span>

### <a name="charactersearchbackward"></a><span data-ttu-id="ffb17-723">CharacterSearchBackward</span><span class="sxs-lookup"><span data-stu-id="ffb17-723">CharacterSearchBackward</span></span>

<span data-ttu-id="ffb17-724">Lisez un caractère et recherchez l’occurrence suivante de ce caractère.</span><span class="sxs-lookup"><span data-stu-id="ffb17-724">Read a character and search backward for the next occurrence of that character.</span></span> <span data-ttu-id="ffb17-725">Si un argument est spécifié, effectuez une recherche vers l’arrière (ou vers l’avant si négatif) pour la nième occurrence.</span><span class="sxs-lookup"><span data-stu-id="ffb17-725">If an argument is specified, search backward (or forward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="ffb17-726">Cmd `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-726">Cmd: `<Shift+F3>`</span></span>
- <span data-ttu-id="ffb17-727">Emacs- `<Ctrl+Alt+]>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-727">Emacs: `<Ctrl+Alt+]>`</span></span>
- <span data-ttu-id="ffb17-728">Mode d’insertion VI : `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-728">Vi insert mode: `<Shift+F3>`</span></span>
- <span data-ttu-id="ffb17-729">Mode de commande VI : `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-729">Vi command mode: `<Shift+F3>`</span></span>

### <a name="repeatlastcharsearch"></a><span data-ttu-id="ffb17-730">RepeatLastCharSearch</span><span class="sxs-lookup"><span data-stu-id="ffb17-730">RepeatLastCharSearch</span></span>

<span data-ttu-id="ffb17-731">Répète la dernière recherche de caractères enregistrée.</span><span class="sxs-lookup"><span data-stu-id="ffb17-731">Repeat the last recorded character search.</span></span>

- <span data-ttu-id="ffb17-732">Mode de commande VI : `<;>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-732">Vi command mode: `<;>`</span></span>

### <a name="repeatlastcharsearchbackwards"></a><span data-ttu-id="ffb17-733">RepeatLastCharSearchBackwards</span><span class="sxs-lookup"><span data-stu-id="ffb17-733">RepeatLastCharSearchBackwards</span></span>

<span data-ttu-id="ffb17-734">Répète la dernière recherche de caractères enregistrée, mais dans la direction opposée.</span><span class="sxs-lookup"><span data-stu-id="ffb17-734">Repeat the last recorded character search, but in the opposite direction.</span></span>

- <span data-ttu-id="ffb17-735">Mode de commande VI : `<,>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-735">Vi command mode: `<,>`</span></span>

### <a name="repeatsearch"></a><span data-ttu-id="ffb17-736">RepeatSearch</span><span class="sxs-lookup"><span data-stu-id="ffb17-736">RepeatSearch</span></span>

<span data-ttu-id="ffb17-737">Répétez la dernière recherche dans la même direction que précédemment.</span><span class="sxs-lookup"><span data-stu-id="ffb17-737">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="ffb17-738">Mode de commande VI : `<n>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-738">Vi command mode: `<n>`</span></span>

### <a name="repeatsearchbackward"></a><span data-ttu-id="ffb17-739">RepeatSearchBackward</span><span class="sxs-lookup"><span data-stu-id="ffb17-739">RepeatSearchBackward</span></span>

<span data-ttu-id="ffb17-740">Répétez la dernière recherche dans la même direction que précédemment.</span><span class="sxs-lookup"><span data-stu-id="ffb17-740">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="ffb17-741">Mode de commande VI : `<N>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-741">Vi command mode: `<N>`</span></span>

### <a name="searchchar"></a><span data-ttu-id="ffb17-742">SearchChar</span><span class="sxs-lookup"><span data-stu-id="ffb17-742">SearchChar</span></span>

<span data-ttu-id="ffb17-743">Lisez le caractère suivant, puis recherchez-le, à l’avenir, puis annulez un caractère.</span><span class="sxs-lookup"><span data-stu-id="ffb17-743">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="ffb17-744">Il s’agit de la fonctionnalité’t'.</span><span class="sxs-lookup"><span data-stu-id="ffb17-744">This is for 't' functionality.</span></span>

- <span data-ttu-id="ffb17-745">Mode de commande VI : `<f>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-745">Vi command mode: `<f>`</span></span>

### <a name="searchcharbackward"></a><span data-ttu-id="ffb17-746">SearchCharBackward</span><span class="sxs-lookup"><span data-stu-id="ffb17-746">SearchCharBackward</span></span>

<span data-ttu-id="ffb17-747">Lisez le caractère suivant, puis recherchez-le, en accédant à l’arrière, puis en annulant un caractère.</span><span class="sxs-lookup"><span data-stu-id="ffb17-747">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="ffb17-748">Il s’agit de la fonctionnalité’t'.</span><span class="sxs-lookup"><span data-stu-id="ffb17-748">This is for 'T' functionality.</span></span>

- <span data-ttu-id="ffb17-749">Mode de commande VI : `<F>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-749">Vi command mode: `<F>`</span></span>

### <a name="searchcharbackwardwithbackoff"></a><span data-ttu-id="ffb17-750">SearchCharBackwardWithBackoff</span><span class="sxs-lookup"><span data-stu-id="ffb17-750">SearchCharBackwardWithBackoff</span></span>

<span data-ttu-id="ffb17-751">Lisez le caractère suivant, puis recherchez-le, en accédant à l’arrière, puis en annulant un caractère.</span><span class="sxs-lookup"><span data-stu-id="ffb17-751">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="ffb17-752">Il s’agit de la fonctionnalité’t'.</span><span class="sxs-lookup"><span data-stu-id="ffb17-752">This is for 'T' functionality.</span></span>

- <span data-ttu-id="ffb17-753">Mode de commande VI : `<T>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-753">Vi command mode: `<T>`</span></span>

### <a name="searchcharwithbackoff"></a><span data-ttu-id="ffb17-754">SearchCharWithBackoff</span><span class="sxs-lookup"><span data-stu-id="ffb17-754">SearchCharWithBackoff</span></span>

<span data-ttu-id="ffb17-755">Lisez le caractère suivant, puis recherchez-le, à l’avenir, puis annulez un caractère.</span><span class="sxs-lookup"><span data-stu-id="ffb17-755">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="ffb17-756">Il s’agit de la fonctionnalité’t'.</span><span class="sxs-lookup"><span data-stu-id="ffb17-756">This is for 't' functionality.</span></span>

- <span data-ttu-id="ffb17-757">Mode de commande VI : `<t>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-757">Vi command mode: `<t>`</span></span>

### <a name="searchforward"></a><span data-ttu-id="ffb17-758">SearchForward</span><span class="sxs-lookup"><span data-stu-id="ffb17-758">SearchForward</span></span>

<span data-ttu-id="ffb17-759">Demande une chaîne de recherche et lance la recherche sur AcceptLine.</span><span class="sxs-lookup"><span data-stu-id="ffb17-759">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="ffb17-760">Mode d’insertion VI : `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-760">Vi insert mode: `<Ctrl+s>`</span></span>
- <span data-ttu-id="ffb17-761">Mode de commande VI : `<?>` , `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="ffb17-761">Vi command mode: `<?>`, `<Ctrl+s>`</span></span>

## <a name="custom-key-bindings"></a><span data-ttu-id="ffb17-762">Combinaisons de touches personnalisées</span><span class="sxs-lookup"><span data-stu-id="ffb17-762">Custom Key Bindings</span></span>

<span data-ttu-id="ffb17-763">PSReadLine prend en charge les combinaisons de touches personnalisées à l’aide de l’applet de commande `Set-PSReadLineKeyHandler` .</span><span class="sxs-lookup"><span data-stu-id="ffb17-763">PSReadLine supports custom key bindings using the cmdlet `Set-PSReadLineKeyHandler`.</span></span> <span data-ttu-id="ffb17-764">La plupart des combinaisons de touches personnalisées appellent l’une des fonctions ci-dessus, par exemple</span><span class="sxs-lookup"><span data-stu-id="ffb17-764">Most custom key bindings call one of the above functions, for example</span></span>

```powershell
Set-PSReadLineKeyHandler -Key UpArrow -Function HistorySearchBackward
```

<span data-ttu-id="ffb17-765">Vous pouvez lier un ScriptBlock à une clé.</span><span class="sxs-lookup"><span data-stu-id="ffb17-765">You can bind a ScriptBlock to a key.</span></span> <span data-ttu-id="ffb17-766">Le ScriptBlock peut faire à peu près tout ce que vous voulez.</span><span class="sxs-lookup"><span data-stu-id="ffb17-766">The ScriptBlock can do pretty much anything you want.</span></span> <span data-ttu-id="ffb17-767">Voici quelques exemples utiles :</span><span class="sxs-lookup"><span data-stu-id="ffb17-767">Some useful examples include</span></span>

- <span data-ttu-id="ffb17-768">modifier la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="ffb17-768">edit the command line</span></span>
- <span data-ttu-id="ffb17-769">ouverture d’une nouvelle fenêtre (par exemple, aide)</span><span class="sxs-lookup"><span data-stu-id="ffb17-769">opening a new window (e.g. help)</span></span>
- <span data-ttu-id="ffb17-770">modifier les répertoires sans modifier la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="ffb17-770">change directories without changing the command line</span></span>

<span data-ttu-id="ffb17-771">Le ScriptBlock reçoit deux arguments :</span><span class="sxs-lookup"><span data-stu-id="ffb17-771">The ScriptBlock receives two arguments:</span></span>

- <span data-ttu-id="ffb17-772">`$key` -Objet **[ConsoleKeyInfo]** qui est la clé qui a déclenché la liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="ffb17-772">`$key` - A **[ConsoleKeyInfo]** object that is the key that triggered the custom binding.</span></span> <span data-ttu-id="ffb17-773">Si vous liez le même ScriptBlock à plusieurs clés et que vous devez effectuer des actions différentes en fonction de la clé, vous pouvez vérifier $key.</span><span class="sxs-lookup"><span data-stu-id="ffb17-773">If you bind the same ScriptBlock to multiple keys and need to perform different actions depending on the key, you can check $key.</span></span> <span data-ttu-id="ffb17-774">De nombreuses liaisons personnalisées ignorent cet argument.</span><span class="sxs-lookup"><span data-stu-id="ffb17-774">Many custom bindings ignore this argument.</span></span>

- <span data-ttu-id="ffb17-775">`$arg` : Argument arbitraire.</span><span class="sxs-lookup"><span data-stu-id="ffb17-775">`$arg` - An arbitrary argument.</span></span> <span data-ttu-id="ffb17-776">Le plus souvent, il s’agit d’un argument entier que l’utilisateur passe à partir des combinaisons de touches DigitArgument.</span><span class="sxs-lookup"><span data-stu-id="ffb17-776">Most often, this would be an integer argument that the user passes from the key bindings DigitArgument.</span></span> <span data-ttu-id="ffb17-777">Si votre liaison n’accepte pas d’arguments, il est raisonnable d’ignorer cet argument.</span><span class="sxs-lookup"><span data-stu-id="ffb17-777">If your binding doesn't accept arguments, it's reasonable to ignore this argument.</span></span>

<span data-ttu-id="ffb17-778">Jetons un coup d’œil à un exemple qui ajoute une ligne de commande à l’historique sans l’exécuter.</span><span class="sxs-lookup"><span data-stu-id="ffb17-778">Let's take a look at an example that adds a command line to history without executing it.</span></span> <span data-ttu-id="ffb17-779">Cela est utile lorsque vous vous rendez compte que vous avez oublié d’effectuer une opération, mais que vous ne voulez pas entrer à nouveau la ligne de commande que vous avez déjà entrée.</span><span class="sxs-lookup"><span data-stu-id="ffb17-779">This is useful when you realize you forgot to do something, but don't want to re-enter the command line you've already entered.</span></span>

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

<span data-ttu-id="ffb17-780">Vous pouvez voir beaucoup plus d’exemples dans le fichier `SamplePSReadLineProfile.ps1` qui est installé dans le dossier du module PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="ffb17-780">You can see many more examples in the file `SamplePSReadLineProfile.ps1` which is installed in the PSReadLine module folder.</span></span>

<span data-ttu-id="ffb17-781">La plupart des combinaisons de touches utilisent des fonctions d’assistance pour la modification de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="ffb17-781">Most key bindings use some helper functions for editing the command line.</span></span>
<span data-ttu-id="ffb17-782">Ces API sont documentées dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="ffb17-782">Those APIs are documented in the next section.</span></span>

## <a name="custom-key-binding-support-apis"></a><span data-ttu-id="ffb17-783">API de prise en charge de la liaison de clé personnalisée</span><span class="sxs-lookup"><span data-stu-id="ffb17-783">Custom Key Binding Support APIs</span></span>

<span data-ttu-id="ffb17-784">Les fonctions suivantes sont publiques dans Microsoft. PowerShell. PSConsoleReadLine, mais ne peuvent pas être directement liées à une clé.</span><span class="sxs-lookup"><span data-stu-id="ffb17-784">The following functions are public in Microsoft.PowerShell.PSConsoleReadLine, but cannot be directly bound to a key.</span></span> <span data-ttu-id="ffb17-785">La plupart sont utiles dans les combinaisons de touches personnalisées.</span><span class="sxs-lookup"><span data-stu-id="ffb17-785">Most are useful in custom key bindings.</span></span>

```csharp
void AddToHistory(string command)
```

<span data-ttu-id="ffb17-786">Ajoutez une ligne de commande à l’historique sans l’exécuter.</span><span class="sxs-lookup"><span data-stu-id="ffb17-786">Add a command line to history without executing it.</span></span>

```csharp
void ClearKillRing()
```

<span data-ttu-id="ffb17-787">Effacez le point d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="ffb17-787">Clear the kill-ring.</span></span>  <span data-ttu-id="ffb17-788">Cela est principalement utilisé pour les tests.</span><span class="sxs-lookup"><span data-stu-id="ffb17-788">This is mostly used for testing.</span></span>

```csharp
void Delete(int start, int length)
```

<span data-ttu-id="ffb17-789">Supprimer les caractères de longueur du début.</span><span class="sxs-lookup"><span data-stu-id="ffb17-789">Delete length characters from start.</span></span>  <span data-ttu-id="ffb17-790">Cette opération prend en charge les opérations d’annulation et de rétablissement.</span><span class="sxs-lookup"><span data-stu-id="ffb17-790">This operation supports undo/redo.</span></span>

```csharp
void Ding()
```

<span data-ttu-id="ffb17-791">Effectuez l’action Ding en fonction des préférences de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="ffb17-791">Perform the Ding action based on the users preference.</span></span>

```csharp
void GetBufferState([ref] string input, [ref] int cursor)
void GetBufferState([ref] Ast ast, [ref] Token[] tokens,
  [ref] ParseError[] parseErrors, [ref] int cursor)
```

<span data-ttu-id="ffb17-792">Ces deux fonctions récupèrent des informations utiles sur l’état actuel de la mémoire tampon d’entrée.</span><span class="sxs-lookup"><span data-stu-id="ffb17-792">These two functions retrieve useful information about the current state of the input buffer.</span></span>  <span data-ttu-id="ffb17-793">La première est plus couramment utilisée dans les cas simples.</span><span class="sxs-lookup"><span data-stu-id="ffb17-793">The first is more commonly used for simple cases.</span></span>  <span data-ttu-id="ffb17-794">Le second est utilisé si votre liaison fait une opération plus avancée avec l’AST.</span><span class="sxs-lookup"><span data-stu-id="ffb17-794">The second is used if your binding is doing something more advanced with the Ast.</span></span>

```csharp
IEnumerable[Microsoft.PowerShell.KeyHandler]
  GetKeyHandlers(bool includeBound, bool includeUnbound)

```

<span data-ttu-id="ffb17-795">Cette fonction est utilisée par Get-PSReadLineKeyHandler et n’est probablement pas utile dans une combinaison de touches personnalisée.</span><span class="sxs-lookup"><span data-stu-id="ffb17-795">This function is used by Get-PSReadLineKeyHandler and probably isn't useful in a custom key binding.</span></span>

```csharp
Microsoft.PowerShell.PSConsoleReadLineOptions GetOptions()
```

<span data-ttu-id="ffb17-796">Cette fonction est utilisée par Get-PSReadLineOption et n’est probablement pas trop utile dans une liaison de clé personnalisée.</span><span class="sxs-lookup"><span data-stu-id="ffb17-796">This function is used by Get-PSReadLineOption and probably isn't too useful in a custom key binding.</span></span>

```csharp
void GetSelectionState([ref] int start, [ref] int length)
```

<span data-ttu-id="ffb17-797">Si aucune sélection n’est effectuée sur la ligne de commande,-1 est retourné à la fois en début et en longueur.</span><span class="sxs-lookup"><span data-stu-id="ffb17-797">If there is no selection on the command line, -1 will be returned in both start and length.</span></span> <span data-ttu-id="ffb17-798">Si une sélection est effectuée sur la ligne de commande, le début et la longueur de la sélection sont retournés.</span><span class="sxs-lookup"><span data-stu-id="ffb17-798">If there is a selection on the command line, the start and length of the selection are returned.</span></span>

```csharp
void Insert(char c)
void Insert(string s)
```

<span data-ttu-id="ffb17-799">Insérez un caractère ou une chaîne au niveau du curseur.</span><span class="sxs-lookup"><span data-stu-id="ffb17-799">Insert a character or string at the cursor.</span></span>  <span data-ttu-id="ffb17-800">Cette opération prend en charge les opérations d’annulation et de rétablissement.</span><span class="sxs-lookup"><span data-stu-id="ffb17-800">This operation supports undo/redo.</span></span>

```csharp
string ReadLine(runspace remoteRunspace,
  System.Management.Automation.EngineIntrinsics engineIntrinsics)
```

<span data-ttu-id="ffb17-801">Il s’agit du point d’entrée principal de PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="ffb17-801">This is the main entry point to PSReadLine.</span></span> <span data-ttu-id="ffb17-802">Comme il ne prend pas en charge la récursivité, il n’est pas utile dans une liaison de clé personnalisée.</span><span class="sxs-lookup"><span data-stu-id="ffb17-802">It does not support recursion, so is not useful in a custom key binding.</span></span>

```csharp
void RemoveKeyHandler(string[] key)
```

<span data-ttu-id="ffb17-803">Cette fonction est utilisée par Remove-PSReadLineKeyHandler et n’est probablement pas trop utile dans une liaison de clé personnalisée.</span><span class="sxs-lookup"><span data-stu-id="ffb17-803">This function is used by Remove-PSReadLineKeyHandler and probably isn't too useful in a custom key binding.</span></span>

```csharp
void Replace(int start, int length, string replacement)
```

<span data-ttu-id="ffb17-804">Remplacez une partie de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="ffb17-804">Replace some of the input.</span></span> <span data-ttu-id="ffb17-805">Cette opération prend en charge les opérations d’annulation et de rétablissement.</span><span class="sxs-lookup"><span data-stu-id="ffb17-805">This operation supports undo/redo.</span></span> <span data-ttu-id="ffb17-806">C’est préférable à Delete, suivi de Insert, car il est traité comme une action unique pour Undo.</span><span class="sxs-lookup"><span data-stu-id="ffb17-806">This is preferred over Delete followed by Insert because it is treated as a single action for undo.</span></span>

```csharp
void SetCursorPosition(int cursor)
```

<span data-ttu-id="ffb17-807">Déplacer le curseur vers l’offset donné.</span><span class="sxs-lookup"><span data-stu-id="ffb17-807">Move the cursor to the given offset.</span></span> <span data-ttu-id="ffb17-808">Le déplacement du curseur n’est pas suivi pour l’annulation.</span><span class="sxs-lookup"><span data-stu-id="ffb17-808">Cursor movement is not tracked for undo.</span></span>

```csharp
void SetOptions(Microsoft.PowerShell.SetPSReadLineOption options)
```

<span data-ttu-id="ffb17-809">Cette fonction est une méthode d’assistance utilisée par l’applet de commande Set-PSReadLineOption, mais peut être utile pour une combinaison de touches personnalisée qui souhaite modifier temporairement un paramètre.</span><span class="sxs-lookup"><span data-stu-id="ffb17-809">This function is a helper method used by the cmdlet Set-PSReadLineOption, but might be useful to a custom key binding that wants to temporarily change a setting.</span></span>

```csharp
bool TryGetArgAsInt(System.Object arg, [ref] int numericArg,
  int defaultNumericArg)
```

<span data-ttu-id="ffb17-810">Cette méthode d’assistance est utilisée pour les liaisons personnalisées qui respectent DigitArgument.</span><span class="sxs-lookup"><span data-stu-id="ffb17-810">This helper method is used for custom bindings that honor DigitArgument.</span></span> <span data-ttu-id="ffb17-811">Un appel classique ressemble à ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="ffb17-811">A typical call looks like</span></span>

```powershell
[int]$numericArg = 0
[Microsoft.PowerShell.PSConsoleReadLine]::TryGetArgAsInt($arg,
  [ref]$numericArg, 1)
```

## <a name="note"></a><span data-ttu-id="ffb17-812">REMARQUE</span><span class="sxs-lookup"><span data-stu-id="ffb17-812">NOTE</span></span>

### <a name="powershell-compatibility"></a><span data-ttu-id="ffb17-813">COMPATIBILITÉ AVEC POWERSHELL</span><span class="sxs-lookup"><span data-stu-id="ffb17-813">POWERSHELL COMPATIBILITY</span></span>

<span data-ttu-id="ffb17-814">PSReadLine nécessite PowerShell 3,0, ou une version plus récente, et l’hôte de la console.</span><span class="sxs-lookup"><span data-stu-id="ffb17-814">PSReadLine requires PowerShell 3.0, or newer, and the console host.</span></span> <span data-ttu-id="ffb17-815">Il ne fonctionne pas dans PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="ffb17-815">It does not work in PowerShell ISE.</span></span> <span data-ttu-id="ffb17-816">Elle fonctionne dans la console de Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="ffb17-816">It does work in the console of Visual Studio Code.</span></span>

### <a name="command-history"></a><span data-ttu-id="ffb17-817">HISTORIQUE DES COMMANDES</span><span class="sxs-lookup"><span data-stu-id="ffb17-817">COMMAND HISTORY</span></span>

<span data-ttu-id="ffb17-818">PSReadLine gère un fichier d’historique contenant toutes les commandes et données que vous avez entrées à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="ffb17-818">PSReadLine maintains a history file containing all the commands and data you have entered from the command line.</span></span> <span data-ttu-id="ffb17-819">Cela peut contenir des données sensibles, y compris des mots de passe.</span><span class="sxs-lookup"><span data-stu-id="ffb17-819">This may contain sensitive data including passwords.</span></span> <span data-ttu-id="ffb17-820">Par exemple, si vous utilisez l’applet de commande, `ConvertTo-SecureString` le mot de passe est enregistré dans le fichier d’historique sous forme de texte brut.</span><span class="sxs-lookup"><span data-stu-id="ffb17-820">For example, if you use the `ConvertTo-SecureString` cmdlet the password is logged in the history file as plain text.</span></span> <span data-ttu-id="ffb17-821">Les fichiers d’historique sont un fichier nommé `$($host.Name)_history.txt` .</span><span class="sxs-lookup"><span data-stu-id="ffb17-821">The history files is a file named `$($host.Name)_history.txt`.</span></span> <span data-ttu-id="ffb17-822">Sur les systèmes Windows, le fichier d’historique est stocké à l’adresse `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine` .</span><span class="sxs-lookup"><span data-stu-id="ffb17-822">On Windows systems the history file is stored at `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine`.</span></span>

### <a name="feedback--contributing-to-psreadline"></a><span data-ttu-id="ffb17-823">Commentaires & contribution à PSReadLine</span><span class="sxs-lookup"><span data-stu-id="ffb17-823">FEEDBACK & CONTRIBUTING TO PSReadLine</span></span>

[<span data-ttu-id="ffb17-824">PSReadLine sur GitHub</span><span class="sxs-lookup"><span data-stu-id="ffb17-824">PSReadLine on GitHub</span></span>](https://github.com/PowerShell/PSReadLine)

<span data-ttu-id="ffb17-825">N’hésitez pas à envoyer une demande de tirage ou à envoyer des commentaires sur la page GitHub.</span><span class="sxs-lookup"><span data-stu-id="ffb17-825">Feel free to submit a pull request or submit feedback on the GitHub page.</span></span>

## <a name="see-also"></a><span data-ttu-id="ffb17-826">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="ffb17-826">SEE ALSO</span></span>

<span data-ttu-id="ffb17-827">PSReadLine est fortement influencé par la bibliothèque GNU [ReadLine](https://tiswww.case.edu/php/chet/readline/rltop.html) .</span><span class="sxs-lookup"><span data-stu-id="ffb17-827">PSReadLine is heavily influenced by the GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) library.</span></span>
