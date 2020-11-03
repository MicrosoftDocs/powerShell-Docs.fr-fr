---
description: PSReadLine fournit une expérience d’édition de ligne de commande améliorée dans la console PowerShell.
keywords: powershell
Locale: en-US
ms.date: 02/10/2020
online version: https://docs.microsoft.com/powershell/module/psreadline/about/about_psreadline?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: À propos de PSReadLine
ms.openlocfilehash: 1188b8dc0b4099a7c1dcc472e3b02c2d4fa908bc
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206690"
---
# <a name="psreadline"></a><span data-ttu-id="2ce29-104">PSReadLine</span><span class="sxs-lookup"><span data-stu-id="2ce29-104">PSReadLine</span></span>

## <a name="about_psreadline"></a><span data-ttu-id="2ce29-105">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="2ce29-105">about_PSReadLine</span></span>

## <a name="short-description"></a><span data-ttu-id="2ce29-106">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="2ce29-106">SHORT DESCRIPTION</span></span>

<span data-ttu-id="2ce29-107">PSReadLine fournit une expérience d’édition de ligne de commande améliorée dans la console PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2ce29-107">PSReadLine provides an improved command-line editing experience in the PowerShell console.</span></span>

## <a name="long-description"></a><span data-ttu-id="2ce29-108">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="2ce29-108">LONG DESCRIPTION</span></span>

<span data-ttu-id="2ce29-109">PSReadLine 2,0 fournit une expérience d’édition de ligne de commande puissante pour la console PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2ce29-109">PSReadLine 2.0 provides a powerful command-line editing experience for the PowerShell console.</span></span> <span data-ttu-id="2ce29-110">Elle offre les possibilités suivantes :</span><span class="sxs-lookup"><span data-stu-id="2ce29-110">It provides:</span></span>

- <span data-ttu-id="2ce29-111">Coloration de la syntaxe de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="2ce29-111">Syntax coloring of the command line</span></span>
- <span data-ttu-id="2ce29-112">Indication visuelle des erreurs de syntaxe</span><span class="sxs-lookup"><span data-stu-id="2ce29-112">A visual indication of syntax errors</span></span>
- <span data-ttu-id="2ce29-113">Une meilleure expérience multi-ligne (modification et historique)</span><span class="sxs-lookup"><span data-stu-id="2ce29-113">A better multi-line experience (both editing and history)</span></span>
- <span data-ttu-id="2ce29-114">Combinaisons de touches personnalisables</span><span class="sxs-lookup"><span data-stu-id="2ce29-114">Customizable key bindings</span></span>
- <span data-ttu-id="2ce29-115">Modes cmd et Emacs</span><span class="sxs-lookup"><span data-stu-id="2ce29-115">Cmd and Emacs modes</span></span>
- <span data-ttu-id="2ce29-116">Nombreuses options de configuration</span><span class="sxs-lookup"><span data-stu-id="2ce29-116">Many configuration options</span></span>
- <span data-ttu-id="2ce29-117">Saisie semi-automatique du style bash (facultatif en mode cmd, par défaut en mode emacs)</span><span class="sxs-lookup"><span data-stu-id="2ce29-117">Bash style completion (optional in Cmd mode, default in Emacs mode)</span></span>
- <span data-ttu-id="2ce29-118">Emacs-Yank/Kill-Ring</span><span class="sxs-lookup"><span data-stu-id="2ce29-118">Emacs yank/kill-ring</span></span>
- <span data-ttu-id="2ce29-119">Mouvement « mot » basé sur un jeton PowerShell et Kill</span><span class="sxs-lookup"><span data-stu-id="2ce29-119">PowerShell token based "word" movement and kill</span></span>

<span data-ttu-id="2ce29-120">Les fonctions suivantes sont disponibles dans la classe **[Microsoft. PowerShell. PSConsoleReadLine]** .</span><span class="sxs-lookup"><span data-stu-id="2ce29-120">The following functions are available in the class **[Microsoft.PowerShell.PSConsoleReadLine]** .</span></span>

> [!NOTE]
> <span data-ttu-id="2ce29-121">À compter de PowerShell 7,0, PowerShell ignore le chargement automatique de PSReadLine sur Windows si un programme de lecture d’écran est détecté.</span><span class="sxs-lookup"><span data-stu-id="2ce29-121">Beginning with PowerShell 7.0, PowerShell skips auto-loading PSReadLine on Windows if a screen reader program is detected.</span></span> <span data-ttu-id="2ce29-122">Actuellement, PSReadLine ne fonctionne pas correctement avec les lecteurs d’écran.</span><span class="sxs-lookup"><span data-stu-id="2ce29-122">Currently, PSReadLine doesn't work well with the screen readers.</span></span> <span data-ttu-id="2ce29-123">Le rendu et la mise en forme par défaut de PowerShell 7,0 sur Windows fonctionnent correctement.</span><span class="sxs-lookup"><span data-stu-id="2ce29-123">The default rendering and formatting of PowerShell 7.0 on Windows works properly.</span></span> <span data-ttu-id="2ce29-124">Vous pouvez charger le module manuellement, si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="2ce29-124">You can manually load the module if necessary.</span></span>

## <a name="basic-editing-functions"></a><span data-ttu-id="2ce29-125">Fonctions d’édition de base</span><span class="sxs-lookup"><span data-stu-id="2ce29-125">Basic editing functions</span></span>

### <a name="abort"></a><span data-ttu-id="2ce29-126">Abandon</span><span class="sxs-lookup"><span data-stu-id="2ce29-126">Abort</span></span>

<span data-ttu-id="2ce29-127">Annuler l’action en cours, par exemple, recherche de l’historique incrémentiel.</span><span class="sxs-lookup"><span data-stu-id="2ce29-127">Abort current action, e.g. incremental history search.</span></span>

- <span data-ttu-id="2ce29-128">Emacs- `<Ctrl+g>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-128">Emacs: `<Ctrl+g>`</span></span>

### <a name="acceptandgetnext"></a><span data-ttu-id="2ce29-129">AcceptAndGetNext</span><span class="sxs-lookup"><span data-stu-id="2ce29-129">AcceptAndGetNext</span></span>

<span data-ttu-id="2ce29-130">Tentative d’exécution de l’entrée en cours.</span><span class="sxs-lookup"><span data-stu-id="2ce29-130">Attempt to execute the current input.</span></span> <span data-ttu-id="2ce29-131">Si elle peut être exécutée (par exemple, AcceptLine), rappelez l’élément suivant de l’historique la prochaine fois que ReadLine est appelé.</span><span class="sxs-lookup"><span data-stu-id="2ce29-131">If it can be executed (like AcceptLine), then recall the next item from history the next time ReadLine is called.</span></span>

- <span data-ttu-id="2ce29-132">Emacs- `<Ctrl+o>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-132">Emacs: `<Ctrl+o>`</span></span>

### <a name="acceptline"></a><span data-ttu-id="2ce29-133">AcceptLine</span><span class="sxs-lookup"><span data-stu-id="2ce29-133">AcceptLine</span></span>

<span data-ttu-id="2ce29-134">Tentative d’exécution de l’entrée en cours.</span><span class="sxs-lookup"><span data-stu-id="2ce29-134">Attempt to execute the current input.</span></span> <span data-ttu-id="2ce29-135">Si l’entrée actuelle est incomplète (par exemple, il manque une parenthèse fermante, un crochet ou un guillemet, l’invite de continuation est affichée sur la ligne suivante et PSReadLine attend que les clés modifient l’entrée actuelle.</span><span class="sxs-lookup"><span data-stu-id="2ce29-135">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="2ce29-136">Cmd `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-136">Cmd: `<Enter>`</span></span>
- <span data-ttu-id="2ce29-137">Emacs- `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-137">Emacs: `<Enter>`</span></span>
- <span data-ttu-id="2ce29-138">Mode d’insertion VI : `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-138">Vi insert mode: `<Enter>`</span></span>

### <a name="addline"></a><span data-ttu-id="2ce29-139">AddLine</span><span class="sxs-lookup"><span data-stu-id="2ce29-139">AddLine</span></span>

<span data-ttu-id="2ce29-140">L’invite de continuation est affichée sur la ligne suivante et PSReadLine attend que les clés modifient l’entrée actuelle.</span><span class="sxs-lookup"><span data-stu-id="2ce29-140">The continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span> <span data-ttu-id="2ce29-141">Cela est utile pour entrer une entrée multiligne sous la forme d’une commande unique, même lorsqu’une seule ligne est complète en entrée.</span><span class="sxs-lookup"><span data-stu-id="2ce29-141">This is useful to enter multi-line input as a single command even when a single line is complete input by itself.</span></span>

- <span data-ttu-id="2ce29-142">Cmd `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-142">Cmd: `<Shift+Enter>`</span></span>
- <span data-ttu-id="2ce29-143">Emacs- `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-143">Emacs: `<Shift+Enter>`</span></span>
- <span data-ttu-id="2ce29-144">Mode d’insertion VI : `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-144">Vi insert mode: `<Shift+Enter>`</span></span>
- <span data-ttu-id="2ce29-145">Mode de commande VI : `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-145">Vi command mode: `<Shift+Enter>`</span></span>

### <a name="backwarddeletechar"></a><span data-ttu-id="2ce29-146">BackwardDeleteChar</span><span class="sxs-lookup"><span data-stu-id="2ce29-146">BackwardDeleteChar</span></span>

<span data-ttu-id="2ce29-147">Supprimez le caractère avant le curseur.</span><span class="sxs-lookup"><span data-stu-id="2ce29-147">Delete the character before the cursor.</span></span>

- <span data-ttu-id="2ce29-148">Cmd : `<Backspace>` , `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-148">Cmd: `<Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="2ce29-149">Emacs : `<Backspace>` , `<Ctrl+Backspace>` , `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-149">Emacs: `<Backspace>`, `<Ctrl+Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="2ce29-150">Mode d’insertion VI : `<Backspace>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-150">Vi insert mode: `<Backspace>`</span></span>
- <span data-ttu-id="2ce29-151">Mode de commande VI : `<X>` , `<d,h>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-151">Vi command mode: `<X>`, `<d,h>`</span></span>

### <a name="backwarddeleteline"></a><span data-ttu-id="2ce29-152">BackwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="2ce29-152">BackwardDeleteLine</span></span>

<span data-ttu-id="2ce29-153">Comme BackwardKillLine-supprime le texte du point jusqu’au début de la ligne, mais ne place pas le texte supprimé dans l’anneau d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="2ce29-153">Like BackwardKillLine - deletes text from the point to the start of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="2ce29-154">Cmd `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-154">Cmd: `<Ctrl+Home>`</span></span>
- <span data-ttu-id="2ce29-155">Mode d’insertion VI : `<Ctrl+u>` , `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-155">Vi insert mode: `<Ctrl+u>`, `<Ctrl+Home>`</span></span>
- <span data-ttu-id="2ce29-156">Mode de commande VI : `<Ctrl+u>` , `<Ctrl+Home>` , `<d,0>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-156">Vi command mode: `<Ctrl+u>`, `<Ctrl+Home>`, `<d,0>`</span></span>

### <a name="backwarddeleteword"></a><span data-ttu-id="2ce29-157">BackwardDeleteWord</span><span class="sxs-lookup"><span data-stu-id="2ce29-157">BackwardDeleteWord</span></span>

<span data-ttu-id="2ce29-158">Supprime le mot précédent.</span><span class="sxs-lookup"><span data-stu-id="2ce29-158">Deletes the previous word.</span></span>

- <span data-ttu-id="2ce29-159">Mode de commande VI : `<Ctrl+w>` , `<d,b>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-159">Vi command mode: `<Ctrl+w>`, `<d,b>`</span></span>

### <a name="backwardkillline"></a><span data-ttu-id="2ce29-160">BackwardKillLine</span><span class="sxs-lookup"><span data-stu-id="2ce29-160">BackwardKillLine</span></span>

<span data-ttu-id="2ce29-161">Effacez l’entrée à partir du début de l’entrée jusqu’au curseur.</span><span class="sxs-lookup"><span data-stu-id="2ce29-161">Clear the input from the start of the input to the cursor.</span></span> <span data-ttu-id="2ce29-162">Le texte effacé est placé dans le Kill-Ring.</span><span class="sxs-lookup"><span data-stu-id="2ce29-162">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="2ce29-163">Emacs- `<Ctrl+u>` , `<Ctrl+x,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-163">Emacs: `<Ctrl+u>`, `<Ctrl+x,Backspace>`</span></span>

### <a name="backwardkillword"></a><span data-ttu-id="2ce29-164">BackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="2ce29-164">BackwardKillWord</span></span>

<span data-ttu-id="2ce29-165">Efface l’entrée du début du mot actuel jusqu’au curseur.</span><span class="sxs-lookup"><span data-stu-id="2ce29-165">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="2ce29-166">Si le curseur se trouve entre des mots, l’entrée est effacée du début du mot précédent au curseur.</span><span class="sxs-lookup"><span data-stu-id="2ce29-166">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="2ce29-167">Le texte effacé est placé dans le Kill-Ring.</span><span class="sxs-lookup"><span data-stu-id="2ce29-167">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="2ce29-168">Cmd : `<Ctrl+Backspace>` , `<Ctrl+w>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-168">Cmd: `<Ctrl+Backspace>`, `<Ctrl+w>`</span></span>
- <span data-ttu-id="2ce29-169">Emacs- `<Alt+Backspace>` , `<Escape,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-169">Emacs: `<Alt+Backspace>`, `<Escape,Backspace>`</span></span>
- <span data-ttu-id="2ce29-170">Mode d’insertion VI : `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-170">Vi insert mode: `<Ctrl+Backspace>`</span></span>
- <span data-ttu-id="2ce29-171">Mode de commande VI : `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-171">Vi command mode: `<Ctrl+Backspace>`</span></span>

### <a name="cancelline"></a><span data-ttu-id="2ce29-172">CancelLine</span><span class="sxs-lookup"><span data-stu-id="2ce29-172">CancelLine</span></span>

<span data-ttu-id="2ce29-173">Annule l’entrée actuelle, en laissant l’entrée à l’écran, mais retourne à l’hôte afin que l’invite soit de nouveau évaluée.</span><span class="sxs-lookup"><span data-stu-id="2ce29-173">Cancel the current input, leaving the input on the screen, but returns back to the host so the prompt is evaluated again.</span></span>

- <span data-ttu-id="2ce29-174">Mode d’insertion VI : `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-174">Vi insert mode: `<Ctrl+c>`</span></span>
- <span data-ttu-id="2ce29-175">Mode de commande VI : `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-175">Vi command mode: `<Ctrl+c>`</span></span>

### <a name="copy"></a><span data-ttu-id="2ce29-176">Copier</span><span class="sxs-lookup"><span data-stu-id="2ce29-176">Copy</span></span>

<span data-ttu-id="2ce29-177">Copier la région sélectionnée dans le presse-papiers du système.</span><span class="sxs-lookup"><span data-stu-id="2ce29-177">Copy selected region to the system clipboard.</span></span> <span data-ttu-id="2ce29-178">Si aucune région n’est sélectionnée, copiez la ligne entière.</span><span class="sxs-lookup"><span data-stu-id="2ce29-178">If no region is selected, copy the whole line.</span></span>

- <span data-ttu-id="2ce29-179">Cmd `<Ctrl+C>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-179">Cmd: `<Ctrl+C>`</span></span>

### <a name="copyorcancelline"></a><span data-ttu-id="2ce29-180">CopyOrCancelLine</span><span class="sxs-lookup"><span data-stu-id="2ce29-180">CopyOrCancelLine</span></span>

<span data-ttu-id="2ce29-181">Si le texte est sélectionné, copiez-le dans le presse-papiers, sinon, annulez la ligne.</span><span class="sxs-lookup"><span data-stu-id="2ce29-181">If text is selected, copy to the clipboard, otherwise cancel the line.</span></span>

- <span data-ttu-id="2ce29-182">Cmd `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-182">Cmd: `<Ctrl+c>`</span></span>
- <span data-ttu-id="2ce29-183">Emacs- `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-183">Emacs: `<Ctrl+c>`</span></span>

### <a name="cut"></a><span data-ttu-id="2ce29-184">Couper</span><span class="sxs-lookup"><span data-stu-id="2ce29-184">Cut</span></span>

<span data-ttu-id="2ce29-185">Supprimer la zone sélectionnée en plaçant le texte supprimé dans le presse-papiers du système.</span><span class="sxs-lookup"><span data-stu-id="2ce29-185">Delete selected region placing deleted text in the system clipboard.</span></span>

- <span data-ttu-id="2ce29-186">Cmd `<Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-186">Cmd: `<Ctrl+x>`</span></span>

### <a name="deletechar"></a><span data-ttu-id="2ce29-187">DeleteChar</span><span class="sxs-lookup"><span data-stu-id="2ce29-187">DeleteChar</span></span>

<span data-ttu-id="2ce29-188">Supprimez le caractère sous le curseur.</span><span class="sxs-lookup"><span data-stu-id="2ce29-188">Delete the character under the cursor.</span></span>

- <span data-ttu-id="2ce29-189">Cmd `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-189">Cmd: `<Delete>`</span></span>
- <span data-ttu-id="2ce29-190">Emacs- `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-190">Emacs: `<Delete>`</span></span>
- <span data-ttu-id="2ce29-191">Mode d’insertion VI : `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-191">Vi insert mode: `<Delete>`</span></span>
- <span data-ttu-id="2ce29-192">Mode de commande VI : `<Delete>` , `<x>` , `<d,l>` , `<d,Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-192">Vi command mode: `<Delete>`, `<x>`, `<d,l>`, `<d,Spacebar>`</span></span>

### <a name="deletecharorexit"></a><span data-ttu-id="2ce29-193">DeleteCharOrExit</span><span class="sxs-lookup"><span data-stu-id="2ce29-193">DeleteCharOrExit</span></span>

<span data-ttu-id="2ce29-194">Supprimez le caractère sous le curseur, ou si la ligne est vide, quittez le processus.</span><span class="sxs-lookup"><span data-stu-id="2ce29-194">Delete the character under the cursor, or if the line is empty, exit the process.</span></span>

- <span data-ttu-id="2ce29-195">Emacs- `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-195">Emacs: `<Ctrl+d>`</span></span>

### <a name="deleteendofbuffer"></a><span data-ttu-id="2ce29-196">DeleteEndOfBuffer</span><span class="sxs-lookup"><span data-stu-id="2ce29-196">DeleteEndOfBuffer</span></span>

<span data-ttu-id="2ce29-197">Supprime à la fin de la mémoire tampon multiligne.</span><span class="sxs-lookup"><span data-stu-id="2ce29-197">Deletes to the end of the multiline buffer.</span></span>

- <span data-ttu-id="2ce29-198">Mode de commande VI : `<d,G>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-198">Vi command mode: `<d,G>`</span></span>

### <a name="deleteendofword"></a><span data-ttu-id="2ce29-199">DeleteEndOfWord</span><span class="sxs-lookup"><span data-stu-id="2ce29-199">DeleteEndOfWord</span></span>

<span data-ttu-id="2ce29-200">Supprimer à la fin du mot.</span><span class="sxs-lookup"><span data-stu-id="2ce29-200">Delete to the end of the word.</span></span>

- <span data-ttu-id="2ce29-201">Mode de commande VI : `<d,e>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-201">Vi command mode: `<d,e>`</span></span>

### <a name="deleteline"></a><span data-ttu-id="2ce29-202">DeleteLine</span><span class="sxs-lookup"><span data-stu-id="2ce29-202">DeleteLine</span></span>

<span data-ttu-id="2ce29-203">Supprime la ligne logique actuelle d’une mémoire tampon multiligne, ce qui permet d’annuler.</span><span class="sxs-lookup"><span data-stu-id="2ce29-203">Deletes the current logical line of a multiline buffer, enabling undo.</span></span>

- <span data-ttu-id="2ce29-204">Mode de commande VI : `<d,d>` , `<d,_>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-204">Vi command mode: `<d,d>`, `<d,_>`</span></span>

### <a name="deletepreviouslines"></a><span data-ttu-id="2ce29-205">DeletePreviousLines</span><span class="sxs-lookup"><span data-stu-id="2ce29-205">DeletePreviousLines</span></span>

<span data-ttu-id="2ce29-206">Supprime les lignes logiques requises précédentes et la ligne logique actuelle dans une mémoire tampon multiligne.</span><span class="sxs-lookup"><span data-stu-id="2ce29-206">Deletes the previous requested logical lines and the current logical line in a multiline buffer.</span></span>

- <span data-ttu-id="2ce29-207">Mode de commande VI : `<d,k>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-207">Vi command mode: `<d,k>`</span></span>

### <a name="deleterelativelines"></a><span data-ttu-id="2ce29-208">DeleteRelativeLines</span><span class="sxs-lookup"><span data-stu-id="2ce29-208">DeleteRelativeLines</span></span>

<span data-ttu-id="2ce29-209">Supprime du début de la mémoire tampon jusqu’à la ligne logique actuelle dans une mémoire tampon multiligne.</span><span class="sxs-lookup"><span data-stu-id="2ce29-209">Deletes from the beginning of the buffer to the current logical line in a multiline buffer.</span></span>

<span data-ttu-id="2ce29-210">Comme la plupart des commandes VI, la `<d,g,g>` commande peut être précédée d’un argument numérique qui spécifie un numéro de ligne absolu, qui, avec le numéro de ligne en cours, compose une plage de lignes à supprimer.</span><span class="sxs-lookup"><span data-stu-id="2ce29-210">As most Vi commands, the `<d,g,g>` command can be prepended with a numeric argument that specifies an absolute line number, which, together with the current line number, make up a range of lines to be deleted.</span></span>
<span data-ttu-id="2ce29-211">S’il n’est pas spécifié, l’argument numérique a la valeur par défaut 1, qui fait référence à la première ligne logique dans une mémoire tampon multiligne.</span><span class="sxs-lookup"><span data-stu-id="2ce29-211">If not specified, the numeric argument defaults to 1, which refers to the first logical line in a multiline buffer.</span></span>

<span data-ttu-id="2ce29-212">Le nombre réel de lignes à supprimer de la ligne multiligne est calculé comme étant la différence entre le numéro de ligne logique actuel et l’argument numérique spécifié, qui peut donc être négatif.</span><span class="sxs-lookup"><span data-stu-id="2ce29-212">The actual number of lines to be deleted from the multiline is computed as the difference between the current logical line number and the specified numeric argument, which can thus be negative.</span></span> <span data-ttu-id="2ce29-213">Par conséquent, la partie _relative_ du nom de la méthode.</span><span class="sxs-lookup"><span data-stu-id="2ce29-213">Hence the _relative_ part of method name.</span></span>

- <span data-ttu-id="2ce29-214">Mode de commande VI : `<d,g,g>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-214">Vi command mode: `<d,g,g>`</span></span>

### <a name="deletenextlines"></a><span data-ttu-id="2ce29-215">DeleteNextLines</span><span class="sxs-lookup"><span data-stu-id="2ce29-215">DeleteNextLines</span></span>

<span data-ttu-id="2ce29-216">Supprime la ligne logique actuelle et les lignes logiques suivantes demandées dans une mémoire tampon multiligne.</span><span class="sxs-lookup"><span data-stu-id="2ce29-216">Deletes the current logical line and the next requested logical lines in a multiline buffer.</span></span>

- <span data-ttu-id="2ce29-217">Mode de commande VI : `<d,j>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-217">Vi command mode: `<d,j>`</span></span>

### <a name="deletelinetofirstchar"></a><span data-ttu-id="2ce29-218">DeleteLineToFirstChar</span><span class="sxs-lookup"><span data-stu-id="2ce29-218">DeleteLineToFirstChar</span></span>

<span data-ttu-id="2ce29-219">Supprime le texte du curseur jusqu’au premier caractère non vide de la ligne.</span><span class="sxs-lookup"><span data-stu-id="2ce29-219">Deletes text from the cursor to the first non-blank character of the line.</span></span>

- <span data-ttu-id="2ce29-220">Mode de commande VI : `<d,^>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-220">Vi command mode: `<d,^>`</span></span>

### <a name="deletetoend"></a><span data-ttu-id="2ce29-221">DeleteToEnd</span><span class="sxs-lookup"><span data-stu-id="2ce29-221">DeleteToEnd</span></span>

<span data-ttu-id="2ce29-222">Supprimer à la fin de la ligne.</span><span class="sxs-lookup"><span data-stu-id="2ce29-222">Delete to the end of the line.</span></span>

- <span data-ttu-id="2ce29-223">Mode de commande VI : `<D>` , `<d,$>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-223">Vi command mode: `<D>`, `<d,$>`</span></span>

### <a name="deleteword"></a><span data-ttu-id="2ce29-224">DeleteWord</span><span class="sxs-lookup"><span data-stu-id="2ce29-224">DeleteWord</span></span>

<span data-ttu-id="2ce29-225">Supprimer le mot suivant.</span><span class="sxs-lookup"><span data-stu-id="2ce29-225">Delete the next word.</span></span>

- <span data-ttu-id="2ce29-226">Mode de commande VI : `<d,w>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-226">Vi command mode: `<d,w>`</span></span>

### <a name="forwarddeleteline"></a><span data-ttu-id="2ce29-227">ForwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="2ce29-227">ForwardDeleteLine</span></span>

<span data-ttu-id="2ce29-228">Comme ForwardKillLine-supprime le texte du point jusqu’à la fin de la ligne, mais ne place pas le texte supprimé dans l’anneau Kill.</span><span class="sxs-lookup"><span data-stu-id="2ce29-228">Like ForwardKillLine - deletes text from the point to the end of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="2ce29-229">Cmd `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-229">Cmd: `<Ctrl+End>`</span></span>
- <span data-ttu-id="2ce29-230">Mode d’insertion VI : `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-230">Vi insert mode: `<Ctrl+End>`</span></span>
- <span data-ttu-id="2ce29-231">Mode de commande VI : `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-231">Vi command mode: `<Ctrl+End>`</span></span>

### <a name="insertlineabove"></a><span data-ttu-id="2ce29-232">InsertLineAbove</span><span class="sxs-lookup"><span data-stu-id="2ce29-232">InsertLineAbove</span></span>

<span data-ttu-id="2ce29-233">Une nouvelle ligne vide est créée au-dessus de la ligne active, quel que soit l’endroit où se trouve le curseur sur la ligne active.</span><span class="sxs-lookup"><span data-stu-id="2ce29-233">A new empty line is created above the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="2ce29-234">Le curseur se déplace au début de la nouvelle ligne.</span><span class="sxs-lookup"><span data-stu-id="2ce29-234">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="2ce29-235">Cmd `<Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-235">Cmd: `<Ctrl+Enter>`</span></span>

### <a name="insertlinebelow"></a><span data-ttu-id="2ce29-236">InsertLineBelow</span><span class="sxs-lookup"><span data-stu-id="2ce29-236">InsertLineBelow</span></span>

<span data-ttu-id="2ce29-237">Une nouvelle ligne vide est créée sous la ligne active, quel que soit l’endroit où se trouve le curseur sur la ligne active.</span><span class="sxs-lookup"><span data-stu-id="2ce29-237">A new empty line is created below the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="2ce29-238">Le curseur se déplace au début de la nouvelle ligne.</span><span class="sxs-lookup"><span data-stu-id="2ce29-238">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="2ce29-239">Cmd `<Shift+Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-239">Cmd: `<Shift+Ctrl+Enter>`</span></span>

### <a name="invertcase"></a><span data-ttu-id="2ce29-240">InvertCase</span><span class="sxs-lookup"><span data-stu-id="2ce29-240">InvertCase</span></span>

<span data-ttu-id="2ce29-241">Inverser la casse du caractère actuel et passer au suivant.</span><span class="sxs-lookup"><span data-stu-id="2ce29-241">Invert the case of the current character and move to the next one.</span></span>

- <span data-ttu-id="2ce29-242">Mode de commande VI : `<~>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-242">Vi command mode: `<~>`</span></span>

### <a name="killline"></a><span data-ttu-id="2ce29-243">KillLine</span><span class="sxs-lookup"><span data-stu-id="2ce29-243">KillLine</span></span>

<span data-ttu-id="2ce29-244">Effacez l’entrée du curseur jusqu’à la fin de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="2ce29-244">Clear the input from the cursor to the end of the input.</span></span> <span data-ttu-id="2ce29-245">Le texte effacé est placé dans le Kill-Ring.</span><span class="sxs-lookup"><span data-stu-id="2ce29-245">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="2ce29-246">Emacs- `<Ctrl+k>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-246">Emacs: `<Ctrl+k>`</span></span>

### <a name="killregion"></a><span data-ttu-id="2ce29-247">KillRegion</span><span class="sxs-lookup"><span data-stu-id="2ce29-247">KillRegion</span></span>

<span data-ttu-id="2ce29-248">Supprimer le texte situé entre le curseur et la marque.</span><span class="sxs-lookup"><span data-stu-id="2ce29-248">Kill the text between the cursor and the mark.</span></span>

- <span data-ttu-id="2ce29-249">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="2ce29-249">Function is unbound.</span></span>

### <a name="killword"></a><span data-ttu-id="2ce29-250">KillWord</span><span class="sxs-lookup"><span data-stu-id="2ce29-250">KillWord</span></span>

<span data-ttu-id="2ce29-251">Efface l’entrée du curseur jusqu’à la fin du mot actuel.</span><span class="sxs-lookup"><span data-stu-id="2ce29-251">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="2ce29-252">Si le curseur se trouve entre des mots, l’entrée est effacée du curseur jusqu’à la fin du mot suivant.</span><span class="sxs-lookup"><span data-stu-id="2ce29-252">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="2ce29-253">Le texte effacé est placé dans le Kill-Ring.</span><span class="sxs-lookup"><span data-stu-id="2ce29-253">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="2ce29-254">Cmd : `<Alt+d>` , `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-254">Cmd: `<Alt+d>`, `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="2ce29-255">Emacs- `<Alt+d>` , `<Escape,d>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-255">Emacs: `<Alt+d>`, `<Escape,d>`</span></span>
- <span data-ttu-id="2ce29-256">Mode d’insertion VI : `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-256">Vi insert mode: `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="2ce29-257">Mode de commande VI : `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-257">Vi command mode: `<Ctrl+Delete>`</span></span>

### <a name="paste"></a><span data-ttu-id="2ce29-258">Coller</span><span class="sxs-lookup"><span data-stu-id="2ce29-258">Paste</span></span>

<span data-ttu-id="2ce29-259">Collez le texte à partir du presse-papiers du système.</span><span class="sxs-lookup"><span data-stu-id="2ce29-259">Paste text from the system clipboard.</span></span>

- <span data-ttu-id="2ce29-260">Cmd : `<Ctrl+v>` , `<Shift+Insert>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-260">Cmd: `<Ctrl+v>`, `<Shift+Insert>`</span></span>
- <span data-ttu-id="2ce29-261">Mode d’insertion VI : `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-261">Vi insert mode: `<Ctrl+v>`</span></span>
- <span data-ttu-id="2ce29-262">Mode de commande VI : `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-262">Vi command mode: `<Ctrl+v>`</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2ce29-263">Lors de l’utilisation de la fonction **Paste** , le contenu entier de la mémoire tampon du presse-papiers est collé dans la mémoire tampon d’entrée de PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="2ce29-263">When using the **Paste** function, the entire contents of the clipboard buffer is pasted into the input buffer of PSReadLine.</span></span> <span data-ttu-id="2ce29-264">La mémoire tampon d’entrée est ensuite transmise à l’analyseur PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2ce29-264">The input buffer is then passed to the PowerShell parser.</span></span> <span data-ttu-id="2ce29-265">L’entrée collée à l’aide de la méthode de collage **avec le bouton droit** de la console de l’application de console est copiée dans la mémoire tampon d’entrée un caractère à la fois.</span><span class="sxs-lookup"><span data-stu-id="2ce29-265">Input pasted using the console application's **right-click** paste method is copied to the input buffer one character at a time.</span></span> <span data-ttu-id="2ce29-266">La mémoire tampon d’entrée est transmise à l’analyseur lorsqu’un caractère de saut de ligne est copié.</span><span class="sxs-lookup"><span data-stu-id="2ce29-266">The input buffer is passed to the parser when a newline character is copied.</span></span> <span data-ttu-id="2ce29-267">Par conséquent, l’entrée est analysée une ligne à la fois.</span><span class="sxs-lookup"><span data-stu-id="2ce29-267">Therefore, the input is parsed one line at a time.</span></span> <span data-ttu-id="2ce29-268">La différence entre les méthodes de collage entraîne un comportement d’exécution différent.</span><span class="sxs-lookup"><span data-stu-id="2ce29-268">The difference between paste methods results in different execution behavior.</span></span>

### <a name="pasteafter"></a><span data-ttu-id="2ce29-269">PasteAfter</span><span class="sxs-lookup"><span data-stu-id="2ce29-269">PasteAfter</span></span>

<span data-ttu-id="2ce29-270">Collez le presse-papiers après le curseur, en déplaçant le curseur à la fin du texte collé.</span><span class="sxs-lookup"><span data-stu-id="2ce29-270">Paste the clipboard after the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="2ce29-271">Mode de commande VI : `<p>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-271">Vi command mode: `<p>`</span></span>

### <a name="pastebefore"></a><span data-ttu-id="2ce29-272">PasteBefore</span><span class="sxs-lookup"><span data-stu-id="2ce29-272">PasteBefore</span></span>

<span data-ttu-id="2ce29-273">Collez le presse-papiers avant le curseur, en déplaçant le curseur à la fin du texte collé.</span><span class="sxs-lookup"><span data-stu-id="2ce29-273">Paste the clipboard before the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="2ce29-274">Mode de commande VI : `<P>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-274">Vi command mode: `<P>`</span></span>

### <a name="prependandaccept"></a><span data-ttu-id="2ce29-275">PrependAndAccept</span><span class="sxs-lookup"><span data-stu-id="2ce29-275">PrependAndAccept</span></span>

<span data-ttu-id="2ce29-276">Faites précéder un' # 'et acceptez la ligne.</span><span class="sxs-lookup"><span data-stu-id="2ce29-276">Prepend a '#' and accept the line.</span></span>

- <span data-ttu-id="2ce29-277">Mode de commande VI : `<#>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-277">Vi command mode: `<#>`</span></span>

### <a name="redo"></a><span data-ttu-id="2ce29-278">Rétablir</span><span class="sxs-lookup"><span data-stu-id="2ce29-278">Redo</span></span>

<span data-ttu-id="2ce29-279">Annule une annulation.</span><span class="sxs-lookup"><span data-stu-id="2ce29-279">Undo an undo.</span></span>

- <span data-ttu-id="2ce29-280">Cmd `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-280">Cmd: `<Ctrl+y>`</span></span>
- <span data-ttu-id="2ce29-281">Mode d’insertion VI : `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-281">Vi insert mode: `<Ctrl+y>`</span></span>
- <span data-ttu-id="2ce29-282">Mode de commande VI : `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-282">Vi command mode: `<Ctrl+y>`</span></span>

### <a name="repeatlastcommand"></a><span data-ttu-id="2ce29-283">RepeatLastCommand</span><span class="sxs-lookup"><span data-stu-id="2ce29-283">RepeatLastCommand</span></span>

<span data-ttu-id="2ce29-284">Répète la dernière modification de texte.</span><span class="sxs-lookup"><span data-stu-id="2ce29-284">Repeat the last text modification.</span></span>

- <span data-ttu-id="2ce29-285">Mode de commande VI : `<.>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-285">Vi command mode: `<.>`</span></span>

### <a name="revertline"></a><span data-ttu-id="2ce29-286">RevertLine</span><span class="sxs-lookup"><span data-stu-id="2ce29-286">RevertLine</span></span>

<span data-ttu-id="2ce29-287">Rétablit toutes les entrées de l’entrée actuelle.</span><span class="sxs-lookup"><span data-stu-id="2ce29-287">Reverts all of the input to the current input.</span></span>

- <span data-ttu-id="2ce29-288">Cmd `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-288">Cmd: `<Escape>`</span></span>
- <span data-ttu-id="2ce29-289">Emacs- `<Alt+r>` , `<Escape,r>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-289">Emacs: `<Alt+r>`, `<Escape,r>`</span></span>

### <a name="shellbackwardkillword"></a><span data-ttu-id="2ce29-290">ShellBackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="2ce29-290">ShellBackwardKillWord</span></span>

<span data-ttu-id="2ce29-291">Efface l’entrée du début du mot actuel jusqu’au curseur.</span><span class="sxs-lookup"><span data-stu-id="2ce29-291">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="2ce29-292">Si le curseur se trouve entre des mots, l’entrée est effacée du début du mot précédent au curseur.</span><span class="sxs-lookup"><span data-stu-id="2ce29-292">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="2ce29-293">Le texte effacé est placé dans le Kill-Ring.</span><span class="sxs-lookup"><span data-stu-id="2ce29-293">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="2ce29-294">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="2ce29-294">Function is unbound.</span></span>

### <a name="shellkillword"></a><span data-ttu-id="2ce29-295">ShellKillWord</span><span class="sxs-lookup"><span data-stu-id="2ce29-295">ShellKillWord</span></span>

<span data-ttu-id="2ce29-296">Efface l’entrée du curseur jusqu’à la fin du mot actuel.</span><span class="sxs-lookup"><span data-stu-id="2ce29-296">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="2ce29-297">Si le curseur se trouve entre des mots, l’entrée est effacée du curseur jusqu’à la fin du mot suivant.</span><span class="sxs-lookup"><span data-stu-id="2ce29-297">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="2ce29-298">Le texte effacé est placé dans le Kill-Ring.</span><span class="sxs-lookup"><span data-stu-id="2ce29-298">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="2ce29-299">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="2ce29-299">Function is unbound.</span></span>

### <a name="swapcharacters"></a><span data-ttu-id="2ce29-300">SwapCharacters</span><span class="sxs-lookup"><span data-stu-id="2ce29-300">SwapCharacters</span></span>

<span data-ttu-id="2ce29-301">Permuter le caractère actuel et celui qui le précèdent.</span><span class="sxs-lookup"><span data-stu-id="2ce29-301">Swap the current character and the one before it.</span></span>

- <span data-ttu-id="2ce29-302">Emacs- `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-302">Emacs: `<Ctrl+t>`</span></span>
- <span data-ttu-id="2ce29-303">Mode d’insertion VI : `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-303">Vi insert mode: `<Ctrl+t>`</span></span>
- <span data-ttu-id="2ce29-304">Mode de commande VI : `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-304">Vi command mode: `<Ctrl+t>`</span></span>

### <a name="undo"></a><span data-ttu-id="2ce29-305">Annuler</span><span class="sxs-lookup"><span data-stu-id="2ce29-305">Undo</span></span>

<span data-ttu-id="2ce29-306">Annuler une modification précédente.</span><span class="sxs-lookup"><span data-stu-id="2ce29-306">Undo a previous edit.</span></span>

- <span data-ttu-id="2ce29-307">Cmd `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-307">Cmd: `<Ctrl+z>`</span></span>
- <span data-ttu-id="2ce29-308">Emacs- `<Ctrl+_>` , `<Ctrl+x,Ctrl+u>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-308">Emacs: `<Ctrl+_>`, `<Ctrl+x,Ctrl+u>`</span></span>
- <span data-ttu-id="2ce29-309">Mode d’insertion VI : `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-309">Vi insert mode: `<Ctrl+z>`</span></span>
- <span data-ttu-id="2ce29-310">Mode de commande VI : `<Ctrl+z>` , `<u>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-310">Vi command mode: `<Ctrl+z>`, `<u>`</span></span>

### <a name="undoall"></a><span data-ttu-id="2ce29-311">UndoAll</span><span class="sxs-lookup"><span data-stu-id="2ce29-311">UndoAll</span></span>

<span data-ttu-id="2ce29-312">Annule toutes les modifications précédentes pour la ligne.</span><span class="sxs-lookup"><span data-stu-id="2ce29-312">Undo all previous edits for line.</span></span>

- <span data-ttu-id="2ce29-313">Mode de commande VI : `<U>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-313">Vi command mode: `<U>`</span></span>

### <a name="unixwordrubout"></a><span data-ttu-id="2ce29-314">UnixWordRubout</span><span class="sxs-lookup"><span data-stu-id="2ce29-314">UnixWordRubout</span></span>

<span data-ttu-id="2ce29-315">Efface l’entrée du début du mot actuel jusqu’au curseur.</span><span class="sxs-lookup"><span data-stu-id="2ce29-315">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="2ce29-316">Si le curseur se trouve entre des mots, l’entrée est effacée du début du mot précédent au curseur.</span><span class="sxs-lookup"><span data-stu-id="2ce29-316">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="2ce29-317">Le texte effacé est placé dans le Kill-Ring.</span><span class="sxs-lookup"><span data-stu-id="2ce29-317">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="2ce29-318">Emacs- `<Ctrl+w>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-318">Emacs: `<Ctrl+w>`</span></span>

### <a name="validateandacceptline"></a><span data-ttu-id="2ce29-319">ValidateAndAcceptLine</span><span class="sxs-lookup"><span data-stu-id="2ce29-319">ValidateAndAcceptLine</span></span>

<span data-ttu-id="2ce29-320">Tentative d’exécution de l’entrée en cours.</span><span class="sxs-lookup"><span data-stu-id="2ce29-320">Attempt to execute the current input.</span></span> <span data-ttu-id="2ce29-321">Si l’entrée actuelle est incomplète (par exemple, il manque une parenthèse fermante, un crochet ou un guillemet, l’invite de continuation est affichée sur la ligne suivante et PSReadLine attend que les clés modifient l’entrée actuelle.</span><span class="sxs-lookup"><span data-stu-id="2ce29-321">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="2ce29-322">Emacs- `<Ctrl+m>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-322">Emacs: `<Ctrl+m>`</span></span>

### <a name="viacceptline"></a><span data-ttu-id="2ce29-323">ViAcceptLine</span><span class="sxs-lookup"><span data-stu-id="2ce29-323">ViAcceptLine</span></span>

<span data-ttu-id="2ce29-324">Acceptez la ligne et passez en mode insertion.</span><span class="sxs-lookup"><span data-stu-id="2ce29-324">Accept the line and switch to Insert mode.</span></span>

- <span data-ttu-id="2ce29-325">Mode de commande VI : `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-325">Vi command mode: `<Enter>`</span></span>

### <a name="viacceptlineorexit"></a><span data-ttu-id="2ce29-326">ViAcceptLineOrExit</span><span class="sxs-lookup"><span data-stu-id="2ce29-326">ViAcceptLineOrExit</span></span>

<span data-ttu-id="2ce29-327">Comme DeleteCharOrExit en mode emacs, mais accepte la ligne au lieu de supprimer un caractère.</span><span class="sxs-lookup"><span data-stu-id="2ce29-327">Like DeleteCharOrExit in Emacs mode, but accepts the line instead of deleting a character.</span></span>

- <span data-ttu-id="2ce29-328">Mode d’insertion VI : `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-328">Vi insert mode: `<Ctrl+d>`</span></span>
- <span data-ttu-id="2ce29-329">Mode de commande VI : `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-329">Vi command mode: `<Ctrl+d>`</span></span>

### <a name="viappendline"></a><span data-ttu-id="2ce29-330">ViAppendLine</span><span class="sxs-lookup"><span data-stu-id="2ce29-330">ViAppendLine</span></span>

<span data-ttu-id="2ce29-331">Une nouvelle ligne est insérée au-dessous de la ligne active.</span><span class="sxs-lookup"><span data-stu-id="2ce29-331">A new line is inserted below the current line.</span></span>

- <span data-ttu-id="2ce29-332">Mode de commande VI : `<o>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-332">Vi command mode: `<o>`</span></span>

### <a name="vibackwarddeleteglob"></a><span data-ttu-id="2ce29-333">ViBackwardDeleteGlob</span><span class="sxs-lookup"><span data-stu-id="2ce29-333">ViBackwardDeleteGlob</span></span>

<span data-ttu-id="2ce29-334">Supprime le mot précédent, en utilisant uniquement un espace blanc comme délimiteur de mot.</span><span class="sxs-lookup"><span data-stu-id="2ce29-334">Deletes the previous word, using only white space as the word delimiter.</span></span>

- <span data-ttu-id="2ce29-335">Mode de commande VI : `<d,B>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-335">Vi command mode: `<d,B>`</span></span>

### <a name="vibackwardglob"></a><span data-ttu-id="2ce29-336">ViBackwardGlob</span><span class="sxs-lookup"><span data-stu-id="2ce29-336">ViBackwardGlob</span></span>

<span data-ttu-id="2ce29-337">Déplace le curseur au début du mot précédent, en utilisant uniquement des espaces blancs comme délimiteurs.</span><span class="sxs-lookup"><span data-stu-id="2ce29-337">Moves the cursor back to the beginning of the previous word, using only white space as delimiters.</span></span>

- <span data-ttu-id="2ce29-338">Mode de commande VI : `<B>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-338">Vi command mode: `<B>`</span></span>

### <a name="videletebrace"></a><span data-ttu-id="2ce29-339">ViDeleteBrace</span><span class="sxs-lookup"><span data-stu-id="2ce29-339">ViDeleteBrace</span></span>

<span data-ttu-id="2ce29-340">Recherchez l’accolade correspondante, la parenthèse ou le crochet, et supprimez tout le contenu dans, y compris l’accolade.</span><span class="sxs-lookup"><span data-stu-id="2ce29-340">Find the matching brace, parenthesis, or square bracket and delete all contents within, including the brace.</span></span>

- <span data-ttu-id="2ce29-341">Mode de commande VI : `<d,%>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-341">Vi command mode: `<d,%>`</span></span>

### <a name="videleteendofglob"></a><span data-ttu-id="2ce29-342">ViDeleteEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="2ce29-342">ViDeleteEndOfGlob</span></span>

<span data-ttu-id="2ce29-343">Supprimer à la fin du mot.</span><span class="sxs-lookup"><span data-stu-id="2ce29-343">Delete to the end of the word.</span></span>

- <span data-ttu-id="2ce29-344">Mode de commande VI : `<d,E>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-344">Vi command mode: `<d,E>`</span></span>

### <a name="videleteglob"></a><span data-ttu-id="2ce29-345">ViDeleteGlob</span><span class="sxs-lookup"><span data-stu-id="2ce29-345">ViDeleteGlob</span></span>

<span data-ttu-id="2ce29-346">Supprime la glob suivante (mot blanc délimité par des espaces).</span><span class="sxs-lookup"><span data-stu-id="2ce29-346">Delete the next glob (white space delimited word).</span></span>

- <span data-ttu-id="2ce29-347">Mode de commande VI : `<d,W>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-347">Vi command mode: `<d,W>`</span></span>

### <a name="videletetobeforechar"></a><span data-ttu-id="2ce29-348">ViDeleteToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="2ce29-348">ViDeleteToBeforeChar</span></span>

<span data-ttu-id="2ce29-349">Supprime jusqu’au caractère donné.</span><span class="sxs-lookup"><span data-stu-id="2ce29-349">Deletes until given character.</span></span>

- <span data-ttu-id="2ce29-350">Mode de commande VI : `<d,t>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-350">Vi command mode: `<d,t>`</span></span>

### <a name="videletetobeforecharbackward"></a><span data-ttu-id="2ce29-351">ViDeleteToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="2ce29-351">ViDeleteToBeforeCharBackward</span></span>

<span data-ttu-id="2ce29-352">Supprime jusqu’au caractère donné.</span><span class="sxs-lookup"><span data-stu-id="2ce29-352">Deletes until given character.</span></span>

- <span data-ttu-id="2ce29-353">Mode de commande VI : `<d,T>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-353">Vi command mode: `<d,T>`</span></span>

### <a name="videletetochar"></a><span data-ttu-id="2ce29-354">ViDeleteToChar</span><span class="sxs-lookup"><span data-stu-id="2ce29-354">ViDeleteToChar</span></span>

<span data-ttu-id="2ce29-355">Supprime jusqu’au caractère donné.</span><span class="sxs-lookup"><span data-stu-id="2ce29-355">Deletes until given character.</span></span>

- <span data-ttu-id="2ce29-356">Mode de commande VI : `<d,f>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-356">Vi command mode: `<d,f>`</span></span>

### <a name="videletetocharbackward"></a><span data-ttu-id="2ce29-357">ViDeleteToCharBackward</span><span class="sxs-lookup"><span data-stu-id="2ce29-357">ViDeleteToCharBackward</span></span>

<span data-ttu-id="2ce29-358">Supprime vers l’arrière jusqu’au caractère donné.</span><span class="sxs-lookup"><span data-stu-id="2ce29-358">Deletes backwards until given character.</span></span>

- <span data-ttu-id="2ce29-359">Mode de commande VI : `<d,F>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-359">Vi command mode: `<d,F>`</span></span>

### <a name="viinsertatbegining"></a><span data-ttu-id="2ce29-360">ViInsertAtBegining</span><span class="sxs-lookup"><span data-stu-id="2ce29-360">ViInsertAtBegining</span></span>

<span data-ttu-id="2ce29-361">Basculez en mode insertion et positionnez le curseur au début de la ligne.</span><span class="sxs-lookup"><span data-stu-id="2ce29-361">Switch to Insert mode and position the cursor at the beginning of the line.</span></span>

- <span data-ttu-id="2ce29-362">Mode de commande VI : `<I>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-362">Vi command mode: `<I>`</span></span>

### <a name="viinsertatend"></a><span data-ttu-id="2ce29-363">ViInsertAtEnd</span><span class="sxs-lookup"><span data-stu-id="2ce29-363">ViInsertAtEnd</span></span>

<span data-ttu-id="2ce29-364">Basculez en mode insertion et positionnez le curseur à la fin de la ligne.</span><span class="sxs-lookup"><span data-stu-id="2ce29-364">Switch to Insert mode and position the cursor at the end of the line.</span></span>

- <span data-ttu-id="2ce29-365">Mode de commande VI : `<A>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-365">Vi command mode: `<A>`</span></span>

### <a name="viinsertline"></a><span data-ttu-id="2ce29-366">ViInsertLine</span><span class="sxs-lookup"><span data-stu-id="2ce29-366">ViInsertLine</span></span>

<span data-ttu-id="2ce29-367">Une nouvelle ligne est insérée au-dessus de la ligne active.</span><span class="sxs-lookup"><span data-stu-id="2ce29-367">A new line is inserted above the current line.</span></span>

- <span data-ttu-id="2ce29-368">Mode de commande VI : `<O>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-368">Vi command mode: `<O>`</span></span>

### <a name="viinsertwithappend"></a><span data-ttu-id="2ce29-369">ViInsertWithAppend</span><span class="sxs-lookup"><span data-stu-id="2ce29-369">ViInsertWithAppend</span></span>

<span data-ttu-id="2ce29-370">Ajouter à partir de la position de la ligne active.</span><span class="sxs-lookup"><span data-stu-id="2ce29-370">Append from the current line position.</span></span>

- <span data-ttu-id="2ce29-371">Mode de commande VI : `<a>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-371">Vi command mode: `<a>`</span></span>

### <a name="viinsertwithdelete"></a><span data-ttu-id="2ce29-372">ViInsertWithDelete</span><span class="sxs-lookup"><span data-stu-id="2ce29-372">ViInsertWithDelete</span></span>

<span data-ttu-id="2ce29-373">Supprimez le caractère actuel et basculez en mode insertion.</span><span class="sxs-lookup"><span data-stu-id="2ce29-373">Delete the current character and switch to Insert mode.</span></span>

- <span data-ttu-id="2ce29-374">Mode de commande VI : `<s>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-374">Vi command mode: `<s>`</span></span>

### <a name="vijoinlines"></a><span data-ttu-id="2ce29-375">ViJoinLines</span><span class="sxs-lookup"><span data-stu-id="2ce29-375">ViJoinLines</span></span>

<span data-ttu-id="2ce29-376">Joint la ligne active et la ligne suivante.</span><span class="sxs-lookup"><span data-stu-id="2ce29-376">Joins the current line and the next line.</span></span>

- <span data-ttu-id="2ce29-377">Mode de commande VI : `<J>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-377">Vi command mode: `<J>`</span></span>

### <a name="vireplaceline"></a><span data-ttu-id="2ce29-378">ViReplaceLine</span><span class="sxs-lookup"><span data-stu-id="2ce29-378">ViReplaceLine</span></span>

<span data-ttu-id="2ce29-379">Effacez l’intégralité de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="2ce29-379">Erase the entire command line.</span></span>

- <span data-ttu-id="2ce29-380">Mode de commande VI : `<S>` , `<c,c>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-380">Vi command mode: `<S>`, `<c,c>`</span></span>

### <a name="vireplacetobeforechar"></a><span data-ttu-id="2ce29-381">ViReplaceToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="2ce29-381">ViReplaceToBeforeChar</span></span>

<span data-ttu-id="2ce29-382">Remplace jusqu’au caractère donné.</span><span class="sxs-lookup"><span data-stu-id="2ce29-382">Replaces until given character.</span></span>

- <span data-ttu-id="2ce29-383">Mode de commande VI : `<c,t>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-383">Vi command mode: `<c,t>`</span></span>

### <a name="vireplacetobeforecharbackward"></a><span data-ttu-id="2ce29-384">ViReplaceToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="2ce29-384">ViReplaceToBeforeCharBackward</span></span>

<span data-ttu-id="2ce29-385">Remplace jusqu’au caractère donné.</span><span class="sxs-lookup"><span data-stu-id="2ce29-385">Replaces until given character.</span></span>

- <span data-ttu-id="2ce29-386">Mode de commande VI : `<c,T>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-386">Vi command mode: `<c,T>`</span></span>

### <a name="vireplacetochar"></a><span data-ttu-id="2ce29-387">ViReplaceToChar</span><span class="sxs-lookup"><span data-stu-id="2ce29-387">ViReplaceToChar</span></span>

<span data-ttu-id="2ce29-388">Supprime jusqu’au caractère donné.</span><span class="sxs-lookup"><span data-stu-id="2ce29-388">Deletes until given character.</span></span>

- <span data-ttu-id="2ce29-389">Mode de commande VI : `<c,f>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-389">Vi command mode: `<c,f>`</span></span>

### <a name="vireplacetocharbackward"></a><span data-ttu-id="2ce29-390">ViReplaceToCharBackward</span><span class="sxs-lookup"><span data-stu-id="2ce29-390">ViReplaceToCharBackward</span></span>

<span data-ttu-id="2ce29-391">Remplace jusqu’au caractère donné.</span><span class="sxs-lookup"><span data-stu-id="2ce29-391">Replaces until given character.</span></span>

- <span data-ttu-id="2ce29-392">Mode de commande VI : `<c,F>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-392">Vi command mode: `<c,F>`</span></span>

### <a name="viyankbeginningofline"></a><span data-ttu-id="2ce29-393">ViYankBeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="2ce29-393">ViYankBeginningOfLine</span></span>

<span data-ttu-id="2ce29-394">Yank entre le début de la mémoire tampon et le curseur.</span><span class="sxs-lookup"><span data-stu-id="2ce29-394">Yank from the beginning of the buffer to the cursor.</span></span>

- <span data-ttu-id="2ce29-395">Mode de commande VI : `<y,0>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-395">Vi command mode: `<y,0>`</span></span>

### <a name="viyankendofglob"></a><span data-ttu-id="2ce29-396">ViYankEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="2ce29-396">ViYankEndOfGlob</span></span>

<span data-ttu-id="2ce29-397">Yank du curseur jusqu’à la fin du ou des mots.</span><span class="sxs-lookup"><span data-stu-id="2ce29-397">Yank from the cursor to the end of the WORD(s).</span></span>

- <span data-ttu-id="2ce29-398">Mode de commande VI : `<y,E>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-398">Vi command mode: `<y,E>`</span></span>

### <a name="viyankendofword"></a><span data-ttu-id="2ce29-399">ViYankEndOfWord</span><span class="sxs-lookup"><span data-stu-id="2ce29-399">ViYankEndOfWord</span></span>

<span data-ttu-id="2ce29-400">Yank du curseur jusqu’à la fin du ou des mots.</span><span class="sxs-lookup"><span data-stu-id="2ce29-400">Yank from the cursor to the end of the word(s).</span></span>

- <span data-ttu-id="2ce29-401">Mode de commande VI : `<y,e>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-401">Vi command mode: `<y,e>`</span></span>

### <a name="viyankleft"></a><span data-ttu-id="2ce29-402">ViYankLeft</span><span class="sxs-lookup"><span data-stu-id="2ce29-402">ViYankLeft</span></span>

<span data-ttu-id="2ce29-403">Yank caractère (s) à gauche du curseur.</span><span class="sxs-lookup"><span data-stu-id="2ce29-403">Yank character(s) to the left of the cursor.</span></span>

- <span data-ttu-id="2ce29-404">Mode de commande VI : `<y,h>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-404">Vi command mode: `<y,h>`</span></span>

### <a name="viyankline"></a><span data-ttu-id="2ce29-405">ViYankLine</span><span class="sxs-lookup"><span data-stu-id="2ce29-405">ViYankLine</span></span>

<span data-ttu-id="2ce29-406">Yank la mémoire tampon entière.</span><span class="sxs-lookup"><span data-stu-id="2ce29-406">Yank the entire buffer.</span></span>

- <span data-ttu-id="2ce29-407">Mode de commande VI : `<y,y>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-407">Vi command mode: `<y,y>`</span></span>

### <a name="viyanknextglob"></a><span data-ttu-id="2ce29-408">ViYankNextGlob</span><span class="sxs-lookup"><span data-stu-id="2ce29-408">ViYankNextGlob</span></span>

<span data-ttu-id="2ce29-409">Yank à partir d’un curseur jusqu’au début du ou des mots suivants.</span><span class="sxs-lookup"><span data-stu-id="2ce29-409">Yank from cursor to the start of the next WORD(s).</span></span>

- <span data-ttu-id="2ce29-410">Mode de commande VI : `<y,W>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-410">Vi command mode: `<y,W>`</span></span>

### <a name="viyanknextword"></a><span data-ttu-id="2ce29-411">ViYankNextWord</span><span class="sxs-lookup"><span data-stu-id="2ce29-411">ViYankNextWord</span></span>

<span data-ttu-id="2ce29-412">Yank le ou les mots après le curseur.</span><span class="sxs-lookup"><span data-stu-id="2ce29-412">Yank the word(s) after the cursor.</span></span>

- <span data-ttu-id="2ce29-413">Mode de commande VI : `<y,w>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-413">Vi command mode: `<y,w>`</span></span>

### <a name="viyankpercent"></a><span data-ttu-id="2ce29-414">ViYankPercent</span><span class="sxs-lookup"><span data-stu-id="2ce29-414">ViYankPercent</span></span>

<span data-ttu-id="2ce29-415">Yank à/à partir de l’accolade correspondante.</span><span class="sxs-lookup"><span data-stu-id="2ce29-415">Yank to/from matching brace.</span></span>

- <span data-ttu-id="2ce29-416">Mode de commande VI : `<y,%>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-416">Vi command mode: `<y,%>`</span></span>

### <a name="viyankpreviousglob"></a><span data-ttu-id="2ce29-417">ViYankPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="2ce29-417">ViYankPreviousGlob</span></span>

<span data-ttu-id="2ce29-418">Yank entre le début du ou des mots et le curseur.</span><span class="sxs-lookup"><span data-stu-id="2ce29-418">Yank from beginning of the WORD(s) to cursor.</span></span>

- <span data-ttu-id="2ce29-419">Mode de commande VI : `<y,B>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-419">Vi command mode: `<y,B>`</span></span>

### <a name="viyankpreviousword"></a><span data-ttu-id="2ce29-420">ViYankPreviousWord</span><span class="sxs-lookup"><span data-stu-id="2ce29-420">ViYankPreviousWord</span></span>

<span data-ttu-id="2ce29-421">Yank le ou les mots avant le curseur.</span><span class="sxs-lookup"><span data-stu-id="2ce29-421">Yank the word(s) before the cursor.</span></span>

- <span data-ttu-id="2ce29-422">Mode de commande VI : `<y,b>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-422">Vi command mode: `<y,b>`</span></span>

### <a name="viyankright"></a><span data-ttu-id="2ce29-423">ViYankRight</span><span class="sxs-lookup"><span data-stu-id="2ce29-423">ViYankRight</span></span>

<span data-ttu-id="2ce29-424">Yank caractère (s) situé sous et à droite du curseur.</span><span class="sxs-lookup"><span data-stu-id="2ce29-424">Yank character(s) under and to the right of the cursor.</span></span>

- <span data-ttu-id="2ce29-425">Mode de commande VI : `<y,l>` , `<y,Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-425">Vi command mode: `<y,l>`, `<y,Spacebar>`</span></span>

### <a name="viyanktoendofline"></a><span data-ttu-id="2ce29-426">ViYankToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="2ce29-426">ViYankToEndOfLine</span></span>

<span data-ttu-id="2ce29-427">Yank du curseur jusqu’à la fin de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="2ce29-427">Yank from the cursor to the end of the buffer.</span></span>

- <span data-ttu-id="2ce29-428">Mode de commande VI : `<y,$>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-428">Vi command mode: `<y,$>`</span></span>

### <a name="viyanktofirstchar"></a><span data-ttu-id="2ce29-429">ViYankToFirstChar</span><span class="sxs-lookup"><span data-stu-id="2ce29-429">ViYankToFirstChar</span></span>

<span data-ttu-id="2ce29-430">Yank du premier caractère autre qu’un espace blanc au curseur.</span><span class="sxs-lookup"><span data-stu-id="2ce29-430">Yank from the first non-whitespace character to the cursor.</span></span>

- <span data-ttu-id="2ce29-431">Mode de commande VI : `<y,^>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-431">Vi command mode: `<y,^>`</span></span>

### <a name="yank"></a><span data-ttu-id="2ce29-432">Yank</span><span class="sxs-lookup"><span data-stu-id="2ce29-432">Yank</span></span>

<span data-ttu-id="2ce29-433">Ajoutez le texte le plus récemment supprimé à l’entrée.</span><span class="sxs-lookup"><span data-stu-id="2ce29-433">Add the most recently killed text to the input.</span></span>

- <span data-ttu-id="2ce29-434">Emacs- `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-434">Emacs: `<Ctrl+y>`</span></span>

### <a name="yanklastarg"></a><span data-ttu-id="2ce29-435">YankLastArg</span><span class="sxs-lookup"><span data-stu-id="2ce29-435">YankLastArg</span></span>

<span data-ttu-id="2ce29-436">Yank le dernier argument de la ligne d’historique précédente.</span><span class="sxs-lookup"><span data-stu-id="2ce29-436">Yank the last argument from the previous history line.</span></span> <span data-ttu-id="2ce29-437">Avec un argument, la première fois qu’il est appelé, se comporte comme YankNthArg.</span><span class="sxs-lookup"><span data-stu-id="2ce29-437">With an argument, the first time it is invoked, behaves just like YankNthArg.</span></span> <span data-ttu-id="2ce29-438">Si elle est appelée plusieurs fois, elle itère au sein de l’historique et ARG définit la direction (négatif inverse la direction).</span><span class="sxs-lookup"><span data-stu-id="2ce29-438">If invoked multiple times, instead it iterates through history and arg sets the direction (negative reverses the direction.)</span></span>

- <span data-ttu-id="2ce29-439">Cmd `<Alt+.>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-439">Cmd: `<Alt+.>`</span></span>
- <span data-ttu-id="2ce29-440">Emacs : `<Alt+.>` , `<Alt+_>` , `<Escape,.>` , `<Escape,_>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-440">Emacs: `<Alt+.>`, `<Alt+_>`, `<Escape,.>`, `<Escape,_>`</span></span>

### <a name="yankntharg"></a><span data-ttu-id="2ce29-441">YankNthArg</span><span class="sxs-lookup"><span data-stu-id="2ce29-441">YankNthArg</span></span>

<span data-ttu-id="2ce29-442">Yank le premier argument (après la commande) à partir de la ligne précédente de l’historique.</span><span class="sxs-lookup"><span data-stu-id="2ce29-442">Yank the first argument (after the command) from the previous history line.</span></span>
<span data-ttu-id="2ce29-443">Avec un argument, Yank le nième argument (à partir de 0), si l’argument est négatif, commencez par le dernier argument.</span><span class="sxs-lookup"><span data-stu-id="2ce29-443">With an argument, yank the nth argument (starting from 0), if the argument is negative, start from the last argument.</span></span>

- <span data-ttu-id="2ce29-444">Emacs- `<Ctrl+Alt+y>` , `<Escape,Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-444">Emacs: `<Ctrl+Alt+y>`, `<Escape,Ctrl+y>`</span></span>

### <a name="yankpop"></a><span data-ttu-id="2ce29-445">YankPop</span><span class="sxs-lookup"><span data-stu-id="2ce29-445">YankPop</span></span>

<span data-ttu-id="2ce29-446">Si l’opération précédente était Yank ou YankPop, remplacez le texte précédemment extrait par le texte supprimé suivant de l’instruction KILL-Ring.</span><span class="sxs-lookup"><span data-stu-id="2ce29-446">If the previous operation was Yank or YankPop, replace the previously yanked text with the next killed text from the kill-ring.</span></span>

- <span data-ttu-id="2ce29-447">Emacs- `<Alt+y>` , `<Escape,y>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-447">Emacs: `<Alt+y>`, `<Escape,y>`</span></span>

## <a name="cursor-movement-functions"></a><span data-ttu-id="2ce29-448">Fonctions de déplacement de curseur</span><span class="sxs-lookup"><span data-stu-id="2ce29-448">Cursor movement functions</span></span>

### <a name="backwardchar"></a><span data-ttu-id="2ce29-449">BackwardChar</span><span class="sxs-lookup"><span data-stu-id="2ce29-449">BackwardChar</span></span>

<span data-ttu-id="2ce29-450">Déplacer le curseur d’un caractère vers la gauche.</span><span class="sxs-lookup"><span data-stu-id="2ce29-450">Move the cursor one character to the left.</span></span> <span data-ttu-id="2ce29-451">Cela peut déplacer le curseur vers la ligne précédente de l’entrée multiligne.</span><span class="sxs-lookup"><span data-stu-id="2ce29-451">This may move the cursor to the previous line of multi-line input.</span></span>

- <span data-ttu-id="2ce29-452">Cmd `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-452">Cmd: `<LeftArrow>`</span></span>
- <span data-ttu-id="2ce29-453">Emacs- `<LeftArrow>` , `<Ctrl+b>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-453">Emacs: `<LeftArrow>`, `<Ctrl+b>`</span></span>

### <a name="backwardword"></a><span data-ttu-id="2ce29-454">BackwardWord</span><span class="sxs-lookup"><span data-stu-id="2ce29-454">BackwardWord</span></span>

<span data-ttu-id="2ce29-455">Ramener le curseur au début du mot actuel, ou si entre les mots, le début du mot précédent.</span><span class="sxs-lookup"><span data-stu-id="2ce29-455">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="2ce29-456">Les limites de mots sont définies par un jeu de caractères configurable.</span><span class="sxs-lookup"><span data-stu-id="2ce29-456">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="2ce29-457">Cmd `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-457">Cmd: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="2ce29-458">Emacs- `<Alt+b>` , `<Escape,b>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-458">Emacs: `<Alt+b>`, `<Escape,b>`</span></span>
- <span data-ttu-id="2ce29-459">Mode d’insertion VI : `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-459">Vi insert mode: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="2ce29-460">Mode de commande VI : `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-460">Vi command mode: `<Ctrl+LeftArrow>`</span></span>

### <a name="beginningofline"></a><span data-ttu-id="2ce29-461">BeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="2ce29-461">BeginningOfLine</span></span>

<span data-ttu-id="2ce29-462">Si l’entrée comporte plusieurs lignes, se déplacer au début de la ligne active ou, le cas échéant, au début de la ligne, se déplacer au début de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="2ce29-462">If the input has multiple lines, move to the start of the current line, or if already at the start of the line, move to the start of the input.</span></span> <span data-ttu-id="2ce29-463">Si l’entrée comporte une seule ligne, accédez au début de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="2ce29-463">If the input has a single line, move to the start of the input.</span></span>

- <span data-ttu-id="2ce29-464">Cmd `<Home>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-464">Cmd: `<Home>`</span></span>
- <span data-ttu-id="2ce29-465">Emacs- `<Home>` , `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-465">Emacs: `<Home>`, `<Ctrl+a>`</span></span>
- <span data-ttu-id="2ce29-466">Mode d’insertion VI : `<Home>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-466">Vi insert mode: `<Home>`</span></span>
- <span data-ttu-id="2ce29-467">Mode de commande VI : `<Home>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-467">Vi command mode: `<Home>`</span></span>

### <a name="endofline"></a><span data-ttu-id="2ce29-468">EndOfLine</span><span class="sxs-lookup"><span data-stu-id="2ce29-468">EndOfLine</span></span>

<span data-ttu-id="2ce29-469">Si l’entrée comporte plusieurs lignes, passez à la fin de la ligne active ou, si elle se trouve déjà à la fin de la ligne, à la fin de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="2ce29-469">If the input has multiple lines, move to the end of the current line, or if already at the end of the line, move to the end of the input.</span></span> <span data-ttu-id="2ce29-470">Si l’entrée comporte une seule ligne, passez à la fin de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="2ce29-470">If the input has a single line, move to the end of the input.</span></span>

- <span data-ttu-id="2ce29-471">Cmd `<End>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-471">Cmd: `<End>`</span></span>
- <span data-ttu-id="2ce29-472">Emacs- `<End>` , `<Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-472">Emacs: `<End>`, `<Ctrl+e>`</span></span>
- <span data-ttu-id="2ce29-473">Mode d’insertion VI : `<End>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-473">Vi insert mode: `<End>`</span></span>

### <a name="forwardchar"></a><span data-ttu-id="2ce29-474">ForwardChar</span><span class="sxs-lookup"><span data-stu-id="2ce29-474">ForwardChar</span></span>

<span data-ttu-id="2ce29-475">Déplacer le curseur d’un caractère vers la droite.</span><span class="sxs-lookup"><span data-stu-id="2ce29-475">Move the cursor one character to the right.</span></span> <span data-ttu-id="2ce29-476">Cela peut déplacer le curseur à la ligne suivante de l’entrée multiligne.</span><span class="sxs-lookup"><span data-stu-id="2ce29-476">This may move the cursor to the next line of multi-line input.</span></span>

- <span data-ttu-id="2ce29-477">Cmd `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-477">Cmd: `<RightArrow>`</span></span>
- <span data-ttu-id="2ce29-478">Emacs- `<RightArrow>` , `<Ctrl+f>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-478">Emacs: `<RightArrow>`, `<Ctrl+f>`</span></span>

### <a name="forwardword"></a><span data-ttu-id="2ce29-479">ForwardWord</span><span class="sxs-lookup"><span data-stu-id="2ce29-479">ForwardWord</span></span>

<span data-ttu-id="2ce29-480">Déplacer le curseur vers l’avant jusqu’à la fin du mot actuel, ou si entre les mots, à la fin du mot suivant.</span><span class="sxs-lookup"><span data-stu-id="2ce29-480">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="2ce29-481">Les limites de mots sont définies par un jeu de caractères configurable.</span><span class="sxs-lookup"><span data-stu-id="2ce29-481">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="2ce29-482">Emacs- `<Alt+f>` , `<Escape,f>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-482">Emacs: `<Alt+f>`, `<Escape,f>`</span></span>

### <a name="gotobrace"></a><span data-ttu-id="2ce29-483">GotoBrace</span><span class="sxs-lookup"><span data-stu-id="2ce29-483">GotoBrace</span></span>

<span data-ttu-id="2ce29-484">Atteindre l’accolade correspondante, les parenthèses ou les crochets.</span><span class="sxs-lookup"><span data-stu-id="2ce29-484">Go to the matching brace, parenthesis, or square bracket.</span></span>

- <span data-ttu-id="2ce29-485">Cmd `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-485">Cmd: `<Ctrl+]>`</span></span>
- <span data-ttu-id="2ce29-486">Mode d’insertion VI : `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-486">Vi insert mode: `<Ctrl+]>`</span></span>
- <span data-ttu-id="2ce29-487">Mode de commande VI : `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-487">Vi command mode: `<Ctrl+]>`</span></span>

### <a name="gotocolumn"></a><span data-ttu-id="2ce29-488">GotoColumn</span><span class="sxs-lookup"><span data-stu-id="2ce29-488">GotoColumn</span></span>

<span data-ttu-id="2ce29-489">Accédez à la colonne indiquée par arg.</span><span class="sxs-lookup"><span data-stu-id="2ce29-489">Move to the column indicated by arg.</span></span>

- <span data-ttu-id="2ce29-490">Mode de commande VI : `<|>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-490">Vi command mode: `<|>`</span></span>

### <a name="gotofirstnonblankofline"></a><span data-ttu-id="2ce29-491">GotoFirstNonBlankOfLine</span><span class="sxs-lookup"><span data-stu-id="2ce29-491">GotoFirstNonBlankOfLine</span></span>

<span data-ttu-id="2ce29-492">Placez le curseur sur le premier caractère non vide de la ligne.</span><span class="sxs-lookup"><span data-stu-id="2ce29-492">Move the cursor to the first non-blank character in the line.</span></span>

- <span data-ttu-id="2ce29-493">Mode de commande VI : `<^>` , `<_>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-493">Vi command mode: `<^>`, `<_>`</span></span>

### <a name="movetoendofline"></a><span data-ttu-id="2ce29-494">MoveToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="2ce29-494">MoveToEndOfLine</span></span>

<span data-ttu-id="2ce29-495">Placez le curseur à la fin de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="2ce29-495">Move the cursor to the end of the input.</span></span>

- <span data-ttu-id="2ce29-496">Mode de commande VI : `<End>` , `<$>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-496">Vi command mode: `<End>`, `<$>`</span></span>

### <a name="nextline"></a><span data-ttu-id="2ce29-497">NextLine</span><span class="sxs-lookup"><span data-stu-id="2ce29-497">NextLine</span></span>

<span data-ttu-id="2ce29-498">Déplacer le curseur sur la ligne suivante.</span><span class="sxs-lookup"><span data-stu-id="2ce29-498">Move the cursor to the next line.</span></span>

- <span data-ttu-id="2ce29-499">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="2ce29-499">Function is unbound.</span></span>

### <a name="nextword"></a><span data-ttu-id="2ce29-500">NextWord</span><span class="sxs-lookup"><span data-stu-id="2ce29-500">NextWord</span></span>

<span data-ttu-id="2ce29-501">Déplacer le curseur vers l’avant jusqu’au début du mot suivant.</span><span class="sxs-lookup"><span data-stu-id="2ce29-501">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="2ce29-502">Les limites de mots sont définies par un jeu de caractères configurable.</span><span class="sxs-lookup"><span data-stu-id="2ce29-502">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="2ce29-503">Cmd `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-503">Cmd: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="2ce29-504">Mode d’insertion VI : `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-504">Vi insert mode: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="2ce29-505">Mode de commande VI : `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-505">Vi command mode: `<Ctrl+RightArrow>`</span></span>

### <a name="nextwordend"></a><span data-ttu-id="2ce29-506">NextWordEnd</span><span class="sxs-lookup"><span data-stu-id="2ce29-506">NextWordEnd</span></span>

<span data-ttu-id="2ce29-507">Déplacer le curseur vers l’avant jusqu’à la fin du mot actuel, ou si entre les mots, à la fin du mot suivant.</span><span class="sxs-lookup"><span data-stu-id="2ce29-507">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="2ce29-508">Les limites de mots sont définies par un jeu de caractères configurable.</span><span class="sxs-lookup"><span data-stu-id="2ce29-508">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="2ce29-509">Mode de commande VI : `<e>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-509">Vi command mode: `<e>`</span></span>

### <a name="previousline"></a><span data-ttu-id="2ce29-510">PreviousLine</span><span class="sxs-lookup"><span data-stu-id="2ce29-510">PreviousLine</span></span>

<span data-ttu-id="2ce29-511">Placez le curseur sur la ligne précédente.</span><span class="sxs-lookup"><span data-stu-id="2ce29-511">Move the cursor to the previous line.</span></span>

- <span data-ttu-id="2ce29-512">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="2ce29-512">Function is unbound.</span></span>

### <a name="shellbackwardword"></a><span data-ttu-id="2ce29-513">ShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="2ce29-513">ShellBackwardWord</span></span>

<span data-ttu-id="2ce29-514">Ramener le curseur au début du mot actuel, ou si entre les mots, le début du mot précédent.</span><span class="sxs-lookup"><span data-stu-id="2ce29-514">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="2ce29-515">Les limites de mots sont définies par les jetons PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2ce29-515">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="2ce29-516">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="2ce29-516">Function is unbound.</span></span>

### <a name="shellforwardword"></a><span data-ttu-id="2ce29-517">ShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="2ce29-517">ShellForwardWord</span></span>

<span data-ttu-id="2ce29-518">Déplacer le curseur vers l’avant jusqu’au début du mot suivant.</span><span class="sxs-lookup"><span data-stu-id="2ce29-518">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="2ce29-519">Les limites de mots sont définies par les jetons PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2ce29-519">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="2ce29-520">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="2ce29-520">Function is unbound.</span></span>

### <a name="shellnextword"></a><span data-ttu-id="2ce29-521">ShellNextWord</span><span class="sxs-lookup"><span data-stu-id="2ce29-521">ShellNextWord</span></span>

<span data-ttu-id="2ce29-522">Déplacer le curseur vers l’avant jusqu’à la fin du mot actuel, ou si entre les mots, à la fin du mot suivant.</span><span class="sxs-lookup"><span data-stu-id="2ce29-522">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="2ce29-523">Les limites de mots sont définies par les jetons PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2ce29-523">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="2ce29-524">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="2ce29-524">Function is unbound.</span></span>

### <a name="vibackwardchar"></a><span data-ttu-id="2ce29-525">ViBackwardChar</span><span class="sxs-lookup"><span data-stu-id="2ce29-525">ViBackwardChar</span></span>

<span data-ttu-id="2ce29-526">Déplacer le curseur d’un caractère vers la gauche en mode d’édition VI.</span><span class="sxs-lookup"><span data-stu-id="2ce29-526">Move the cursor one character to the left in the Vi edit mode.</span></span> <span data-ttu-id="2ce29-527">Cela peut déplacer le curseur vers la ligne précédente de l’entrée multiligne.</span><span class="sxs-lookup"><span data-stu-id="2ce29-527">This may move the cursor to the previous line of multi-line input.</span></span>

- <span data-ttu-id="2ce29-528">Mode d’insertion VI : `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-528">Vi insert mode: `<LeftArrow>`</span></span>
- <span data-ttu-id="2ce29-529">Mode de commande VI : `<LeftArrow>` , `<Backspace>` , `<h>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-529">Vi command mode: `<LeftArrow>`, `<Backspace>`, `<h>`</span></span>

### <a name="vibackwardword"></a><span data-ttu-id="2ce29-530">ViBackwardWord</span><span class="sxs-lookup"><span data-stu-id="2ce29-530">ViBackwardWord</span></span>

<span data-ttu-id="2ce29-531">Ramener le curseur au début du mot actuel, ou si entre les mots, le début du mot précédent.</span><span class="sxs-lookup"><span data-stu-id="2ce29-531">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="2ce29-532">Les limites de mots sont définies par un jeu de caractères configurable.</span><span class="sxs-lookup"><span data-stu-id="2ce29-532">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="2ce29-533">Mode de commande VI : `<b>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-533">Vi command mode: `<b>`</span></span>

### <a name="viforwardchar"></a><span data-ttu-id="2ce29-534">ViForwardChar</span><span class="sxs-lookup"><span data-stu-id="2ce29-534">ViForwardChar</span></span>

<span data-ttu-id="2ce29-535">Déplacer le curseur d’un caractère vers la droite en mode d’édition VI.</span><span class="sxs-lookup"><span data-stu-id="2ce29-535">Move the cursor one character to the right in the Vi edit mode.</span></span> <span data-ttu-id="2ce29-536">Cela peut déplacer le curseur à la ligne suivante de l’entrée multiligne.</span><span class="sxs-lookup"><span data-stu-id="2ce29-536">This may move the cursor to the next line of multi-line input.</span></span>

- <span data-ttu-id="2ce29-537">Mode d’insertion VI : `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-537">Vi insert mode: `<RightArrow>`</span></span>
- <span data-ttu-id="2ce29-538">Mode de commande VI : `<RightArrow>` , `<Spacebar>` , `<l>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-538">Vi command mode: `<RightArrow>`, `<Spacebar>`, `<l>`</span></span>

### <a name="viendofglob"></a><span data-ttu-id="2ce29-539">ViEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="2ce29-539">ViEndOfGlob</span></span>

<span data-ttu-id="2ce29-540">Déplace le curseur à la fin du mot, en utilisant uniquement des espaces blancs comme délimiteurs.</span><span class="sxs-lookup"><span data-stu-id="2ce29-540">Moves the cursor to the end of the word, using only white space as delimiters.</span></span>

- <span data-ttu-id="2ce29-541">Mode de commande VI : `<E>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-541">Vi command mode: `<E>`</span></span>

### <a name="viendofpreviousglob"></a><span data-ttu-id="2ce29-542">ViEndOfPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="2ce29-542">ViEndOfPreviousGlob</span></span>

<span data-ttu-id="2ce29-543">Passe à la fin du mot précédent, en utilisant uniquement un espace blanc comme délimiteur de mot.</span><span class="sxs-lookup"><span data-stu-id="2ce29-543">Moves to the end of the previous word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="2ce29-544">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="2ce29-544">Function is unbound.</span></span>

### <a name="vigotobrace"></a><span data-ttu-id="2ce29-545">ViGotoBrace</span><span class="sxs-lookup"><span data-stu-id="2ce29-545">ViGotoBrace</span></span>

<span data-ttu-id="2ce29-546">Semblable à GotoBrace, mais est basé sur un caractère et non sur un jeton.</span><span class="sxs-lookup"><span data-stu-id="2ce29-546">Similar to GotoBrace, but is character based instead of token based.</span></span>

- <span data-ttu-id="2ce29-547">Mode de commande VI : `<%>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-547">Vi command mode: `<%>`</span></span>

### <a name="vinextglob"></a><span data-ttu-id="2ce29-548">ViNextGlob</span><span class="sxs-lookup"><span data-stu-id="2ce29-548">ViNextGlob</span></span>

<span data-ttu-id="2ce29-549">Passe au mot suivant, en utilisant uniquement un espace blanc comme délimiteur de mot.</span><span class="sxs-lookup"><span data-stu-id="2ce29-549">Moves to the next word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="2ce29-550">Mode de commande VI : `<W>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-550">Vi command mode: `<W>`</span></span>

### <a name="vinextword"></a><span data-ttu-id="2ce29-551">ViNextWord</span><span class="sxs-lookup"><span data-stu-id="2ce29-551">ViNextWord</span></span>

<span data-ttu-id="2ce29-552">Déplacer le curseur vers l’avant jusqu’au début du mot suivant.</span><span class="sxs-lookup"><span data-stu-id="2ce29-552">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="2ce29-553">Les limites de mots sont définies par un jeu de caractères configurable.</span><span class="sxs-lookup"><span data-stu-id="2ce29-553">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="2ce29-554">Mode de commande VI : `<w>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-554">Vi command mode: `<w>`</span></span>

## <a name="history-functions"></a><span data-ttu-id="2ce29-555">Fonctions d’historique</span><span class="sxs-lookup"><span data-stu-id="2ce29-555">History functions</span></span>

### <a name="beginningofhistory"></a><span data-ttu-id="2ce29-556">BeginningOfHistory</span><span class="sxs-lookup"><span data-stu-id="2ce29-556">BeginningOfHistory</span></span>

<span data-ttu-id="2ce29-557">Accéder au premier élément de l’historique.</span><span class="sxs-lookup"><span data-stu-id="2ce29-557">Move to the first item in the history.</span></span>

- <span data-ttu-id="2ce29-558">Emacs- `<Alt+<>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-558">Emacs: `<Alt+<>`</span></span>

### <a name="clearhistory"></a><span data-ttu-id="2ce29-559">ClearHistory</span><span class="sxs-lookup"><span data-stu-id="2ce29-559">ClearHistory</span></span>

<span data-ttu-id="2ce29-560">Efface l’historique dans PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="2ce29-560">Clears history in PSReadLine.</span></span> <span data-ttu-id="2ce29-561">Cela n’affecte pas l’historique PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2ce29-561">This does not affect PowerShell history.</span></span>

- <span data-ttu-id="2ce29-562">Cmd `<Alt+F7>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-562">Cmd: `<Alt+F7>`</span></span>

### <a name="endofhistory"></a><span data-ttu-id="2ce29-563">EndOfHistory</span><span class="sxs-lookup"><span data-stu-id="2ce29-563">EndOfHistory</span></span>

<span data-ttu-id="2ce29-564">Accéder au dernier élément (l’entrée en cours) dans l’historique.</span><span class="sxs-lookup"><span data-stu-id="2ce29-564">Move to the last item (the current input) in the history.</span></span>

- <span data-ttu-id="2ce29-565">Emacs- `<Alt+>>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-565">Emacs: `<Alt+>>`</span></span>

### <a name="forwardsearchhistory"></a><span data-ttu-id="2ce29-566">ForwardSearchHistory</span><span class="sxs-lookup"><span data-stu-id="2ce29-566">ForwardSearchHistory</span></span>

<span data-ttu-id="2ce29-567">Effectuer une recherche incrémentielle par progression dans l’historique.</span><span class="sxs-lookup"><span data-stu-id="2ce29-567">Perform an incremental forward search through history.</span></span>

- <span data-ttu-id="2ce29-568">Cmd `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-568">Cmd: `<Ctrl+s>`</span></span>
- <span data-ttu-id="2ce29-569">Emacs- `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-569">Emacs: `<Ctrl+s>`</span></span>

### <a name="historysearchbackward"></a><span data-ttu-id="2ce29-570">HistorySearchBackward</span><span class="sxs-lookup"><span data-stu-id="2ce29-570">HistorySearchBackward</span></span>

<span data-ttu-id="2ce29-571">Remplacez l’entrée actuelle par l’élément « Previous » de l’historique PSReadLine qui correspond aux caractères entre le début et l’entrée et le curseur.</span><span class="sxs-lookup"><span data-stu-id="2ce29-571">Replace the current input with the 'previous' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="2ce29-572">Cmd `<F8>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-572">Cmd: `<F8>`</span></span>

### <a name="historysearchforward"></a><span data-ttu-id="2ce29-573">HistorySearchForward</span><span class="sxs-lookup"><span data-stu-id="2ce29-573">HistorySearchForward</span></span>

<span data-ttu-id="2ce29-574">Remplacez l’entrée actuelle par l’élément « Next » de l’historique PSReadLine qui correspond aux caractères entre le début et l’entrée et le curseur.</span><span class="sxs-lookup"><span data-stu-id="2ce29-574">Replace the current input with the 'next' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="2ce29-575">Cmd `<Shift+F8>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-575">Cmd: `<Shift+F8>`</span></span>

### <a name="nexthistory"></a><span data-ttu-id="2ce29-576">NextHistory</span><span class="sxs-lookup"><span data-stu-id="2ce29-576">NextHistory</span></span>

<span data-ttu-id="2ce29-577">Remplacez l’entrée actuelle par l’élément « Next » de l’historique PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="2ce29-577">Replace the current input with the 'next' item from PSReadLine history.</span></span>

- <span data-ttu-id="2ce29-578">Cmd `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-578">Cmd: `<DownArrow>`</span></span>
- <span data-ttu-id="2ce29-579">Emacs- `<DownArrow>` , `<Ctrl+n>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-579">Emacs: `<DownArrow>`, `<Ctrl+n>`</span></span>
- <span data-ttu-id="2ce29-580">Mode d’insertion VI : `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-580">Vi insert mode: `<DownArrow>`</span></span>
- <span data-ttu-id="2ce29-581">Mode de commande VI : `<DownArrow>` , `<j>` , `<+>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-581">Vi command mode: `<DownArrow>`, `<j>`, `<+>`</span></span>

### <a name="previoushistory"></a><span data-ttu-id="2ce29-582">PreviousHistory</span><span class="sxs-lookup"><span data-stu-id="2ce29-582">PreviousHistory</span></span>

<span data-ttu-id="2ce29-583">Remplacez l’entrée actuelle par l’élément « Previous » de l’historique PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="2ce29-583">Replace the current input with the 'previous' item from PSReadLine history.</span></span>

- <span data-ttu-id="2ce29-584">Cmd `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-584">Cmd: `<UpArrow>`</span></span>
- <span data-ttu-id="2ce29-585">Emacs- `<UpArrow>` , `<Ctrl+p>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-585">Emacs: `<UpArrow>`, `<Ctrl+p>`</span></span>
- <span data-ttu-id="2ce29-586">Mode d’insertion VI : `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-586">Vi insert mode: `<UpArrow>`</span></span>
- <span data-ttu-id="2ce29-587">Mode de commande VI : `<UpArrow>` , `<k>` , `<->`</span><span class="sxs-lookup"><span data-stu-id="2ce29-587">Vi command mode: `<UpArrow>`, `<k>`, `<->`</span></span>

### <a name="reversesearchhistory"></a><span data-ttu-id="2ce29-588">ReverseSearchHistory</span><span class="sxs-lookup"><span data-stu-id="2ce29-588">ReverseSearchHistory</span></span>

<span data-ttu-id="2ce29-589">Effectuer une recherche incrémentielle incrémentielle dans l’historique.</span><span class="sxs-lookup"><span data-stu-id="2ce29-589">Perform an incremental backward search through history.</span></span>

- <span data-ttu-id="2ce29-590">Cmd `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-590">Cmd: `<Ctrl+r>`</span></span>
- <span data-ttu-id="2ce29-591">Emacs- `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-591">Emacs: `<Ctrl+r>`</span></span>

### <a name="visearchhistorybackward"></a><span data-ttu-id="2ce29-592">ViSearchHistoryBackward</span><span class="sxs-lookup"><span data-stu-id="2ce29-592">ViSearchHistoryBackward</span></span>

<span data-ttu-id="2ce29-593">Demande une chaîne de recherche et lance la recherche sur AcceptLine.</span><span class="sxs-lookup"><span data-stu-id="2ce29-593">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="2ce29-594">Mode d’insertion VI : `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-594">Vi insert mode: `<Ctrl+r>`</span></span>
- <span data-ttu-id="2ce29-595">Mode de commande VI : `</>` , `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-595">Vi command mode: `</>`, `<Ctrl+r>`</span></span>

## <a name="completion-functions"></a><span data-ttu-id="2ce29-596">Fonctions d’achèvement</span><span class="sxs-lookup"><span data-stu-id="2ce29-596">Completion functions</span></span>

### <a name="complete"></a><span data-ttu-id="2ce29-597">Terminé</span><span class="sxs-lookup"><span data-stu-id="2ce29-597">Complete</span></span>

<span data-ttu-id="2ce29-598">Tentative d’exécution de l’opération sur le texte entourant le curseur.</span><span class="sxs-lookup"><span data-stu-id="2ce29-598">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="2ce29-599">S’il existe plusieurs saisies semi-automatiques possibles, le plus long préfixe non ambigu est utilisé pour la finalisation.</span><span class="sxs-lookup"><span data-stu-id="2ce29-599">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="2ce29-600">Si vous essayez de terminer la saisie semi-automatique la plus longue, une liste des saisies semi-automatiques possibles s’affiche.</span><span class="sxs-lookup"><span data-stu-id="2ce29-600">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="2ce29-601">Emacs- `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-601">Emacs: `<Tab>`</span></span>

### <a name="menucomplete"></a><span data-ttu-id="2ce29-602">MenuComplete</span><span class="sxs-lookup"><span data-stu-id="2ce29-602">MenuComplete</span></span>

<span data-ttu-id="2ce29-603">Tentative d’exécution de l’opération sur le texte entourant le curseur.</span><span class="sxs-lookup"><span data-stu-id="2ce29-603">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="2ce29-604">S’il existe plusieurs saisies semi-automatiques possibles, le plus long préfixe non ambigu est utilisé pour la finalisation.</span><span class="sxs-lookup"><span data-stu-id="2ce29-604">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="2ce29-605">Si vous essayez de terminer la saisie semi-automatique la plus longue, une liste des saisies semi-automatiques possibles s’affiche.</span><span class="sxs-lookup"><span data-stu-id="2ce29-605">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="2ce29-606">Cmd : `<Ctrl+@>` , `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-606">Cmd: `<Ctrl+@>`, `<Ctrl+Spacebar>`</span></span>
- <span data-ttu-id="2ce29-607">Emacs- `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-607">Emacs: `<Ctrl+Spacebar>`</span></span>

### <a name="possiblecompletions"></a><span data-ttu-id="2ce29-608">PossibleCompletions</span><span class="sxs-lookup"><span data-stu-id="2ce29-608">PossibleCompletions</span></span>

<span data-ttu-id="2ce29-609">Affiche la liste des saisies semi-automatiques possibles.</span><span class="sxs-lookup"><span data-stu-id="2ce29-609">Display the list of possible completions.</span></span>

- <span data-ttu-id="2ce29-610">Emacs- `<Alt+=>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-610">Emacs: `<Alt+=>`</span></span>
- <span data-ttu-id="2ce29-611">Mode d’insertion VI : `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-611">Vi insert mode: `<Ctrl+Spacebar>`</span></span>
- <span data-ttu-id="2ce29-612">Mode de commande VI : `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-612">Vi command mode: `<Ctrl+Spacebar>`</span></span>

### <a name="tabcompletenext"></a><span data-ttu-id="2ce29-613">TabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="2ce29-613">TabCompleteNext</span></span>

<span data-ttu-id="2ce29-614">Tente de terminer le texte entourant le curseur avec la prochaine saisie semi-automatique disponible.</span><span class="sxs-lookup"><span data-stu-id="2ce29-614">Attempt to complete the text surrounding the cursor with the next available completion.</span></span>

- <span data-ttu-id="2ce29-615">Cmd `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-615">Cmd: `<Tab>`</span></span>
- <span data-ttu-id="2ce29-616">Mode de commande VI : `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-616">Vi command mode: `<Tab>`</span></span>

### <a name="tabcompleteprevious"></a><span data-ttu-id="2ce29-617">TabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="2ce29-617">TabCompletePrevious</span></span>

<span data-ttu-id="2ce29-618">Tente de terminer le texte entourant le curseur avec l’achèvement disponible précédent.</span><span class="sxs-lookup"><span data-stu-id="2ce29-618">Attempt to complete the text surrounding the cursor with the previous available completion.</span></span>

- <span data-ttu-id="2ce29-619">Cmd `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-619">Cmd: `<Shift+Tab>`</span></span>
- <span data-ttu-id="2ce29-620">Mode de commande VI : `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-620">Vi command mode: `<Shift+Tab>`</span></span>

### <a name="vitabcompletenext"></a><span data-ttu-id="2ce29-621">ViTabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="2ce29-621">ViTabCompleteNext</span></span>

<span data-ttu-id="2ce29-622">Met fin au groupe d’édition actuel, si nécessaire, et appelle TabCompleteNext.</span><span class="sxs-lookup"><span data-stu-id="2ce29-622">Ends the current edit group, if needed, and invokes TabCompleteNext.</span></span>

- <span data-ttu-id="2ce29-623">Mode d’insertion VI : `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-623">Vi insert mode: `<Tab>`</span></span>

### <a name="vitabcompleteprevious"></a><span data-ttu-id="2ce29-624">ViTabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="2ce29-624">ViTabCompletePrevious</span></span>

<span data-ttu-id="2ce29-625">Met fin au groupe d’édition actuel, si nécessaire, et appelle TabCompletePrevious.</span><span class="sxs-lookup"><span data-stu-id="2ce29-625">Ends the current edit group, if needed, and invokes TabCompletePrevious.</span></span>

- <span data-ttu-id="2ce29-626">Mode d’insertion VI : `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-626">Vi insert mode: `<Shift+Tab>`</span></span>

## <a name="miscellaneous-functions"></a><span data-ttu-id="2ce29-627">Fonctions diverses</span><span class="sxs-lookup"><span data-stu-id="2ce29-627">Miscellaneous functions</span></span>

### <a name="acceptnextsuggestionword"></a><span data-ttu-id="2ce29-628">AcceptNextSuggestionWord</span><span class="sxs-lookup"><span data-stu-id="2ce29-628">AcceptNextSuggestionWord</span></span>

<span data-ttu-id="2ce29-629">Accepter le mot suivant de la suggestion inline ou sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="2ce29-629">Accept the next word of the inline or selected suggestion.</span></span>

- <span data-ttu-id="2ce29-630">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="2ce29-630">Function is unbound.</span></span>

### <a name="acceptsuggestion"></a><span data-ttu-id="2ce29-631">AcceptSuggestion</span><span class="sxs-lookup"><span data-stu-id="2ce29-631">AcceptSuggestion</span></span>

<span data-ttu-id="2ce29-632">Acceptez la suggestion en ligne ou la suggestion sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="2ce29-632">Accept the current inline or selected suggestion.</span></span>

- <span data-ttu-id="2ce29-633">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="2ce29-633">Function is unbound.</span></span>

### <a name="capturescreen"></a><span data-ttu-id="2ce29-634">CaptureScreen</span><span class="sxs-lookup"><span data-stu-id="2ce29-634">CaptureScreen</span></span>

<span data-ttu-id="2ce29-635">Démarrer la capture d’écran interactive-flèches haut et bas sélectionnez lignes, entrez copie le texte sélectionné dans le presse-papiers en tant que texte et html.</span><span class="sxs-lookup"><span data-stu-id="2ce29-635">Start interactive screen capture - up/down arrows select lines, enter copies selected text to clipboard as text and html.</span></span>

- <span data-ttu-id="2ce29-636">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="2ce29-636">Function is unbound.</span></span>

### <a name="clearscreen"></a><span data-ttu-id="2ce29-637">ClearScreen</span><span class="sxs-lookup"><span data-stu-id="2ce29-637">ClearScreen</span></span>

<span data-ttu-id="2ce29-638">Effacez l’écran et dessinez la ligne active en haut de l’écran.</span><span class="sxs-lookup"><span data-stu-id="2ce29-638">Clear the screen and draw the current line at the top of the screen.</span></span>

- <span data-ttu-id="2ce29-639">Cmd `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-639">Cmd: `<Ctrl+l>`</span></span>
- <span data-ttu-id="2ce29-640">Emacs- `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-640">Emacs: `<Ctrl+l>`</span></span>
- <span data-ttu-id="2ce29-641">Mode d’insertion VI : `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-641">Vi insert mode: `<Ctrl+l>`</span></span>
- <span data-ttu-id="2ce29-642">Mode de commande VI : `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-642">Vi command mode: `<Ctrl+l>`</span></span>

### <a name="digitargument"></a><span data-ttu-id="2ce29-643">DigitArgument</span><span class="sxs-lookup"><span data-stu-id="2ce29-643">DigitArgument</span></span>

<span data-ttu-id="2ce29-644">Démarrez un nouvel argument digit à passer à d’autres fonctions.</span><span class="sxs-lookup"><span data-stu-id="2ce29-644">Start a new digit argument to pass to other functions.</span></span>

- <span data-ttu-id="2ce29-645">Cmd : `<Alt+0>` ,,,,, `<Alt+1>` `<Alt+2>` `<Alt+3>` `<Alt+4>` `<Alt+5>` , `<Alt+6>` , `<Alt+7>` , `<Alt+8>` , `<Alt+9>` , `<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="2ce29-645">Cmd: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="2ce29-646">Emacs-,,,,,,,,, `<Alt+0>` `<Alt+1>` `<Alt+2>` `<Alt+3>` `<Alt+4>` `<Alt+5>` `<Alt+6>` `<Alt+7>` `<Alt+8>` , `<Alt+9>` , `<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="2ce29-646">Emacs: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="2ce29-647">Mode de commande VI : `<0>` , `<1>` ,, `<2>` `<3>` , `<4>` , `<5>` , `<6>` , `<7>` , `<8>` , `<9>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-647">Vi command mode: `<0>`, `<1>`, `<2>`, `<3>`, `<4>`, `<5>`, `<6>`, `<7>`, `<8>`, `<9>`</span></span>

### <a name="invokeprompt"></a><span data-ttu-id="2ce29-648">InvokePrompt</span><span class="sxs-lookup"><span data-stu-id="2ce29-648">InvokePrompt</span></span>

<span data-ttu-id="2ce29-649">Efface l’invite en cours et appelle la fonction prompt pour réafficher l’invite.</span><span class="sxs-lookup"><span data-stu-id="2ce29-649">Erases the current prompt and calls the prompt function to redisplay the prompt.</span></span> <span data-ttu-id="2ce29-650">Utile pour les gestionnaires de clés personnalisés qui changent d’État, par exemple modifier le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="2ce29-650">Useful for custom key handlers that change state, e.g. change the current directory.</span></span>

- <span data-ttu-id="2ce29-651">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="2ce29-651">Function is unbound.</span></span>

### <a name="scrolldisplaydown"></a><span data-ttu-id="2ce29-652">ScrollDisplayDown</span><span class="sxs-lookup"><span data-stu-id="2ce29-652">ScrollDisplayDown</span></span>

<span data-ttu-id="2ce29-653">Faites défiler l’écran vers le volet d’affichage.</span><span class="sxs-lookup"><span data-stu-id="2ce29-653">Scroll the display down one screen.</span></span>

- <span data-ttu-id="2ce29-654">Cmd `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-654">Cmd: `<PageDown>`</span></span>
- <span data-ttu-id="2ce29-655">Emacs- `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-655">Emacs: `<PageDown>`</span></span>

### <a name="scrolldisplaydownline"></a><span data-ttu-id="2ce29-656">ScrollDisplayDownLine</span><span class="sxs-lookup"><span data-stu-id="2ce29-656">ScrollDisplayDownLine</span></span>

<span data-ttu-id="2ce29-657">Faites défiler l’affichage d’une ligne vers le dessous.</span><span class="sxs-lookup"><span data-stu-id="2ce29-657">Scroll the display down one line.</span></span>

- <span data-ttu-id="2ce29-658">Cmd `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-658">Cmd: `<Ctrl+PageDown>`</span></span>
- <span data-ttu-id="2ce29-659">Emacs- `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-659">Emacs: `<Ctrl+PageDown>`</span></span>

### <a name="scrolldisplaytocursor"></a><span data-ttu-id="2ce29-660">ScrollDisplayToCursor</span><span class="sxs-lookup"><span data-stu-id="2ce29-660">ScrollDisplayToCursor</span></span>

<span data-ttu-id="2ce29-661">Faites défiler l’affichage jusqu’au curseur.</span><span class="sxs-lookup"><span data-stu-id="2ce29-661">Scroll the display to the cursor.</span></span>

- <span data-ttu-id="2ce29-662">Emacs- `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-662">Emacs: `<Ctrl+End>`</span></span>

### <a name="scrolldisplaytop"></a><span data-ttu-id="2ce29-663">ScrollDisplayTop</span><span class="sxs-lookup"><span data-stu-id="2ce29-663">ScrollDisplayTop</span></span>

<span data-ttu-id="2ce29-664">Faites défiler l’affichage vers le haut.</span><span class="sxs-lookup"><span data-stu-id="2ce29-664">Scroll the display to the top.</span></span>

- <span data-ttu-id="2ce29-665">Emacs- `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-665">Emacs: `<Ctrl+Home>`</span></span>

### <a name="scrolldisplayup"></a><span data-ttu-id="2ce29-666">ScrollDisplayUp</span><span class="sxs-lookup"><span data-stu-id="2ce29-666">ScrollDisplayUp</span></span>

<span data-ttu-id="2ce29-667">Faites défiler l’écran afficher vers le haut.</span><span class="sxs-lookup"><span data-stu-id="2ce29-667">Scroll the display up one screen.</span></span>

- <span data-ttu-id="2ce29-668">Cmd `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-668">Cmd: `<PageUp>`</span></span>
- <span data-ttu-id="2ce29-669">Emacs- `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-669">Emacs: `<PageUp>`</span></span>

### <a name="scrolldisplayupline"></a><span data-ttu-id="2ce29-670">ScrollDisplayUpLine</span><span class="sxs-lookup"><span data-stu-id="2ce29-670">ScrollDisplayUpLine</span></span>

<span data-ttu-id="2ce29-671">Faites défiler l’affichage d’une ligne vers le haut.</span><span class="sxs-lookup"><span data-stu-id="2ce29-671">Scroll the display up one line.</span></span>

- <span data-ttu-id="2ce29-672">Cmd `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-672">Cmd: `<Ctrl+PageUp>`</span></span>
- <span data-ttu-id="2ce29-673">Emacs- `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-673">Emacs: `<Ctrl+PageUp>`</span></span>

### <a name="selfinsert"></a><span data-ttu-id="2ce29-674">SelfInsert</span><span class="sxs-lookup"><span data-stu-id="2ce29-674">SelfInsert</span></span>

<span data-ttu-id="2ce29-675">Insérez la clé.</span><span class="sxs-lookup"><span data-stu-id="2ce29-675">Insert the key.</span></span>

- <span data-ttu-id="2ce29-676">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="2ce29-676">Function is unbound.</span></span>

### <a name="showkeybindings"></a><span data-ttu-id="2ce29-677">ShowKeyBindings</span><span class="sxs-lookup"><span data-stu-id="2ce29-677">ShowKeyBindings</span></span>

<span data-ttu-id="2ce29-678">Affiche toutes les clés liées.</span><span class="sxs-lookup"><span data-stu-id="2ce29-678">Show all bound keys.</span></span>

- <span data-ttu-id="2ce29-679">Cmd `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-679">Cmd: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="2ce29-680">Emacs- `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-680">Emacs: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="2ce29-681">Mode d’insertion VI : `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-681">Vi insert mode: `<Ctrl+Alt+?>`</span></span>

### <a name="vicommandmode"></a><span data-ttu-id="2ce29-682">ViCommandMode</span><span class="sxs-lookup"><span data-stu-id="2ce29-682">ViCommandMode</span></span>

<span data-ttu-id="2ce29-683">Basculez le mode d’opération actuel de Vi-Insert à VI-Command.</span><span class="sxs-lookup"><span data-stu-id="2ce29-683">Switch the current operating mode from Vi-Insert to Vi-Command.</span></span>

- <span data-ttu-id="2ce29-684">Mode d’insertion VI : `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-684">Vi insert mode: `<Escape>`</span></span>

### <a name="vidigitargumentinchord"></a><span data-ttu-id="2ce29-685">ViDigitArgumentInChord</span><span class="sxs-lookup"><span data-stu-id="2ce29-685">ViDigitArgumentInChord</span></span>

<span data-ttu-id="2ce29-686">Démarrez un nouvel argument digit à passer à d’autres fonctions dans l’un des cordes de VI.</span><span class="sxs-lookup"><span data-stu-id="2ce29-686">Start a new digit argument to pass to other functions while in one of vi's chords.</span></span>

- <span data-ttu-id="2ce29-687">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="2ce29-687">Function is unbound.</span></span>

### <a name="vieditvisually"></a><span data-ttu-id="2ce29-688">ViEditVisually</span><span class="sxs-lookup"><span data-stu-id="2ce29-688">ViEditVisually</span></span>

<span data-ttu-id="2ce29-689">Modifiez la ligne de commande dans un éditeur de texte spécifié par $env : EDITOR ou $env : VISUAL.</span><span class="sxs-lookup"><span data-stu-id="2ce29-689">Edit the command line in a text editor specified by $env:EDITOR or $env:VISUAL.</span></span>

- <span data-ttu-id="2ce29-690">Emacs- `<Ctrl+x,Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-690">Emacs: `<Ctrl+x,Ctrl+e>`</span></span>
- <span data-ttu-id="2ce29-691">Mode de commande VI : `<v>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-691">Vi command mode: `<v>`</span></span>

### <a name="viexit"></a><span data-ttu-id="2ce29-692">ViExit</span><span class="sxs-lookup"><span data-stu-id="2ce29-692">ViExit</span></span>

<span data-ttu-id="2ce29-693">Quitte l’interpréteur de commandes.</span><span class="sxs-lookup"><span data-stu-id="2ce29-693">Exits the shell.</span></span>

- <span data-ttu-id="2ce29-694">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="2ce29-694">Function is unbound.</span></span>

### <a name="viinsertmode"></a><span data-ttu-id="2ce29-695">ViInsertMode</span><span class="sxs-lookup"><span data-stu-id="2ce29-695">ViInsertMode</span></span>

<span data-ttu-id="2ce29-696">Basculez en mode insertion.</span><span class="sxs-lookup"><span data-stu-id="2ce29-696">Switch to Insert mode.</span></span>

- <span data-ttu-id="2ce29-697">Mode de commande VI : `<i>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-697">Vi command mode: `<i>`</span></span>

### <a name="whatiskey"></a><span data-ttu-id="2ce29-698">WhatIsKey</span><span class="sxs-lookup"><span data-stu-id="2ce29-698">WhatIsKey</span></span>

<span data-ttu-id="2ce29-699">Lisez une clé et dites-moi à quoi la clé est liée.</span><span class="sxs-lookup"><span data-stu-id="2ce29-699">Read a key and tell me what the key is bound to.</span></span>

- <span data-ttu-id="2ce29-700">Cmd `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-700">Cmd: `<Alt+?>`</span></span>
- <span data-ttu-id="2ce29-701">Emacs- `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-701">Emacs: `<Alt+?>`</span></span>

## <a name="selection-functions"></a><span data-ttu-id="2ce29-702">Fonctions de sélection</span><span class="sxs-lookup"><span data-stu-id="2ce29-702">Selection functions</span></span>

### <a name="exchangepointandmark"></a><span data-ttu-id="2ce29-703">ExchangePointAndMark</span><span class="sxs-lookup"><span data-stu-id="2ce29-703">ExchangePointAndMark</span></span>

<span data-ttu-id="2ce29-704">Le curseur est placé à l’emplacement de la marque et la marque est déplacée vers l’emplacement du curseur.</span><span class="sxs-lookup"><span data-stu-id="2ce29-704">The cursor is placed at the location of the mark and the mark is moved to the location of the cursor.</span></span>

- <span data-ttu-id="2ce29-705">Emacs- `<Ctrl+x,Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-705">Emacs: `<Ctrl+x,Ctrl+x>`</span></span>

### <a name="selectall"></a><span data-ttu-id="2ce29-706">SelectAll</span><span class="sxs-lookup"><span data-stu-id="2ce29-706">SelectAll</span></span>

<span data-ttu-id="2ce29-707">Sélectionnez la ligne entière.</span><span class="sxs-lookup"><span data-stu-id="2ce29-707">Select the entire line.</span></span>

- <span data-ttu-id="2ce29-708">Cmd `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-708">Cmd: `<Ctrl+a>`</span></span>

### <a name="selectbackwardchar"></a><span data-ttu-id="2ce29-709">SelectBackwardChar</span><span class="sxs-lookup"><span data-stu-id="2ce29-709">SelectBackwardChar</span></span>

<span data-ttu-id="2ce29-710">Ajustez la sélection actuelle pour inclure le caractère précédent.</span><span class="sxs-lookup"><span data-stu-id="2ce29-710">Adjust the current selection to include the previous character.</span></span>

- <span data-ttu-id="2ce29-711">Cmd `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-711">Cmd: `<Shift+LeftArrow>`</span></span>
- <span data-ttu-id="2ce29-712">Emacs- `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-712">Emacs: `<Shift+LeftArrow>`</span></span>

### <a name="selectbackwardsline"></a><span data-ttu-id="2ce29-713">SelectBackwardsLine</span><span class="sxs-lookup"><span data-stu-id="2ce29-713">SelectBackwardsLine</span></span>

<span data-ttu-id="2ce29-714">Ajustez la sélection actuelle à inclure à partir du curseur jusqu’au début de la ligne.</span><span class="sxs-lookup"><span data-stu-id="2ce29-714">Adjust the current selection to include from the cursor to the start of the line.</span></span>

- <span data-ttu-id="2ce29-715">Cmd `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-715">Cmd: `<Shift+Home>`</span></span>
- <span data-ttu-id="2ce29-716">Emacs- `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-716">Emacs: `<Shift+Home>`</span></span>

### <a name="selectbackwardword"></a><span data-ttu-id="2ce29-717">SelectBackwardWord</span><span class="sxs-lookup"><span data-stu-id="2ce29-717">SelectBackwardWord</span></span>

<span data-ttu-id="2ce29-718">Ajustez la sélection actuelle pour inclure le mot précédent.</span><span class="sxs-lookup"><span data-stu-id="2ce29-718">Adjust the current selection to include the previous word.</span></span>

- <span data-ttu-id="2ce29-719">Cmd `<Shift+Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-719">Cmd: `<Shift+Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="2ce29-720">Emacs- `<Alt+B>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-720">Emacs: `<Alt+B>`</span></span>

### <a name="selectforwardchar"></a><span data-ttu-id="2ce29-721">SelectForwardChar</span><span class="sxs-lookup"><span data-stu-id="2ce29-721">SelectForwardChar</span></span>

<span data-ttu-id="2ce29-722">Ajustez la sélection actuelle pour inclure le caractère suivant.</span><span class="sxs-lookup"><span data-stu-id="2ce29-722">Adjust the current selection to include the next character.</span></span>

- <span data-ttu-id="2ce29-723">Cmd `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-723">Cmd: `<Shift+RightArrow>`</span></span>
- <span data-ttu-id="2ce29-724">Emacs- `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-724">Emacs: `<Shift+RightArrow>`</span></span>

### <a name="selectforwardword"></a><span data-ttu-id="2ce29-725">SelectForwardWord</span><span class="sxs-lookup"><span data-stu-id="2ce29-725">SelectForwardWord</span></span>

<span data-ttu-id="2ce29-726">Ajustez la sélection actuelle pour inclure le mot suivant à l’aide de ForwardWord.</span><span class="sxs-lookup"><span data-stu-id="2ce29-726">Adjust the current selection to include the next word using ForwardWord.</span></span>

- <span data-ttu-id="2ce29-727">Emacs- `<Alt+F>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-727">Emacs: `<Alt+F>`</span></span>

### <a name="selectline"></a><span data-ttu-id="2ce29-728">SelectLine</span><span class="sxs-lookup"><span data-stu-id="2ce29-728">SelectLine</span></span>

<span data-ttu-id="2ce29-729">Ajustez la sélection actuelle à inclure à partir du curseur jusqu’à la fin de la ligne.</span><span class="sxs-lookup"><span data-stu-id="2ce29-729">Adjust the current selection to include from the cursor to the end of the line.</span></span>

- <span data-ttu-id="2ce29-730">Cmd `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-730">Cmd: `<Shift+End>`</span></span>
- <span data-ttu-id="2ce29-731">Emacs- `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-731">Emacs: `<Shift+End>`</span></span>

### <a name="selectnextword"></a><span data-ttu-id="2ce29-732">SelectNextWord</span><span class="sxs-lookup"><span data-stu-id="2ce29-732">SelectNextWord</span></span>

<span data-ttu-id="2ce29-733">Ajustez la sélection actuelle pour inclure le mot suivant.</span><span class="sxs-lookup"><span data-stu-id="2ce29-733">Adjust the current selection to include the next word.</span></span>

- <span data-ttu-id="2ce29-734">Cmd `<Shift+Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-734">Cmd: `<Shift+Ctrl+RightArrow>`</span></span>

### <a name="selectshellbackwardword"></a><span data-ttu-id="2ce29-735">SelectShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="2ce29-735">SelectShellBackwardWord</span></span>

<span data-ttu-id="2ce29-736">Ajustez la sélection actuelle pour inclure le mot précédent à l’aide de ShellBackwardWord.</span><span class="sxs-lookup"><span data-stu-id="2ce29-736">Adjust the current selection to include the previous word using ShellBackwardWord.</span></span>

- <span data-ttu-id="2ce29-737">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="2ce29-737">Function is unbound.</span></span>

### <a name="selectshellforwardword"></a><span data-ttu-id="2ce29-738">SelectShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="2ce29-738">SelectShellForwardWord</span></span>

<span data-ttu-id="2ce29-739">Ajustez la sélection actuelle pour inclure le mot suivant à l’aide de ShellForwardWord.</span><span class="sxs-lookup"><span data-stu-id="2ce29-739">Adjust the current selection to include the next word using ShellForwardWord.</span></span>

- <span data-ttu-id="2ce29-740">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="2ce29-740">Function is unbound.</span></span>

### <a name="selectshellnextword"></a><span data-ttu-id="2ce29-741">SelectShellNextWord</span><span class="sxs-lookup"><span data-stu-id="2ce29-741">SelectShellNextWord</span></span>

<span data-ttu-id="2ce29-742">Ajustez la sélection actuelle pour inclure le mot suivant à l’aide de ShellNextWord.</span><span class="sxs-lookup"><span data-stu-id="2ce29-742">Adjust the current selection to include the next word using ShellNextWord.</span></span>

- <span data-ttu-id="2ce29-743">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="2ce29-743">Function is unbound.</span></span>

### <a name="setmark"></a><span data-ttu-id="2ce29-744">SetMark</span><span class="sxs-lookup"><span data-stu-id="2ce29-744">SetMark</span></span>

<span data-ttu-id="2ce29-745">Marquez l’emplacement actuel du curseur pour une utilisation dans une commande d’édition suivante.</span><span class="sxs-lookup"><span data-stu-id="2ce29-745">Mark the current location of the cursor for use in a subsequent editing command.</span></span>

- <span data-ttu-id="2ce29-746">Emacs- `<Ctrl+@>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-746">Emacs: `<Ctrl+@>`</span></span>

## <a name="search-functions"></a><span data-ttu-id="2ce29-747">Fonctions de recherche</span><span class="sxs-lookup"><span data-stu-id="2ce29-747">Search functions</span></span>

### <a name="charactersearch"></a><span data-ttu-id="2ce29-748">CharacterSearch</span><span class="sxs-lookup"><span data-stu-id="2ce29-748">CharacterSearch</span></span>

<span data-ttu-id="2ce29-749">Lisez un caractère et recherchez l’occurrence suivante de ce caractère.</span><span class="sxs-lookup"><span data-stu-id="2ce29-749">Read a character and search forward for the next occurrence of that character.</span></span>
<span data-ttu-id="2ce29-750">Si un argument est spécifié, effectuez une recherche vers l’avant (ou vers l’arrière si négatif) pour la nième occurrence.</span><span class="sxs-lookup"><span data-stu-id="2ce29-750">If an argument is specified, search forward (or backward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="2ce29-751">Cmd `<F3>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-751">Cmd: `<F3>`</span></span>
- <span data-ttu-id="2ce29-752">Emacs- `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-752">Emacs: `<Ctrl+]>`</span></span>
- <span data-ttu-id="2ce29-753">Mode d’insertion VI : `<F3>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-753">Vi insert mode: `<F3>`</span></span>
- <span data-ttu-id="2ce29-754">Mode de commande VI : `<F3>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-754">Vi command mode: `<F3>`</span></span>

### <a name="charactersearchbackward"></a><span data-ttu-id="2ce29-755">CharacterSearchBackward</span><span class="sxs-lookup"><span data-stu-id="2ce29-755">CharacterSearchBackward</span></span>

<span data-ttu-id="2ce29-756">Lisez un caractère et recherchez l’occurrence suivante de ce caractère.</span><span class="sxs-lookup"><span data-stu-id="2ce29-756">Read a character and search backward for the next occurrence of that character.</span></span> <span data-ttu-id="2ce29-757">Si un argument est spécifié, effectuez une recherche vers l’arrière (ou vers l’avant si négatif) pour la nième occurrence.</span><span class="sxs-lookup"><span data-stu-id="2ce29-757">If an argument is specified, search backward (or forward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="2ce29-758">Cmd `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-758">Cmd: `<Shift+F3>`</span></span>
- <span data-ttu-id="2ce29-759">Emacs- `<Ctrl+Alt+]>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-759">Emacs: `<Ctrl+Alt+]>`</span></span>
- <span data-ttu-id="2ce29-760">Mode d’insertion VI : `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-760">Vi insert mode: `<Shift+F3>`</span></span>
- <span data-ttu-id="2ce29-761">Mode de commande VI : `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-761">Vi command mode: `<Shift+F3>`</span></span>

### <a name="repeatlastcharsearch"></a><span data-ttu-id="2ce29-762">RepeatLastCharSearch</span><span class="sxs-lookup"><span data-stu-id="2ce29-762">RepeatLastCharSearch</span></span>

<span data-ttu-id="2ce29-763">Répète la dernière recherche de caractères enregistrée.</span><span class="sxs-lookup"><span data-stu-id="2ce29-763">Repeat the last recorded character search.</span></span>

- <span data-ttu-id="2ce29-764">Mode de commande VI : `<;>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-764">Vi command mode: `<;>`</span></span>

### <a name="repeatlastcharsearchbackwards"></a><span data-ttu-id="2ce29-765">RepeatLastCharSearchBackwards</span><span class="sxs-lookup"><span data-stu-id="2ce29-765">RepeatLastCharSearchBackwards</span></span>

<span data-ttu-id="2ce29-766">Répète la dernière recherche de caractères enregistrée, mais dans la direction opposée.</span><span class="sxs-lookup"><span data-stu-id="2ce29-766">Repeat the last recorded character search, but in the opposite direction.</span></span>

- <span data-ttu-id="2ce29-767">Mode de commande VI : `<,>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-767">Vi command mode: `<,>`</span></span>

### <a name="repeatsearch"></a><span data-ttu-id="2ce29-768">RepeatSearch</span><span class="sxs-lookup"><span data-stu-id="2ce29-768">RepeatSearch</span></span>

<span data-ttu-id="2ce29-769">Répétez la dernière recherche dans la même direction que précédemment.</span><span class="sxs-lookup"><span data-stu-id="2ce29-769">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="2ce29-770">Mode de commande VI : `<n>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-770">Vi command mode: `<n>`</span></span>

### <a name="repeatsearchbackward"></a><span data-ttu-id="2ce29-771">RepeatSearchBackward</span><span class="sxs-lookup"><span data-stu-id="2ce29-771">RepeatSearchBackward</span></span>

<span data-ttu-id="2ce29-772">Répétez la dernière recherche dans la même direction que précédemment.</span><span class="sxs-lookup"><span data-stu-id="2ce29-772">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="2ce29-773">Mode de commande VI : `<N>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-773">Vi command mode: `<N>`</span></span>

### <a name="searchchar"></a><span data-ttu-id="2ce29-774">SearchChar</span><span class="sxs-lookup"><span data-stu-id="2ce29-774">SearchChar</span></span>

<span data-ttu-id="2ce29-775">Lisez le caractère suivant, puis recherchez-le, à l’avenir, puis annulez un caractère.</span><span class="sxs-lookup"><span data-stu-id="2ce29-775">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="2ce29-776">Il s’agit de la fonctionnalité’t'.</span><span class="sxs-lookup"><span data-stu-id="2ce29-776">This is for 't' functionality.</span></span>

- <span data-ttu-id="2ce29-777">Mode de commande VI : `<f>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-777">Vi command mode: `<f>`</span></span>

### <a name="searchcharbackward"></a><span data-ttu-id="2ce29-778">SearchCharBackward</span><span class="sxs-lookup"><span data-stu-id="2ce29-778">SearchCharBackward</span></span>

<span data-ttu-id="2ce29-779">Lisez le caractère suivant, puis recherchez-le, en accédant à l’arrière, puis en annulant un caractère.</span><span class="sxs-lookup"><span data-stu-id="2ce29-779">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="2ce29-780">Il s’agit de la fonctionnalité’t'.</span><span class="sxs-lookup"><span data-stu-id="2ce29-780">This is for 'T' functionality.</span></span>

- <span data-ttu-id="2ce29-781">Mode de commande VI : `<F>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-781">Vi command mode: `<F>`</span></span>

### <a name="searchcharbackwardwithbackoff"></a><span data-ttu-id="2ce29-782">SearchCharBackwardWithBackoff</span><span class="sxs-lookup"><span data-stu-id="2ce29-782">SearchCharBackwardWithBackoff</span></span>

<span data-ttu-id="2ce29-783">Lisez le caractère suivant, puis recherchez-le, en accédant à l’arrière, puis en annulant un caractère.</span><span class="sxs-lookup"><span data-stu-id="2ce29-783">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="2ce29-784">Il s’agit de la fonctionnalité’t'.</span><span class="sxs-lookup"><span data-stu-id="2ce29-784">This is for 'T' functionality.</span></span>

- <span data-ttu-id="2ce29-785">Mode de commande VI : `<T>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-785">Vi command mode: `<T>`</span></span>

### <a name="searchcharwithbackoff"></a><span data-ttu-id="2ce29-786">SearchCharWithBackoff</span><span class="sxs-lookup"><span data-stu-id="2ce29-786">SearchCharWithBackoff</span></span>

<span data-ttu-id="2ce29-787">Lisez le caractère suivant, puis recherchez-le, à l’avenir, puis annulez un caractère.</span><span class="sxs-lookup"><span data-stu-id="2ce29-787">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="2ce29-788">Il s’agit de la fonctionnalité’t'.</span><span class="sxs-lookup"><span data-stu-id="2ce29-788">This is for 't' functionality.</span></span>

- <span data-ttu-id="2ce29-789">Mode de commande VI : `<t>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-789">Vi command mode: `<t>`</span></span>

### <a name="searchforward"></a><span data-ttu-id="2ce29-790">SearchForward</span><span class="sxs-lookup"><span data-stu-id="2ce29-790">SearchForward</span></span>

<span data-ttu-id="2ce29-791">Demande une chaîne de recherche et lance la recherche sur AcceptLine.</span><span class="sxs-lookup"><span data-stu-id="2ce29-791">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="2ce29-792">Mode d’insertion VI : `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-792">Vi insert mode: `<Ctrl+s>`</span></span>
- <span data-ttu-id="2ce29-793">Mode de commande VI : `<?>` , `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="2ce29-793">Vi command mode: `<?>`, `<Ctrl+s>`</span></span>

## <a name="custom-key-bindings"></a><span data-ttu-id="2ce29-794">Combinaisons de touches personnalisées</span><span class="sxs-lookup"><span data-stu-id="2ce29-794">Custom Key Bindings</span></span>

<span data-ttu-id="2ce29-795">PSReadLine prend en charge les combinaisons de touches personnalisées à l’aide de l’applet de commande `Set-PSReadLineKeyHandler` .</span><span class="sxs-lookup"><span data-stu-id="2ce29-795">PSReadLine supports custom key bindings using the cmdlet `Set-PSReadLineKeyHandler`.</span></span> <span data-ttu-id="2ce29-796">La plupart des combinaisons de touches personnalisées appellent l’une des fonctions ci-dessus, par exemple</span><span class="sxs-lookup"><span data-stu-id="2ce29-796">Most custom key bindings call one of the above functions, for example</span></span>

```powershell
Set-PSReadLineKeyHandler -Key UpArrow -Function HistorySearchBackward
```

<span data-ttu-id="2ce29-797">Vous pouvez lier un ScriptBlock à une clé.</span><span class="sxs-lookup"><span data-stu-id="2ce29-797">You can bind a ScriptBlock to a key.</span></span> <span data-ttu-id="2ce29-798">Le ScriptBlock peut faire à peu près tout ce que vous voulez.</span><span class="sxs-lookup"><span data-stu-id="2ce29-798">The ScriptBlock can do pretty much anything you want.</span></span> <span data-ttu-id="2ce29-799">Voici quelques exemples utiles :</span><span class="sxs-lookup"><span data-stu-id="2ce29-799">Some useful examples include</span></span>

- <span data-ttu-id="2ce29-800">modifier la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="2ce29-800">edit the command line</span></span>
- <span data-ttu-id="2ce29-801">ouverture d’une nouvelle fenêtre (par exemple, aide)</span><span class="sxs-lookup"><span data-stu-id="2ce29-801">opening a new window (e.g. help)</span></span>
- <span data-ttu-id="2ce29-802">modifier les répertoires sans modifier la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="2ce29-802">change directories without changing the command line</span></span>

<span data-ttu-id="2ce29-803">Le ScriptBlock reçoit deux arguments :</span><span class="sxs-lookup"><span data-stu-id="2ce29-803">The ScriptBlock receives two arguments:</span></span>

- <span data-ttu-id="2ce29-804">`$key` -Objet **[ConsoleKeyInfo]** qui est la clé qui a déclenché la liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="2ce29-804">`$key` - A **[ConsoleKeyInfo]** object that is the key that triggered the custom binding.</span></span> <span data-ttu-id="2ce29-805">Si vous liez le même ScriptBlock à plusieurs clés et que vous devez effectuer des actions différentes en fonction de la clé, vous pouvez vérifier $key.</span><span class="sxs-lookup"><span data-stu-id="2ce29-805">If you bind the same ScriptBlock to multiple keys and need to perform different actions depending on the key, you can check $key.</span></span> <span data-ttu-id="2ce29-806">De nombreuses liaisons personnalisées ignorent cet argument.</span><span class="sxs-lookup"><span data-stu-id="2ce29-806">Many custom bindings ignore this argument.</span></span>

- <span data-ttu-id="2ce29-807">`$arg` : Argument arbitraire.</span><span class="sxs-lookup"><span data-stu-id="2ce29-807">`$arg` - An arbitrary argument.</span></span> <span data-ttu-id="2ce29-808">Le plus souvent, il s’agit d’un argument entier que l’utilisateur passe à partir des combinaisons de touches DigitArgument.</span><span class="sxs-lookup"><span data-stu-id="2ce29-808">Most often, this would be an integer argument that the user passes from the key bindings DigitArgument.</span></span> <span data-ttu-id="2ce29-809">Si votre liaison n’accepte pas d’arguments, il est raisonnable d’ignorer cet argument.</span><span class="sxs-lookup"><span data-stu-id="2ce29-809">If your binding doesn't accept arguments, it's reasonable to ignore this argument.</span></span>

<span data-ttu-id="2ce29-810">Jetons un coup d’œil à un exemple qui ajoute une ligne de commande à l’historique sans l’exécuter.</span><span class="sxs-lookup"><span data-stu-id="2ce29-810">Let's take a look at an example that adds a command line to history without executing it.</span></span> <span data-ttu-id="2ce29-811">Cela est utile lorsque vous vous rendez compte que vous avez oublié d’effectuer une opération, mais que vous ne voulez pas entrer à nouveau la ligne de commande que vous avez déjà entrée.</span><span class="sxs-lookup"><span data-stu-id="2ce29-811">This is useful when you realize you forgot to do something, but don't want to re-enter the command line you've already entered.</span></span>

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

<span data-ttu-id="2ce29-812">Vous pouvez voir beaucoup plus d’exemples dans le fichier `SamplePSReadLineProfile.ps1` qui est installé dans le dossier du module PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="2ce29-812">You can see many more examples in the file `SamplePSReadLineProfile.ps1` which is installed in the PSReadLine module folder.</span></span>

<span data-ttu-id="2ce29-813">La plupart des combinaisons de touches utilisent des fonctions d’assistance pour la modification de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="2ce29-813">Most key bindings use some helper functions for editing the command line.</span></span>
<span data-ttu-id="2ce29-814">Ces API sont documentées dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="2ce29-814">Those APIs are documented in the next section.</span></span>

## <a name="custom-key-binding-support-apis"></a><span data-ttu-id="2ce29-815">API de prise en charge de la liaison de clé personnalisée</span><span class="sxs-lookup"><span data-stu-id="2ce29-815">Custom Key Binding Support APIs</span></span>

<span data-ttu-id="2ce29-816">Les fonctions suivantes sont publiques dans Microsoft. PowerShell. PSConsoleReadLine, mais ne peuvent pas être directement liées à une clé.</span><span class="sxs-lookup"><span data-stu-id="2ce29-816">The following functions are public in Microsoft.PowerShell.PSConsoleReadLine, but cannot be directly bound to a key.</span></span> <span data-ttu-id="2ce29-817">La plupart sont utiles dans les combinaisons de touches personnalisées.</span><span class="sxs-lookup"><span data-stu-id="2ce29-817">Most are useful in custom key bindings.</span></span>

```csharp
void AddToHistory(string command)
```

<span data-ttu-id="2ce29-818">Ajoutez une ligne de commande à l’historique sans l’exécuter.</span><span class="sxs-lookup"><span data-stu-id="2ce29-818">Add a command line to history without executing it.</span></span>

```csharp
void ClearKillRing()
```

<span data-ttu-id="2ce29-819">Effacez le point d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="2ce29-819">Clear the kill-ring.</span></span>  <span data-ttu-id="2ce29-820">Cela est principalement utilisé pour les tests.</span><span class="sxs-lookup"><span data-stu-id="2ce29-820">This is mostly used for testing.</span></span>

```csharp
void Delete(int start, int length)
```

<span data-ttu-id="2ce29-821">Supprimer les caractères de longueur du début.</span><span class="sxs-lookup"><span data-stu-id="2ce29-821">Delete length characters from start.</span></span>  <span data-ttu-id="2ce29-822">Cette opération prend en charge les opérations d’annulation et de rétablissement.</span><span class="sxs-lookup"><span data-stu-id="2ce29-822">This operation supports undo/redo.</span></span>

```csharp
void Ding()
```

<span data-ttu-id="2ce29-823">Effectuez l’action Ding en fonction des préférences de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="2ce29-823">Perform the Ding action based on the users preference.</span></span>

```csharp
void GetBufferState([ref] string input, [ref] int cursor)
void GetBufferState([ref] Ast ast, [ref] Token[] tokens,
  [ref] ParseError[] parseErrors, [ref] int cursor)
```

<span data-ttu-id="2ce29-824">Ces deux fonctions récupèrent des informations utiles sur l’état actuel de la mémoire tampon d’entrée.</span><span class="sxs-lookup"><span data-stu-id="2ce29-824">These two functions retrieve useful information about the current state of the input buffer.</span></span>  <span data-ttu-id="2ce29-825">La première est plus couramment utilisée dans les cas simples.</span><span class="sxs-lookup"><span data-stu-id="2ce29-825">The first is more commonly used for simple cases.</span></span>  <span data-ttu-id="2ce29-826">Le second est utilisé si votre liaison fait une opération plus avancée avec l’AST.</span><span class="sxs-lookup"><span data-stu-id="2ce29-826">The second is used if your binding is doing something more advanced with the Ast.</span></span>

```csharp
IEnumerable[Microsoft.PowerShell.KeyHandler]
  GetKeyHandlers(bool includeBound, bool includeUnbound)

IEnumerable[Microsoft.PowerShell.KeyHandler]
  GetKeyHandlers(string[] Chord)
```

<span data-ttu-id="2ce29-827">Ces deux fonctions sont utilisées par `Get-PSReadLineKeyHandler` .</span><span class="sxs-lookup"><span data-stu-id="2ce29-827">These two functions are used by `Get-PSReadLineKeyHandler`.</span></span> <span data-ttu-id="2ce29-828">La première est utilisée pour récupérer toutes les combinaisons de touches.</span><span class="sxs-lookup"><span data-stu-id="2ce29-828">The first is used to get all key bindings.</span></span> <span data-ttu-id="2ce29-829">Le second est utilisé pour recevoir des combinaisons de touches spécifiques.</span><span class="sxs-lookup"><span data-stu-id="2ce29-829">The second is used to get specific key bindings.</span></span>

```csharp
Microsoft.PowerShell.PSConsoleReadLineOptions GetOptions()
```

<span data-ttu-id="2ce29-830">Cette fonction est utilisée par Get-PSReadLineOption et n’est probablement pas trop utile dans une liaison de clé personnalisée.</span><span class="sxs-lookup"><span data-stu-id="2ce29-830">This function is used by Get-PSReadLineOption and probably isn't too useful in a custom key binding.</span></span>

```csharp
void GetSelectionState([ref] int start, [ref] int length)
```

<span data-ttu-id="2ce29-831">Si aucune sélection n’est effectuée sur la ligne de commande,-1 est retourné à la fois en début et en longueur.</span><span class="sxs-lookup"><span data-stu-id="2ce29-831">If there is no selection on the command line, -1 will be returned in both start and length.</span></span> <span data-ttu-id="2ce29-832">Si une sélection est effectuée sur la ligne de commande, le début et la longueur de la sélection sont retournés.</span><span class="sxs-lookup"><span data-stu-id="2ce29-832">If there is a selection on the command line, the start and length of the selection are returned.</span></span>

```csharp
void Insert(char c)
void Insert(string s)
```

<span data-ttu-id="2ce29-833">Insérez un caractère ou une chaîne au niveau du curseur.</span><span class="sxs-lookup"><span data-stu-id="2ce29-833">Insert a character or string at the cursor.</span></span>  <span data-ttu-id="2ce29-834">Cette opération prend en charge les opérations d’annulation et de rétablissement.</span><span class="sxs-lookup"><span data-stu-id="2ce29-834">This operation supports undo/redo.</span></span>

```csharp
string ReadLine(runspace remoteRunspace,
  System.Management.Automation.EngineIntrinsics engineIntrinsics)
```

<span data-ttu-id="2ce29-835">Il s’agit du point d’entrée principal de PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="2ce29-835">This is the main entry point to PSReadLine.</span></span> <span data-ttu-id="2ce29-836">Comme il ne prend pas en charge la récursivité, il n’est pas utile dans une liaison de clé personnalisée.</span><span class="sxs-lookup"><span data-stu-id="2ce29-836">It does not support recursion, so is not useful in a custom key binding.</span></span>

```csharp
void RemoveKeyHandler(string[] key)
```

<span data-ttu-id="2ce29-837">Cette fonction est utilisée par Remove-PSReadLineKeyHandler et n’est probablement pas trop utile dans une liaison de clé personnalisée.</span><span class="sxs-lookup"><span data-stu-id="2ce29-837">This function is used by Remove-PSReadLineKeyHandler and probably isn't too useful in a custom key binding.</span></span>

```csharp
void Replace(int start, int length, string replacement)
```

<span data-ttu-id="2ce29-838">Remplacez une partie de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="2ce29-838">Replace some of the input.</span></span> <span data-ttu-id="2ce29-839">Cette opération prend en charge les opérations d’annulation et de rétablissement.</span><span class="sxs-lookup"><span data-stu-id="2ce29-839">This operation supports undo/redo.</span></span> <span data-ttu-id="2ce29-840">C’est préférable à Delete, suivi de Insert, car il est traité comme une action unique pour Undo.</span><span class="sxs-lookup"><span data-stu-id="2ce29-840">This is preferred over Delete followed by Insert because it is treated as a single action for undo.</span></span>

```csharp
void SetCursorPosition(int cursor)
```

<span data-ttu-id="2ce29-841">Déplacer le curseur vers l’offset donné.</span><span class="sxs-lookup"><span data-stu-id="2ce29-841">Move the cursor to the given offset.</span></span> <span data-ttu-id="2ce29-842">Le déplacement du curseur n’est pas suivi pour l’annulation.</span><span class="sxs-lookup"><span data-stu-id="2ce29-842">Cursor movement is not tracked for undo.</span></span>

```csharp
void SetOptions(Microsoft.PowerShell.SetPSReadLineOption options)
```

<span data-ttu-id="2ce29-843">Cette fonction est une méthode d’assistance utilisée par l’applet de commande Set-PSReadLineOption, mais peut être utile pour une combinaison de touches personnalisée qui souhaite modifier temporairement un paramètre.</span><span class="sxs-lookup"><span data-stu-id="2ce29-843">This function is a helper method used by the cmdlet Set-PSReadLineOption, but might be useful to a custom key binding that wants to temporarily change a setting.</span></span>

```csharp
bool TryGetArgAsInt(System.Object arg, [ref] int numericArg,
  int defaultNumericArg)
```

<span data-ttu-id="2ce29-844">Cette méthode d’assistance est utilisée pour les liaisons personnalisées qui respectent DigitArgument.</span><span class="sxs-lookup"><span data-stu-id="2ce29-844">This helper method is used for custom bindings that honor DigitArgument.</span></span> <span data-ttu-id="2ce29-845">Un appel classique ressemble à ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="2ce29-845">A typical call looks like</span></span>

```powershell
[int]$numericArg = 0
[Microsoft.PowerShell.PSConsoleReadLine]::TryGetArgAsInt($arg,
  [ref]$numericArg, 1)
```

## <a name="note"></a><span data-ttu-id="2ce29-846">REMARQUE</span><span class="sxs-lookup"><span data-stu-id="2ce29-846">NOTE</span></span>

### <a name="powershell-compatibility"></a><span data-ttu-id="2ce29-847">COMPATIBILITÉ AVEC POWERSHELL</span><span class="sxs-lookup"><span data-stu-id="2ce29-847">POWERSHELL COMPATIBILITY</span></span>

<span data-ttu-id="2ce29-848">PSReadLine nécessite PowerShell 3,0, ou une version plus récente, et l’hôte de la console.</span><span class="sxs-lookup"><span data-stu-id="2ce29-848">PSReadLine requires PowerShell 3.0, or newer, and the console host.</span></span> <span data-ttu-id="2ce29-849">Il ne fonctionne pas dans PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="2ce29-849">It does not work in PowerShell ISE.</span></span> <span data-ttu-id="2ce29-850">Elle fonctionne dans la console de Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="2ce29-850">It does work in the console of Visual Studio Code.</span></span>

### <a name="command-history"></a><span data-ttu-id="2ce29-851">HISTORIQUE DES COMMANDES</span><span class="sxs-lookup"><span data-stu-id="2ce29-851">COMMAND HISTORY</span></span>

<span data-ttu-id="2ce29-852">PSReadLine gère un fichier d’historique contenant toutes les commandes et données que vous avez entrées à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="2ce29-852">PSReadLine maintains a history file containing all the commands and data you have entered from the command line.</span></span> <span data-ttu-id="2ce29-853">Cela peut contenir des données sensibles, y compris des mots de passe.</span><span class="sxs-lookup"><span data-stu-id="2ce29-853">This may contain sensitive data including passwords.</span></span> <span data-ttu-id="2ce29-854">Par exemple, si vous utilisez l’applet de commande, `ConvertTo-SecureString` le mot de passe est enregistré dans le fichier d’historique sous forme de texte brut.</span><span class="sxs-lookup"><span data-stu-id="2ce29-854">For example, if you use the `ConvertTo-SecureString` cmdlet the password is logged in the history file as plain text.</span></span> <span data-ttu-id="2ce29-855">Les fichiers d’historique sont un fichier nommé `$($host.Name)_history.txt` .</span><span class="sxs-lookup"><span data-stu-id="2ce29-855">The history files is a file named `$($host.Name)_history.txt`.</span></span> <span data-ttu-id="2ce29-856">Sur les systèmes Windows, le fichier d’historique est stocké à l’adresse `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine` .</span><span class="sxs-lookup"><span data-stu-id="2ce29-856">On Windows systems the history file is stored at `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine`.</span></span> <span data-ttu-id="2ce29-857">Sur les systèmes non-Windows, les fichiers d’historique sont stockés dans `$env:XDG_DATA_HOME/powershell/PSReadLine` ou `$env:HOME/.local/share/powershell/PSReadLine` .</span><span class="sxs-lookup"><span data-stu-id="2ce29-857">On non-Windows systems, the history files is stored at `$env:XDG_DATA_HOME/powershell/PSReadLine` or `$env:HOME/.local/share/powershell/PSReadLine`.</span></span>

### <a name="feedback--contributing-to-psreadline"></a><span data-ttu-id="2ce29-858">Commentaires & contribution à PSReadLine</span><span class="sxs-lookup"><span data-stu-id="2ce29-858">FEEDBACK & CONTRIBUTING TO PSReadLine</span></span>

[<span data-ttu-id="2ce29-859">PSReadLine sur GitHub</span><span class="sxs-lookup"><span data-stu-id="2ce29-859">PSReadLine on GitHub</span></span>](https://github.com/PowerShell/PSReadLine)

<span data-ttu-id="2ce29-860">N’hésitez pas à envoyer une demande de tirage ou à envoyer des commentaires sur la page GitHub.</span><span class="sxs-lookup"><span data-stu-id="2ce29-860">Feel free to submit a pull request or submit feedback on the GitHub page.</span></span>

## <a name="see-also"></a><span data-ttu-id="2ce29-861">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="2ce29-861">SEE ALSO</span></span>

<span data-ttu-id="2ce29-862">PSReadLine est fortement influencé par la bibliothèque GNU [ReadLine](https://tiswww.case.edu/php/chet/readline/rltop.html) .</span><span class="sxs-lookup"><span data-stu-id="2ce29-862">PSReadLine is heavily influenced by the GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) library.</span></span>

