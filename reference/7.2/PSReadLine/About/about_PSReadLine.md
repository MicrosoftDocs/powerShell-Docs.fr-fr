---
description: PSReadLine fournit une expérience d’édition de ligne de commande améliorée dans la console PowerShell.
Locale: en-US
ms.date: 11/23/2020
online version: https://docs.microsoft.com/powershell/module/psreadline/about/about_psreadline?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: À propos de PSReadLine
ms.openlocfilehash: b0c5950b2af6a866d0ffcfdd6ce7ad92a1763778
ms.sourcegitcommit: 77f6225ab0c8ea9faa1fe46b2ea15c178ec170e3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100500210"
---
# <a name="psreadline"></a><span data-ttu-id="16183-103">PSReadLine</span><span class="sxs-lookup"><span data-stu-id="16183-103">PSReadLine</span></span>

## <a name="about_psreadline"></a><span data-ttu-id="16183-104">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="16183-104">about_PSReadLine</span></span>

## <a name="short-description"></a><span data-ttu-id="16183-105">Description courte</span><span class="sxs-lookup"><span data-stu-id="16183-105">Short Description</span></span>

<span data-ttu-id="16183-106">PSReadLine fournit une expérience d’édition de ligne de commande améliorée dans la console PowerShell.</span><span class="sxs-lookup"><span data-stu-id="16183-106">PSReadLine provides an improved command-line editing experience in the PowerShell console.</span></span>

## <a name="long-description"></a><span data-ttu-id="16183-107">Description longue</span><span class="sxs-lookup"><span data-stu-id="16183-107">Long Description</span></span>

<span data-ttu-id="16183-108">PSReadLine 2,2 fournit une expérience d’édition de ligne de commande puissante pour la console PowerShell.</span><span class="sxs-lookup"><span data-stu-id="16183-108">PSReadLine 2.2 provides a powerful command-line editing experience for the PowerShell console.</span></span> <span data-ttu-id="16183-109">Elle offre les possibilités suivantes :</span><span class="sxs-lookup"><span data-stu-id="16183-109">It provides:</span></span>

- <span data-ttu-id="16183-110">Coloration de la syntaxe de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="16183-110">Syntax coloring of the command line</span></span>
- <span data-ttu-id="16183-111">Indication visuelle des erreurs de syntaxe</span><span class="sxs-lookup"><span data-stu-id="16183-111">A visual indication of syntax errors</span></span>
- <span data-ttu-id="16183-112">Une meilleure expérience multi-ligne (modification et historique)</span><span class="sxs-lookup"><span data-stu-id="16183-112">A better multi-line experience (both editing and history)</span></span>
- <span data-ttu-id="16183-113">Combinaisons de touches personnalisables</span><span class="sxs-lookup"><span data-stu-id="16183-113">Customizable key bindings</span></span>
- <span data-ttu-id="16183-114">Modes cmd et Emacs</span><span class="sxs-lookup"><span data-stu-id="16183-114">Cmd and Emacs modes</span></span>
- <span data-ttu-id="16183-115">Nombreuses options de configuration</span><span class="sxs-lookup"><span data-stu-id="16183-115">Many configuration options</span></span>
- <span data-ttu-id="16183-116">Saisie semi-automatique du style bash (facultatif en mode cmd, par défaut en mode emacs)</span><span class="sxs-lookup"><span data-stu-id="16183-116">Bash style completion (optional in Cmd mode, default in Emacs mode)</span></span>
- <span data-ttu-id="16183-117">Emacs-Yank/Kill-Ring</span><span class="sxs-lookup"><span data-stu-id="16183-117">Emacs yank/kill-ring</span></span>
- <span data-ttu-id="16183-118">Mouvement « mot » basé sur un jeton PowerShell et Kill</span><span class="sxs-lookup"><span data-stu-id="16183-118">PowerShell token based "word" movement and kill</span></span>
- <span data-ttu-id="16183-119">IntelliSense prédictif</span><span class="sxs-lookup"><span data-stu-id="16183-119">Predictive IntelliSense</span></span>

<span data-ttu-id="16183-120">PSReadLine 2.2.0 a ajouté deux nouvelles fonctionnalités IntelliSense prédictives :</span><span class="sxs-lookup"><span data-stu-id="16183-120">PSReadLine 2.2.0 added two new predictive IntelliSense features:</span></span>

- <span data-ttu-id="16183-121">Ajout du paramètre **PredictionViewStyle** pour permettre la sélection du nouveau `ListView` .</span><span class="sxs-lookup"><span data-stu-id="16183-121">Added the **PredictionViewStyle** parameter to allow for the selection of the new `ListView`.</span></span>
- <span data-ttu-id="16183-122">Connexion de PSReadLine aux `CommandPrediction` API introduites dans PS 7,1 pour permettre à un utilisateur de pouvoir importer un module de prédiction qui peut restituer les suggestions à partir d’une source personnalisée.</span><span class="sxs-lookup"><span data-stu-id="16183-122">Connected PSReadLine to the `CommandPrediction` APIs introduced in PS 7.1 to allow a user can import a predictor module that can render the suggestions from a custom source.</span></span>

<span data-ttu-id="16183-123">PSReadLine nécessite PowerShell 3,0 ou une version plus récente.</span><span class="sxs-lookup"><span data-stu-id="16183-123">PSReadLine requires PowerShell 3.0, or newer.</span></span> <span data-ttu-id="16183-124">PSReadLine fonctionne avec l’hôte de console, Visual Studio Code et le terminal de fenêtre par défaut.</span><span class="sxs-lookup"><span data-stu-id="16183-124">PSReadLine works with default console host, Visual Studio Code, and Window Terminal.</span></span> <span data-ttu-id="16183-125">Il ne fonctionne pas dans PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="16183-125">It does not work in PowerShell ISE.</span></span>

<span data-ttu-id="16183-126">PSReadLine 2.2.0 est fourni avec PowerShell 7,2 et est pris en charge dans toutes les versions prises en charge de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="16183-126">PSReadLine 2.2.0 ships with PowerShell 7.2 and is supported in all supported versions of PowerShell.</span></span> <span data-ttu-id="16183-127">Vous pouvez l’installer à partir du PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="16183-127">It is available to install from the PowerShell Gallery.</span></span>
<span data-ttu-id="16183-128">Pour installer PSReadLine 2.2.0 dans une version prise en charge de PowerShell, exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="16183-128">To install PSReadLine 2.2.0 in a supported version of PowerShell run the following command.</span></span>

```powershell
Install-Module -Name PSReadLine -AllowPrerelease
```

> [!NOTE]
> <span data-ttu-id="16183-129">À compter de PowerShell 7,0, PowerShell ignore le chargement automatique de PSReadLine sur Windows si un programme de lecture d’écran est détecté.</span><span class="sxs-lookup"><span data-stu-id="16183-129">Beginning with PowerShell 7.0, PowerShell skips auto-loading PSReadLine on Windows if a screen reader program is detected.</span></span> <span data-ttu-id="16183-130">Actuellement, PSReadLine ne fonctionne pas correctement avec les lecteurs d’écran.</span><span class="sxs-lookup"><span data-stu-id="16183-130">Currently, PSReadLine doesn't work well with the screen readers.</span></span> <span data-ttu-id="16183-131">Le rendu et la mise en forme par défaut de PowerShell 7,0 sur Windows fonctionnent correctement.</span><span class="sxs-lookup"><span data-stu-id="16183-131">The default rendering and formatting of PowerShell 7.0 on Windows works properly.</span></span> <span data-ttu-id="16183-132">Vous pouvez charger le module manuellement, si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="16183-132">You can manually load the module if necessary.</span></span>

## <a name="predictive-intellisense"></a><span data-ttu-id="16183-133">IntelliSense prédictif</span><span class="sxs-lookup"><span data-stu-id="16183-133">Predictive IntelliSense</span></span>

<span data-ttu-id="16183-134">La fonctionnalité IntelliSense prédictive est un ajout au concept de saisie semi-automatique via la touche Tab qui aide l’utilisateur à exécuter correctement les commandes.</span><span class="sxs-lookup"><span data-stu-id="16183-134">Predictive IntelliSense is an addition to the concept of tab completion that assists the user in successfully completing commands.</span></span> <span data-ttu-id="16183-135">Il permet aux utilisateurs de découvrir, de modifier et d’exécuter des commandes complètes basées sur des prédictions correspondantes à partir de l’historique de l’utilisateur et d’autres plug-ins spécifiques au domaine.</span><span class="sxs-lookup"><span data-stu-id="16183-135">It enables users to discover, edit, and execute full commands based on matching predictions from the user's history and additional domain specific plugins.</span></span>

### <a name="enable-predictive-intellisense"></a><span data-ttu-id="16183-136">Activer la fonctionnalité IntelliSense prédictive</span><span class="sxs-lookup"><span data-stu-id="16183-136">Enable Predictive IntelliSense</span></span>

<span data-ttu-id="16183-137">La fonctionnalité IntelliSense prédictive est désactivée par défaut.</span><span class="sxs-lookup"><span data-stu-id="16183-137">Predictive IntelliSense is disabled by default.</span></span> <span data-ttu-id="16183-138">Pour activer les prédictions, exécutez simplement la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="16183-138">To enable predictions, just run the following command:</span></span>

```powershell
Set-PSReadLineOption -PredictionSource History
```

<span data-ttu-id="16183-139">Le paramètre **PredictionSource** peut également accepter des plug-ins pour des exigences personnalisées et spécifiques à un domaine.</span><span class="sxs-lookup"><span data-stu-id="16183-139">The **PredictionSource** parameter can also accept plugins for domain specific and custom requirements.</span></span>

<span data-ttu-id="16183-140">Pour désactiver IntelliSense prédictif, il suffit d’exécuter :</span><span class="sxs-lookup"><span data-stu-id="16183-140">To disable Predictive IntelliSense, just run:</span></span>

```powershell
Set-PSReadLineOption -PredictionSource None
```

<span data-ttu-id="16183-141">Les fonctions suivantes sont disponibles dans la classe **[Microsoft. PowerShell. PSConsoleReadLine]**.</span><span class="sxs-lookup"><span data-stu-id="16183-141">The following functions are available in the class **[Microsoft.PowerShell.PSConsoleReadLine]**.</span></span>

## <a name="basic-editing-functions"></a><span data-ttu-id="16183-142">Fonctions d’édition de base</span><span class="sxs-lookup"><span data-stu-id="16183-142">Basic editing functions</span></span>

### <a name="abort"></a><span data-ttu-id="16183-143">Abandon</span><span class="sxs-lookup"><span data-stu-id="16183-143">Abort</span></span>

<span data-ttu-id="16183-144">Annuler l’action en cours, par exemple, recherche de l’historique incrémentiel.</span><span class="sxs-lookup"><span data-stu-id="16183-144">Abort current action, e.g. incremental history search.</span></span>

- <span data-ttu-id="16183-145">Emacs- `<Ctrl+g>`</span><span class="sxs-lookup"><span data-stu-id="16183-145">Emacs: `<Ctrl+g>`</span></span>

### <a name="acceptandgetnext"></a><span data-ttu-id="16183-146">AcceptAndGetNext</span><span class="sxs-lookup"><span data-stu-id="16183-146">AcceptAndGetNext</span></span>

<span data-ttu-id="16183-147">Tentative d’exécution de l’entrée en cours.</span><span class="sxs-lookup"><span data-stu-id="16183-147">Attempt to execute the current input.</span></span> <span data-ttu-id="16183-148">Si elle peut être exécutée (par exemple, AcceptLine), rappelez l’élément suivant de l’historique la prochaine fois que ReadLine est appelé.</span><span class="sxs-lookup"><span data-stu-id="16183-148">If it can be executed (like AcceptLine), then recall the next item from history the next time ReadLine is called.</span></span>

- <span data-ttu-id="16183-149">Emacs- `<Ctrl+o>`</span><span class="sxs-lookup"><span data-stu-id="16183-149">Emacs: `<Ctrl+o>`</span></span>

### <a name="acceptline"></a><span data-ttu-id="16183-150">AcceptLine</span><span class="sxs-lookup"><span data-stu-id="16183-150">AcceptLine</span></span>

<span data-ttu-id="16183-151">Tentative d’exécution de l’entrée en cours.</span><span class="sxs-lookup"><span data-stu-id="16183-151">Attempt to execute the current input.</span></span> <span data-ttu-id="16183-152">Si l’entrée actuelle est incomplète (par exemple, il manque une parenthèse fermante, un crochet ou un guillemet, l’invite de continuation est affichée sur la ligne suivante et PSReadLine attend que les clés modifient l’entrée actuelle.</span><span class="sxs-lookup"><span data-stu-id="16183-152">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="16183-153">Cmd `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="16183-153">Cmd: `<Enter>`</span></span>
- <span data-ttu-id="16183-154">Emacs- `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="16183-154">Emacs: `<Enter>`</span></span>
- <span data-ttu-id="16183-155">Mode d’insertion VI : `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="16183-155">Vi insert mode: `<Enter>`</span></span>

### <a name="addline"></a><span data-ttu-id="16183-156">AddLine</span><span class="sxs-lookup"><span data-stu-id="16183-156">AddLine</span></span>

<span data-ttu-id="16183-157">L’invite de continuation est affichée sur la ligne suivante et PSReadLine attend que les clés modifient l’entrée actuelle.</span><span class="sxs-lookup"><span data-stu-id="16183-157">The continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span> <span data-ttu-id="16183-158">Cela est utile pour entrer une entrée multiligne sous la forme d’une commande unique, même lorsqu’une seule ligne est complète en entrée.</span><span class="sxs-lookup"><span data-stu-id="16183-158">This is useful to enter multi-line input as a single command even when a single line is complete input by itself.</span></span>

- <span data-ttu-id="16183-159">Cmd `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="16183-159">Cmd: `<Shift+Enter>`</span></span>
- <span data-ttu-id="16183-160">Emacs- `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="16183-160">Emacs: `<Shift+Enter>`</span></span>
- <span data-ttu-id="16183-161">Mode d’insertion VI : `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="16183-161">Vi insert mode: `<Shift+Enter>`</span></span>
- <span data-ttu-id="16183-162">Mode de commande VI : `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="16183-162">Vi command mode: `<Shift+Enter>`</span></span>

### <a name="backwarddeletechar"></a><span data-ttu-id="16183-163">BackwardDeleteChar</span><span class="sxs-lookup"><span data-stu-id="16183-163">BackwardDeleteChar</span></span>

<span data-ttu-id="16183-164">Supprimez le caractère avant le curseur.</span><span class="sxs-lookup"><span data-stu-id="16183-164">Delete the character before the cursor.</span></span>

- <span data-ttu-id="16183-165">Cmd : `<Backspace>` , `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="16183-165">Cmd: `<Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="16183-166">Emacs : `<Backspace>` , `<Ctrl+Backspace>` , `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="16183-166">Emacs: `<Backspace>`, `<Ctrl+Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="16183-167">Mode d’insertion VI : `<Backspace>`</span><span class="sxs-lookup"><span data-stu-id="16183-167">Vi insert mode: `<Backspace>`</span></span>
- <span data-ttu-id="16183-168">Mode de commande VI : `<X>` , `<d,h>`</span><span class="sxs-lookup"><span data-stu-id="16183-168">Vi command mode: `<X>`, `<d,h>`</span></span>

### <a name="backwarddeleteline"></a><span data-ttu-id="16183-169">BackwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="16183-169">BackwardDeleteLine</span></span>

<span data-ttu-id="16183-170">Comme BackwardKillLine-supprime le texte du point jusqu’au début de la ligne, mais ne place pas le texte supprimé dans l’anneau d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="16183-170">Like BackwardKillLine - deletes text from the point to the start of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="16183-171">Cmd `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="16183-171">Cmd: `<Ctrl+Home>`</span></span>
- <span data-ttu-id="16183-172">Mode d’insertion VI : `<Ctrl+u>` , `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="16183-172">Vi insert mode: `<Ctrl+u>`, `<Ctrl+Home>`</span></span>
- <span data-ttu-id="16183-173">Mode de commande VI : `<Ctrl+u>` , `<Ctrl+Home>` , `<d,0>`</span><span class="sxs-lookup"><span data-stu-id="16183-173">Vi command mode: `<Ctrl+u>`, `<Ctrl+Home>`, `<d,0>`</span></span>

### <a name="backwarddeleteword"></a><span data-ttu-id="16183-174">BackwardDeleteWord</span><span class="sxs-lookup"><span data-stu-id="16183-174">BackwardDeleteWord</span></span>

<span data-ttu-id="16183-175">Supprime le mot précédent.</span><span class="sxs-lookup"><span data-stu-id="16183-175">Deletes the previous word.</span></span>

- <span data-ttu-id="16183-176">Mode de commande VI : `<Ctrl+w>` , `<d,b>`</span><span class="sxs-lookup"><span data-stu-id="16183-176">Vi command mode: `<Ctrl+w>`, `<d,b>`</span></span>

### <a name="backwardkillline"></a><span data-ttu-id="16183-177">BackwardKillLine</span><span class="sxs-lookup"><span data-stu-id="16183-177">BackwardKillLine</span></span>

<span data-ttu-id="16183-178">Effacez l’entrée à partir du début de l’entrée jusqu’au curseur.</span><span class="sxs-lookup"><span data-stu-id="16183-178">Clear the input from the start of the input to the cursor.</span></span> <span data-ttu-id="16183-179">Le texte effacé est placé dans le Kill-Ring.</span><span class="sxs-lookup"><span data-stu-id="16183-179">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="16183-180">Emacs- `<Ctrl+u>` , `<Ctrl+x,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="16183-180">Emacs: `<Ctrl+u>`, `<Ctrl+x,Backspace>`</span></span>

### <a name="backwardkillword"></a><span data-ttu-id="16183-181">BackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="16183-181">BackwardKillWord</span></span>

<span data-ttu-id="16183-182">Efface l’entrée du début du mot actuel jusqu’au curseur.</span><span class="sxs-lookup"><span data-stu-id="16183-182">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="16183-183">Si le curseur se trouve entre des mots, l’entrée est effacée du début du mot précédent au curseur.</span><span class="sxs-lookup"><span data-stu-id="16183-183">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="16183-184">Le texte effacé est placé dans le Kill-Ring.</span><span class="sxs-lookup"><span data-stu-id="16183-184">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="16183-185">Cmd : `<Ctrl+Backspace>` , `<Ctrl+w>`</span><span class="sxs-lookup"><span data-stu-id="16183-185">Cmd: `<Ctrl+Backspace>`, `<Ctrl+w>`</span></span>
- <span data-ttu-id="16183-186">Emacs- `<Alt+Backspace>` , `<Escape,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="16183-186">Emacs: `<Alt+Backspace>`, `<Escape,Backspace>`</span></span>
- <span data-ttu-id="16183-187">Mode d’insertion VI : `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="16183-187">Vi insert mode: `<Ctrl+Backspace>`</span></span>
- <span data-ttu-id="16183-188">Mode de commande VI : `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="16183-188">Vi command mode: `<Ctrl+Backspace>`</span></span>

### <a name="cancelline"></a><span data-ttu-id="16183-189">CancelLine</span><span class="sxs-lookup"><span data-stu-id="16183-189">CancelLine</span></span>

<span data-ttu-id="16183-190">Annule l’entrée actuelle, en laissant l’entrée à l’écran, mais retourne à l’hôte afin que l’invite soit de nouveau évaluée.</span><span class="sxs-lookup"><span data-stu-id="16183-190">Cancel the current input, leaving the input on the screen, but returns back to the host so the prompt is evaluated again.</span></span>

- <span data-ttu-id="16183-191">Mode d’insertion VI : `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="16183-191">Vi insert mode: `<Ctrl+c>`</span></span>
- <span data-ttu-id="16183-192">Mode de commande VI : `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="16183-192">Vi command mode: `<Ctrl+c>`</span></span>

### <a name="copy"></a><span data-ttu-id="16183-193">Copier</span><span class="sxs-lookup"><span data-stu-id="16183-193">Copy</span></span>

<span data-ttu-id="16183-194">Copier la région sélectionnée dans le presse-papiers du système.</span><span class="sxs-lookup"><span data-stu-id="16183-194">Copy selected region to the system clipboard.</span></span> <span data-ttu-id="16183-195">Si aucune région n’est sélectionnée, copiez la ligne entière.</span><span class="sxs-lookup"><span data-stu-id="16183-195">If no region is selected, copy the whole line.</span></span>

- <span data-ttu-id="16183-196">Cmd `<Ctrl+C>`</span><span class="sxs-lookup"><span data-stu-id="16183-196">Cmd: `<Ctrl+C>`</span></span>

### <a name="copyorcancelline"></a><span data-ttu-id="16183-197">CopyOrCancelLine</span><span class="sxs-lookup"><span data-stu-id="16183-197">CopyOrCancelLine</span></span>

<span data-ttu-id="16183-198">Si le texte est sélectionné, copiez-le dans le presse-papiers, sinon, annulez la ligne.</span><span class="sxs-lookup"><span data-stu-id="16183-198">If text is selected, copy to the clipboard, otherwise cancel the line.</span></span>

- <span data-ttu-id="16183-199">Cmd `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="16183-199">Cmd: `<Ctrl+c>`</span></span>
- <span data-ttu-id="16183-200">Emacs- `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="16183-200">Emacs: `<Ctrl+c>`</span></span>

### <a name="cut"></a><span data-ttu-id="16183-201">Couper</span><span class="sxs-lookup"><span data-stu-id="16183-201">Cut</span></span>

<span data-ttu-id="16183-202">Supprimer la zone sélectionnée en plaçant le texte supprimé dans le presse-papiers du système.</span><span class="sxs-lookup"><span data-stu-id="16183-202">Delete selected region placing deleted text in the system clipboard.</span></span>

- <span data-ttu-id="16183-203">Cmd `<Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="16183-203">Cmd: `<Ctrl+x>`</span></span>

### <a name="deletechar"></a><span data-ttu-id="16183-204">DeleteChar</span><span class="sxs-lookup"><span data-stu-id="16183-204">DeleteChar</span></span>

<span data-ttu-id="16183-205">Supprimez le caractère sous le curseur.</span><span class="sxs-lookup"><span data-stu-id="16183-205">Delete the character under the cursor.</span></span>

- <span data-ttu-id="16183-206">Cmd `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="16183-206">Cmd: `<Delete>`</span></span>
- <span data-ttu-id="16183-207">Emacs- `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="16183-207">Emacs: `<Delete>`</span></span>
- <span data-ttu-id="16183-208">Mode d’insertion VI : `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="16183-208">Vi insert mode: `<Delete>`</span></span>
- <span data-ttu-id="16183-209">Mode de commande VI : `<Delete>` , `<x>` , `<d,l>` , `<d,Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="16183-209">Vi command mode: `<Delete>`, `<x>`, `<d,l>`, `<d,Spacebar>`</span></span>

### <a name="deletecharorexit"></a><span data-ttu-id="16183-210">DeleteCharOrExit</span><span class="sxs-lookup"><span data-stu-id="16183-210">DeleteCharOrExit</span></span>

<span data-ttu-id="16183-211">Supprimez le caractère sous le curseur, ou si la ligne est vide, quittez le processus.</span><span class="sxs-lookup"><span data-stu-id="16183-211">Delete the character under the cursor, or if the line is empty, exit the process.</span></span>

- <span data-ttu-id="16183-212">Emacs- `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="16183-212">Emacs: `<Ctrl+d>`</span></span>

### <a name="deleteendofbuffer"></a><span data-ttu-id="16183-213">DeleteEndOfBuffer</span><span class="sxs-lookup"><span data-stu-id="16183-213">DeleteEndOfBuffer</span></span>

<span data-ttu-id="16183-214">Supprime à la fin de la mémoire tampon multiligne.</span><span class="sxs-lookup"><span data-stu-id="16183-214">Deletes to the end of the multiline buffer.</span></span>

- <span data-ttu-id="16183-215">Mode de commande VI : `<d,G>`</span><span class="sxs-lookup"><span data-stu-id="16183-215">Vi command mode: `<d,G>`</span></span>

### <a name="deleteendofword"></a><span data-ttu-id="16183-216">DeleteEndOfWord</span><span class="sxs-lookup"><span data-stu-id="16183-216">DeleteEndOfWord</span></span>

<span data-ttu-id="16183-217">Supprimer à la fin du mot.</span><span class="sxs-lookup"><span data-stu-id="16183-217">Delete to the end of the word.</span></span>

- <span data-ttu-id="16183-218">Mode de commande VI : `<d,e>`</span><span class="sxs-lookup"><span data-stu-id="16183-218">Vi command mode: `<d,e>`</span></span>

### <a name="deleteline"></a><span data-ttu-id="16183-219">DeleteLine</span><span class="sxs-lookup"><span data-stu-id="16183-219">DeleteLine</span></span>

<span data-ttu-id="16183-220">Supprime la ligne logique actuelle d’une mémoire tampon multiligne, ce qui permet d’annuler.</span><span class="sxs-lookup"><span data-stu-id="16183-220">Deletes the current logical line of a multiline buffer, enabling undo.</span></span>

- <span data-ttu-id="16183-221">Mode de commande VI : `<d,d>` , `<d,_>`</span><span class="sxs-lookup"><span data-stu-id="16183-221">Vi command mode: `<d,d>`, `<d,_>`</span></span>

### <a name="deletepreviouslines"></a><span data-ttu-id="16183-222">DeletePreviousLines</span><span class="sxs-lookup"><span data-stu-id="16183-222">DeletePreviousLines</span></span>

<span data-ttu-id="16183-223">Supprime les lignes logiques requises précédentes et la ligne logique actuelle dans une mémoire tampon multiligne.</span><span class="sxs-lookup"><span data-stu-id="16183-223">Deletes the previous requested logical lines and the current logical line in a multiline buffer.</span></span>

- <span data-ttu-id="16183-224">Mode de commande VI : `<d,k>`</span><span class="sxs-lookup"><span data-stu-id="16183-224">Vi command mode: `<d,k>`</span></span>

### <a name="deleterelativelines"></a><span data-ttu-id="16183-225">DeleteRelativeLines</span><span class="sxs-lookup"><span data-stu-id="16183-225">DeleteRelativeLines</span></span>

<span data-ttu-id="16183-226">Supprime du début de la mémoire tampon jusqu’à la ligne logique actuelle dans une mémoire tampon multiligne.</span><span class="sxs-lookup"><span data-stu-id="16183-226">Deletes from the beginning of the buffer to the current logical line in a multiline buffer.</span></span>

<span data-ttu-id="16183-227">Comme la plupart des commandes VI, la `<d,g,g>` commande peut être précédée d’un argument numérique qui spécifie un numéro de ligne absolu, qui, avec le numéro de ligne en cours, compose une plage de lignes à supprimer.</span><span class="sxs-lookup"><span data-stu-id="16183-227">As most Vi commands, the `<d,g,g>` command can be prepended with a numeric argument that specifies an absolute line number, which, together with the current line number, make up a range of lines to be deleted.</span></span>
<span data-ttu-id="16183-228">S’il n’est pas spécifié, l’argument numérique a la valeur par défaut 1, qui fait référence à la première ligne logique dans une mémoire tampon multiligne.</span><span class="sxs-lookup"><span data-stu-id="16183-228">If not specified, the numeric argument defaults to 1, which refers to the first logical line in a multiline buffer.</span></span>

<span data-ttu-id="16183-229">Le nombre réel de lignes à supprimer de la ligne multiligne est calculé comme étant la différence entre le numéro de ligne logique actuel et l’argument numérique spécifié, qui peut donc être négatif.</span><span class="sxs-lookup"><span data-stu-id="16183-229">The actual number of lines to be deleted from the multiline is computed as the difference between the current logical line number and the specified numeric argument, which can thus be negative.</span></span> <span data-ttu-id="16183-230">Par conséquent, la partie _relative_ du nom de la méthode.</span><span class="sxs-lookup"><span data-stu-id="16183-230">Hence the _relative_ part of method name.</span></span>

- <span data-ttu-id="16183-231">Mode de commande VI : `<d,g,g>`</span><span class="sxs-lookup"><span data-stu-id="16183-231">Vi command mode: `<d,g,g>`</span></span>

### <a name="deletenextlines"></a><span data-ttu-id="16183-232">DeleteNextLines</span><span class="sxs-lookup"><span data-stu-id="16183-232">DeleteNextLines</span></span>

<span data-ttu-id="16183-233">Supprime la ligne logique actuelle et les lignes logiques suivantes demandées dans une mémoire tampon multiligne.</span><span class="sxs-lookup"><span data-stu-id="16183-233">Deletes the current logical line and the next requested logical lines in a multiline buffer.</span></span>

- <span data-ttu-id="16183-234">Mode de commande VI : `<d,j>`</span><span class="sxs-lookup"><span data-stu-id="16183-234">Vi command mode: `<d,j>`</span></span>

### <a name="deletelinetofirstchar"></a><span data-ttu-id="16183-235">DeleteLineToFirstChar</span><span class="sxs-lookup"><span data-stu-id="16183-235">DeleteLineToFirstChar</span></span>

<span data-ttu-id="16183-236">Supprime du premier caractère non vide de la ligne logique actuelle dans une mémoire tampon multiligne.</span><span class="sxs-lookup"><span data-stu-id="16183-236">Deletes from the first non-blank character of the current logical line in a multiline buffer.</span></span>

- <span data-ttu-id="16183-237">Mode de commande VI : `<d,^>`</span><span class="sxs-lookup"><span data-stu-id="16183-237">Vi command mode: `<d,^>`</span></span>

### <a name="deletetoend"></a><span data-ttu-id="16183-238">DeleteToEnd</span><span class="sxs-lookup"><span data-stu-id="16183-238">DeleteToEnd</span></span>

<span data-ttu-id="16183-239">Supprimer à la fin de la ligne.</span><span class="sxs-lookup"><span data-stu-id="16183-239">Delete to the end of the line.</span></span>

- <span data-ttu-id="16183-240">Mode de commande VI : `<D>` , `<d,$>`</span><span class="sxs-lookup"><span data-stu-id="16183-240">Vi command mode: `<D>`, `<d,$>`</span></span>

### <a name="deleteword"></a><span data-ttu-id="16183-241">DeleteWord</span><span class="sxs-lookup"><span data-stu-id="16183-241">DeleteWord</span></span>

<span data-ttu-id="16183-242">Supprimer le mot suivant.</span><span class="sxs-lookup"><span data-stu-id="16183-242">Delete the next word.</span></span>

- <span data-ttu-id="16183-243">Mode de commande VI : `<d,w>`</span><span class="sxs-lookup"><span data-stu-id="16183-243">Vi command mode: `<d,w>`</span></span>

### <a name="forwarddeleteline"></a><span data-ttu-id="16183-244">ForwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="16183-244">ForwardDeleteLine</span></span>

<span data-ttu-id="16183-245">Comme ForwardKillLine-supprime le texte du point jusqu’à la fin de la ligne, mais ne place pas le texte supprimé dans l’anneau Kill.</span><span class="sxs-lookup"><span data-stu-id="16183-245">Like ForwardKillLine - deletes text from the point to the end of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="16183-246">Cmd `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="16183-246">Cmd: `<Ctrl+End>`</span></span>
- <span data-ttu-id="16183-247">Mode d’insertion VI : `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="16183-247">Vi insert mode: `<Ctrl+End>`</span></span>
- <span data-ttu-id="16183-248">Mode de commande VI : `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="16183-248">Vi command mode: `<Ctrl+End>`</span></span>

### <a name="insertlineabove"></a><span data-ttu-id="16183-249">InsertLineAbove</span><span class="sxs-lookup"><span data-stu-id="16183-249">InsertLineAbove</span></span>

<span data-ttu-id="16183-250">Une nouvelle ligne vide est créée au-dessus de la ligne active, quel que soit l’endroit où se trouve le curseur sur la ligne active.</span><span class="sxs-lookup"><span data-stu-id="16183-250">A new empty line is created above the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="16183-251">Le curseur se déplace au début de la nouvelle ligne.</span><span class="sxs-lookup"><span data-stu-id="16183-251">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="16183-252">Cmd `<Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="16183-252">Cmd: `<Ctrl+Enter>`</span></span>

### <a name="insertlinebelow"></a><span data-ttu-id="16183-253">InsertLineBelow</span><span class="sxs-lookup"><span data-stu-id="16183-253">InsertLineBelow</span></span>

<span data-ttu-id="16183-254">Une nouvelle ligne vide est créée sous la ligne active, quel que soit l’endroit où se trouve le curseur sur la ligne active.</span><span class="sxs-lookup"><span data-stu-id="16183-254">A new empty line is created below the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="16183-255">Le curseur se déplace au début de la nouvelle ligne.</span><span class="sxs-lookup"><span data-stu-id="16183-255">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="16183-256">Cmd `<Shift+Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="16183-256">Cmd: `<Shift+Ctrl+Enter>`</span></span>

### <a name="invertcase"></a><span data-ttu-id="16183-257">InvertCase</span><span class="sxs-lookup"><span data-stu-id="16183-257">InvertCase</span></span>

<span data-ttu-id="16183-258">Inverser la casse du caractère actuel et passer au suivant.</span><span class="sxs-lookup"><span data-stu-id="16183-258">Invert the case of the current character and move to the next one.</span></span>

- <span data-ttu-id="16183-259">Mode de commande VI : `<~>`</span><span class="sxs-lookup"><span data-stu-id="16183-259">Vi command mode: `<~>`</span></span>

### <a name="killline"></a><span data-ttu-id="16183-260">KillLine</span><span class="sxs-lookup"><span data-stu-id="16183-260">KillLine</span></span>

<span data-ttu-id="16183-261">Effacez l’entrée du curseur jusqu’à la fin de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="16183-261">Clear the input from the cursor to the end of the input.</span></span> <span data-ttu-id="16183-262">Le texte effacé est placé dans le Kill-Ring.</span><span class="sxs-lookup"><span data-stu-id="16183-262">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="16183-263">Emacs- `<Ctrl+k>`</span><span class="sxs-lookup"><span data-stu-id="16183-263">Emacs: `<Ctrl+k>`</span></span>

### <a name="killregion"></a><span data-ttu-id="16183-264">KillRegion</span><span class="sxs-lookup"><span data-stu-id="16183-264">KillRegion</span></span>

<span data-ttu-id="16183-265">Supprimer le texte situé entre le curseur et la marque.</span><span class="sxs-lookup"><span data-stu-id="16183-265">Kill the text between the cursor and the mark.</span></span>

- <span data-ttu-id="16183-266">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="16183-266">Function is unbound.</span></span>

### <a name="killword"></a><span data-ttu-id="16183-267">KillWord</span><span class="sxs-lookup"><span data-stu-id="16183-267">KillWord</span></span>

<span data-ttu-id="16183-268">Efface l’entrée du curseur jusqu’à la fin du mot actuel.</span><span class="sxs-lookup"><span data-stu-id="16183-268">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="16183-269">Si le curseur se trouve entre des mots, l’entrée est effacée du curseur jusqu’à la fin du mot suivant.</span><span class="sxs-lookup"><span data-stu-id="16183-269">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="16183-270">Le texte effacé est placé dans le Kill-Ring.</span><span class="sxs-lookup"><span data-stu-id="16183-270">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="16183-271">Cmd : `<Alt+d>` , `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="16183-271">Cmd: `<Alt+d>`, `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="16183-272">Emacs- `<Alt+d>` , `<Escape,d>`</span><span class="sxs-lookup"><span data-stu-id="16183-272">Emacs: `<Alt+d>`, `<Escape,d>`</span></span>
- <span data-ttu-id="16183-273">Mode d’insertion VI : `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="16183-273">Vi insert mode: `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="16183-274">Mode de commande VI : `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="16183-274">Vi command mode: `<Ctrl+Delete>`</span></span>

### <a name="paste"></a><span data-ttu-id="16183-275">Coller</span><span class="sxs-lookup"><span data-stu-id="16183-275">Paste</span></span>

<span data-ttu-id="16183-276">Collez le texte à partir du presse-papiers du système.</span><span class="sxs-lookup"><span data-stu-id="16183-276">Paste text from the system clipboard.</span></span>

- <span data-ttu-id="16183-277">Cmd : `<Ctrl+v>` , `<Shift+Insert>`</span><span class="sxs-lookup"><span data-stu-id="16183-277">Cmd: `<Ctrl+v>`, `<Shift+Insert>`</span></span>
- <span data-ttu-id="16183-278">Mode d’insertion VI : `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="16183-278">Vi insert mode: `<Ctrl+v>`</span></span>
- <span data-ttu-id="16183-279">Mode de commande VI : `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="16183-279">Vi command mode: `<Ctrl+v>`</span></span>

> [!IMPORTANT]
> <span data-ttu-id="16183-280">Lors de l’utilisation de la fonction **Paste** , le contenu entier de la mémoire tampon du presse-papiers est collé dans la mémoire tampon d’entrée de PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="16183-280">When using the **Paste** function, the entire contents of the clipboard buffer is pasted into the input buffer of PSReadLine.</span></span> <span data-ttu-id="16183-281">La mémoire tampon d’entrée est ensuite transmise à l’analyseur PowerShell.</span><span class="sxs-lookup"><span data-stu-id="16183-281">The input buffer is then passed to the PowerShell parser.</span></span> <span data-ttu-id="16183-282">L’entrée collée à l’aide de la méthode de collage **avec le bouton droit** de la console de l’application de console est copiée dans la mémoire tampon d’entrée un caractère à la fois.</span><span class="sxs-lookup"><span data-stu-id="16183-282">Input pasted using the console application's **right-click** paste method is copied to the input buffer one character at a time.</span></span> <span data-ttu-id="16183-283">La mémoire tampon d’entrée est transmise à l’analyseur lorsqu’un caractère de saut de ligne est copié.</span><span class="sxs-lookup"><span data-stu-id="16183-283">The input buffer is passed to the parser when a newline character is copied.</span></span> <span data-ttu-id="16183-284">Par conséquent, l’entrée est analysée une ligne à la fois.</span><span class="sxs-lookup"><span data-stu-id="16183-284">Therefore, the input is parsed one line at a time.</span></span> <span data-ttu-id="16183-285">La différence entre les méthodes de collage entraîne un comportement d’exécution différent.</span><span class="sxs-lookup"><span data-stu-id="16183-285">The difference between paste methods results in different execution behavior.</span></span>

### <a name="pasteafter"></a><span data-ttu-id="16183-286">PasteAfter</span><span class="sxs-lookup"><span data-stu-id="16183-286">PasteAfter</span></span>

<span data-ttu-id="16183-287">Collez le presse-papiers après le curseur, en déplaçant le curseur à la fin du texte collé.</span><span class="sxs-lookup"><span data-stu-id="16183-287">Paste the clipboard after the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="16183-288">Mode de commande VI : `<p>`</span><span class="sxs-lookup"><span data-stu-id="16183-288">Vi command mode: `<p>`</span></span>

### <a name="pastebefore"></a><span data-ttu-id="16183-289">PasteBefore</span><span class="sxs-lookup"><span data-stu-id="16183-289">PasteBefore</span></span>

<span data-ttu-id="16183-290">Collez le presse-papiers avant le curseur, en déplaçant le curseur à la fin du texte collé.</span><span class="sxs-lookup"><span data-stu-id="16183-290">Paste the clipboard before the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="16183-291">Mode de commande VI : `<P>`</span><span class="sxs-lookup"><span data-stu-id="16183-291">Vi command mode: `<P>`</span></span>

### <a name="prependandaccept"></a><span data-ttu-id="16183-292">PrependAndAccept</span><span class="sxs-lookup"><span data-stu-id="16183-292">PrependAndAccept</span></span>

<span data-ttu-id="16183-293">Faites précéder un' # 'et acceptez la ligne.</span><span class="sxs-lookup"><span data-stu-id="16183-293">Prepend a '#' and accept the line.</span></span>

- <span data-ttu-id="16183-294">Mode de commande VI : `<#>`</span><span class="sxs-lookup"><span data-stu-id="16183-294">Vi command mode: `<#>`</span></span>

### <a name="redo"></a><span data-ttu-id="16183-295">Rétablir</span><span class="sxs-lookup"><span data-stu-id="16183-295">Redo</span></span>

<span data-ttu-id="16183-296">Annule une annulation.</span><span class="sxs-lookup"><span data-stu-id="16183-296">Undo an undo.</span></span>

- <span data-ttu-id="16183-297">Cmd `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="16183-297">Cmd: `<Ctrl+y>`</span></span>
- <span data-ttu-id="16183-298">Mode d’insertion VI : `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="16183-298">Vi insert mode: `<Ctrl+y>`</span></span>
- <span data-ttu-id="16183-299">Mode de commande VI : `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="16183-299">Vi command mode: `<Ctrl+y>`</span></span>

### <a name="repeatlastcommand"></a><span data-ttu-id="16183-300">RepeatLastCommand</span><span class="sxs-lookup"><span data-stu-id="16183-300">RepeatLastCommand</span></span>

<span data-ttu-id="16183-301">Répète la dernière modification de texte.</span><span class="sxs-lookup"><span data-stu-id="16183-301">Repeat the last text modification.</span></span>

- <span data-ttu-id="16183-302">Mode de commande VI : `<.>`</span><span class="sxs-lookup"><span data-stu-id="16183-302">Vi command mode: `<.>`</span></span>

### <a name="revertline"></a><span data-ttu-id="16183-303">RevertLine</span><span class="sxs-lookup"><span data-stu-id="16183-303">RevertLine</span></span>

<span data-ttu-id="16183-304">Rétablit toutes les entrées de l’entrée actuelle.</span><span class="sxs-lookup"><span data-stu-id="16183-304">Reverts all of the input to the current input.</span></span>

- <span data-ttu-id="16183-305">Cmd `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="16183-305">Cmd: `<Escape>`</span></span>
- <span data-ttu-id="16183-306">Emacs- `<Alt+r>` , `<Escape,r>`</span><span class="sxs-lookup"><span data-stu-id="16183-306">Emacs: `<Alt+r>`, `<Escape,r>`</span></span>

### <a name="shellbackwardkillword"></a><span data-ttu-id="16183-307">ShellBackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="16183-307">ShellBackwardKillWord</span></span>

<span data-ttu-id="16183-308">Efface l’entrée du début du mot actuel jusqu’au curseur.</span><span class="sxs-lookup"><span data-stu-id="16183-308">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="16183-309">Si le curseur se trouve entre des mots, l’entrée est effacée du début du mot précédent au curseur.</span><span class="sxs-lookup"><span data-stu-id="16183-309">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="16183-310">Le texte effacé est placé dans le Kill-Ring.</span><span class="sxs-lookup"><span data-stu-id="16183-310">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="16183-311">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="16183-311">Function is unbound.</span></span>

### <a name="shellkillword"></a><span data-ttu-id="16183-312">ShellKillWord</span><span class="sxs-lookup"><span data-stu-id="16183-312">ShellKillWord</span></span>

<span data-ttu-id="16183-313">Efface l’entrée du curseur jusqu’à la fin du mot actuel.</span><span class="sxs-lookup"><span data-stu-id="16183-313">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="16183-314">Si le curseur se trouve entre des mots, l’entrée est effacée du curseur jusqu’à la fin du mot suivant.</span><span class="sxs-lookup"><span data-stu-id="16183-314">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="16183-315">Le texte effacé est placé dans le Kill-Ring.</span><span class="sxs-lookup"><span data-stu-id="16183-315">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="16183-316">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="16183-316">Function is unbound.</span></span>

### <a name="swapcharacters"></a><span data-ttu-id="16183-317">SwapCharacters</span><span class="sxs-lookup"><span data-stu-id="16183-317">SwapCharacters</span></span>

<span data-ttu-id="16183-318">Permuter le caractère actuel et celui qui le précèdent.</span><span class="sxs-lookup"><span data-stu-id="16183-318">Swap the current character and the one before it.</span></span>

- <span data-ttu-id="16183-319">Emacs- `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="16183-319">Emacs: `<Ctrl+t>`</span></span>
- <span data-ttu-id="16183-320">Mode d’insertion VI : `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="16183-320">Vi insert mode: `<Ctrl+t>`</span></span>
- <span data-ttu-id="16183-321">Mode de commande VI : `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="16183-321">Vi command mode: `<Ctrl+t>`</span></span>

### <a name="undo"></a><span data-ttu-id="16183-322">Annuler</span><span class="sxs-lookup"><span data-stu-id="16183-322">Undo</span></span>

<span data-ttu-id="16183-323">Annuler une modification précédente.</span><span class="sxs-lookup"><span data-stu-id="16183-323">Undo a previous edit.</span></span>

- <span data-ttu-id="16183-324">Cmd `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="16183-324">Cmd: `<Ctrl+z>`</span></span>
- <span data-ttu-id="16183-325">Emacs- `<Ctrl+_>` , `<Ctrl+x,Ctrl+u>`</span><span class="sxs-lookup"><span data-stu-id="16183-325">Emacs: `<Ctrl+_>`, `<Ctrl+x,Ctrl+u>`</span></span>
- <span data-ttu-id="16183-326">Mode d’insertion VI : `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="16183-326">Vi insert mode: `<Ctrl+z>`</span></span>
- <span data-ttu-id="16183-327">Mode de commande VI : `<Ctrl+z>` , `<u>`</span><span class="sxs-lookup"><span data-stu-id="16183-327">Vi command mode: `<Ctrl+z>`, `<u>`</span></span>

### <a name="undoall"></a><span data-ttu-id="16183-328">UndoAll</span><span class="sxs-lookup"><span data-stu-id="16183-328">UndoAll</span></span>

<span data-ttu-id="16183-329">Annule toutes les modifications précédentes pour la ligne.</span><span class="sxs-lookup"><span data-stu-id="16183-329">Undo all previous edits for line.</span></span>

- <span data-ttu-id="16183-330">Mode de commande VI : `<U>`</span><span class="sxs-lookup"><span data-stu-id="16183-330">Vi command mode: `<U>`</span></span>

### <a name="unixwordrubout"></a><span data-ttu-id="16183-331">UnixWordRubout</span><span class="sxs-lookup"><span data-stu-id="16183-331">UnixWordRubout</span></span>

<span data-ttu-id="16183-332">Efface l’entrée du début du mot actuel jusqu’au curseur.</span><span class="sxs-lookup"><span data-stu-id="16183-332">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="16183-333">Si le curseur se trouve entre des mots, l’entrée est effacée du début du mot précédent au curseur.</span><span class="sxs-lookup"><span data-stu-id="16183-333">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="16183-334">Le texte effacé est placé dans le Kill-Ring.</span><span class="sxs-lookup"><span data-stu-id="16183-334">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="16183-335">Emacs- `<Ctrl+w>`</span><span class="sxs-lookup"><span data-stu-id="16183-335">Emacs: `<Ctrl+w>`</span></span>

### <a name="validateandacceptline"></a><span data-ttu-id="16183-336">ValidateAndAcceptLine</span><span class="sxs-lookup"><span data-stu-id="16183-336">ValidateAndAcceptLine</span></span>

<span data-ttu-id="16183-337">Tentative d’exécution de l’entrée en cours.</span><span class="sxs-lookup"><span data-stu-id="16183-337">Attempt to execute the current input.</span></span> <span data-ttu-id="16183-338">Si l’entrée actuelle est incomplète (par exemple, il manque une parenthèse fermante, un crochet ou un guillemet, l’invite de continuation est affichée sur la ligne suivante et PSReadLine attend que les clés modifient l’entrée actuelle.</span><span class="sxs-lookup"><span data-stu-id="16183-338">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="16183-339">Emacs- `<Ctrl+m>`</span><span class="sxs-lookup"><span data-stu-id="16183-339">Emacs: `<Ctrl+m>`</span></span>

### <a name="viacceptline"></a><span data-ttu-id="16183-340">ViAcceptLine</span><span class="sxs-lookup"><span data-stu-id="16183-340">ViAcceptLine</span></span>

<span data-ttu-id="16183-341">Acceptez la ligne et passez en mode insertion.</span><span class="sxs-lookup"><span data-stu-id="16183-341">Accept the line and switch to Insert mode.</span></span>

- <span data-ttu-id="16183-342">Mode de commande VI : `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="16183-342">Vi command mode: `<Enter>`</span></span>

### <a name="viacceptlineorexit"></a><span data-ttu-id="16183-343">ViAcceptLineOrExit</span><span class="sxs-lookup"><span data-stu-id="16183-343">ViAcceptLineOrExit</span></span>

<span data-ttu-id="16183-344">Comme DeleteCharOrExit en mode emacs, mais accepte la ligne au lieu de supprimer un caractère.</span><span class="sxs-lookup"><span data-stu-id="16183-344">Like DeleteCharOrExit in Emacs mode, but accepts the line instead of deleting a character.</span></span>

- <span data-ttu-id="16183-345">Mode d’insertion VI : `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="16183-345">Vi insert mode: `<Ctrl+d>`</span></span>
- <span data-ttu-id="16183-346">Mode de commande VI : `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="16183-346">Vi command mode: `<Ctrl+d>`</span></span>

### <a name="viappendline"></a><span data-ttu-id="16183-347">ViAppendLine</span><span class="sxs-lookup"><span data-stu-id="16183-347">ViAppendLine</span></span>

<span data-ttu-id="16183-348">Une nouvelle ligne est insérée au-dessous de la ligne active.</span><span class="sxs-lookup"><span data-stu-id="16183-348">A new line is inserted below the current line.</span></span>

- <span data-ttu-id="16183-349">Mode de commande VI : `<o>`</span><span class="sxs-lookup"><span data-stu-id="16183-349">Vi command mode: `<o>`</span></span>

### <a name="vibackwarddeleteglob"></a><span data-ttu-id="16183-350">ViBackwardDeleteGlob</span><span class="sxs-lookup"><span data-stu-id="16183-350">ViBackwardDeleteGlob</span></span>

<span data-ttu-id="16183-351">Supprime le mot précédent, en utilisant uniquement un espace blanc comme délimiteur de mot.</span><span class="sxs-lookup"><span data-stu-id="16183-351">Deletes the previous word, using only white space as the word delimiter.</span></span>

- <span data-ttu-id="16183-352">Mode de commande VI : `<d,B>`</span><span class="sxs-lookup"><span data-stu-id="16183-352">Vi command mode: `<d,B>`</span></span>

### <a name="vibackwardglob"></a><span data-ttu-id="16183-353">ViBackwardGlob</span><span class="sxs-lookup"><span data-stu-id="16183-353">ViBackwardGlob</span></span>

<span data-ttu-id="16183-354">Déplace le curseur au début du mot précédent, en utilisant uniquement des espaces blancs comme délimiteurs.</span><span class="sxs-lookup"><span data-stu-id="16183-354">Moves the cursor back to the beginning of the previous word, using only white space as delimiters.</span></span>

- <span data-ttu-id="16183-355">Mode de commande VI : `<B>`</span><span class="sxs-lookup"><span data-stu-id="16183-355">Vi command mode: `<B>`</span></span>

### <a name="videletebrace"></a><span data-ttu-id="16183-356">ViDeleteBrace</span><span class="sxs-lookup"><span data-stu-id="16183-356">ViDeleteBrace</span></span>

<span data-ttu-id="16183-357">Recherchez l’accolade correspondante, la parenthèse ou le crochet, et supprimez tout le contenu dans, y compris l’accolade.</span><span class="sxs-lookup"><span data-stu-id="16183-357">Find the matching brace, parenthesis, or square bracket and delete all contents within, including the brace.</span></span>

- <span data-ttu-id="16183-358">Mode de commande VI : `<d,%>`</span><span class="sxs-lookup"><span data-stu-id="16183-358">Vi command mode: `<d,%>`</span></span>

### <a name="videleteendofglob"></a><span data-ttu-id="16183-359">ViDeleteEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="16183-359">ViDeleteEndOfGlob</span></span>

<span data-ttu-id="16183-360">Supprimer à la fin du mot.</span><span class="sxs-lookup"><span data-stu-id="16183-360">Delete to the end of the word.</span></span>

- <span data-ttu-id="16183-361">Mode de commande VI : `<d,E>`</span><span class="sxs-lookup"><span data-stu-id="16183-361">Vi command mode: `<d,E>`</span></span>

### <a name="videleteglob"></a><span data-ttu-id="16183-362">ViDeleteGlob</span><span class="sxs-lookup"><span data-stu-id="16183-362">ViDeleteGlob</span></span>

<span data-ttu-id="16183-363">Supprime la glob suivante (mot blanc délimité par des espaces).</span><span class="sxs-lookup"><span data-stu-id="16183-363">Delete the next glob (white space delimited word).</span></span>

- <span data-ttu-id="16183-364">Mode de commande VI : `<d,W>`</span><span class="sxs-lookup"><span data-stu-id="16183-364">Vi command mode: `<d,W>`</span></span>

### <a name="videletetobeforechar"></a><span data-ttu-id="16183-365">ViDeleteToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="16183-365">ViDeleteToBeforeChar</span></span>

<span data-ttu-id="16183-366">Supprime jusqu’au caractère donné.</span><span class="sxs-lookup"><span data-stu-id="16183-366">Deletes until given character.</span></span>

- <span data-ttu-id="16183-367">Mode de commande VI : `<d,t>`</span><span class="sxs-lookup"><span data-stu-id="16183-367">Vi command mode: `<d,t>`</span></span>

### <a name="videletetobeforecharbackward"></a><span data-ttu-id="16183-368">ViDeleteToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="16183-368">ViDeleteToBeforeCharBackward</span></span>

<span data-ttu-id="16183-369">Supprime jusqu’au caractère donné.</span><span class="sxs-lookup"><span data-stu-id="16183-369">Deletes until given character.</span></span>

- <span data-ttu-id="16183-370">Mode de commande VI : `<d,T>`</span><span class="sxs-lookup"><span data-stu-id="16183-370">Vi command mode: `<d,T>`</span></span>

### <a name="videletetochar"></a><span data-ttu-id="16183-371">ViDeleteToChar</span><span class="sxs-lookup"><span data-stu-id="16183-371">ViDeleteToChar</span></span>

<span data-ttu-id="16183-372">Supprime jusqu’au caractère donné.</span><span class="sxs-lookup"><span data-stu-id="16183-372">Deletes until given character.</span></span>

- <span data-ttu-id="16183-373">Mode de commande VI : `<d,f>`</span><span class="sxs-lookup"><span data-stu-id="16183-373">Vi command mode: `<d,f>`</span></span>

### <a name="videletetocharbackward"></a><span data-ttu-id="16183-374">ViDeleteToCharBackward</span><span class="sxs-lookup"><span data-stu-id="16183-374">ViDeleteToCharBackward</span></span>

<span data-ttu-id="16183-375">Supprime vers l’arrière jusqu’au caractère donné.</span><span class="sxs-lookup"><span data-stu-id="16183-375">Deletes backwards until given character.</span></span>

- <span data-ttu-id="16183-376">Mode de commande VI : `<d,F>`</span><span class="sxs-lookup"><span data-stu-id="16183-376">Vi command mode: `<d,F>`</span></span>

### <a name="viinsertatbegining"></a><span data-ttu-id="16183-377">ViInsertAtBegining</span><span class="sxs-lookup"><span data-stu-id="16183-377">ViInsertAtBegining</span></span>

<span data-ttu-id="16183-378">Basculez en mode insertion et positionnez le curseur au début de la ligne.</span><span class="sxs-lookup"><span data-stu-id="16183-378">Switch to Insert mode and position the cursor at the beginning of the line.</span></span>

- <span data-ttu-id="16183-379">Mode de commande VI : `<I>`</span><span class="sxs-lookup"><span data-stu-id="16183-379">Vi command mode: `<I>`</span></span>

### <a name="viinsertatend"></a><span data-ttu-id="16183-380">ViInsertAtEnd</span><span class="sxs-lookup"><span data-stu-id="16183-380">ViInsertAtEnd</span></span>

<span data-ttu-id="16183-381">Basculez en mode insertion et positionnez le curseur à la fin de la ligne.</span><span class="sxs-lookup"><span data-stu-id="16183-381">Switch to Insert mode and position the cursor at the end of the line.</span></span>

- <span data-ttu-id="16183-382">Mode de commande VI : `<A>`</span><span class="sxs-lookup"><span data-stu-id="16183-382">Vi command mode: `<A>`</span></span>

### <a name="viinsertline"></a><span data-ttu-id="16183-383">ViInsertLine</span><span class="sxs-lookup"><span data-stu-id="16183-383">ViInsertLine</span></span>

<span data-ttu-id="16183-384">Une nouvelle ligne est insérée au-dessus de la ligne active.</span><span class="sxs-lookup"><span data-stu-id="16183-384">A new line is inserted above the current line.</span></span>

- <span data-ttu-id="16183-385">Mode de commande VI : `<O>`</span><span class="sxs-lookup"><span data-stu-id="16183-385">Vi command mode: `<O>`</span></span>

### <a name="viinsertwithappend"></a><span data-ttu-id="16183-386">ViInsertWithAppend</span><span class="sxs-lookup"><span data-stu-id="16183-386">ViInsertWithAppend</span></span>

<span data-ttu-id="16183-387">Ajouter à partir de la position de la ligne active.</span><span class="sxs-lookup"><span data-stu-id="16183-387">Append from the current line position.</span></span>

- <span data-ttu-id="16183-388">Mode de commande VI : `<a>`</span><span class="sxs-lookup"><span data-stu-id="16183-388">Vi command mode: `<a>`</span></span>

### <a name="viinsertwithdelete"></a><span data-ttu-id="16183-389">ViInsertWithDelete</span><span class="sxs-lookup"><span data-stu-id="16183-389">ViInsertWithDelete</span></span>

<span data-ttu-id="16183-390">Supprimez le caractère actuel et basculez en mode insertion.</span><span class="sxs-lookup"><span data-stu-id="16183-390">Delete the current character and switch to Insert mode.</span></span>

- <span data-ttu-id="16183-391">Mode de commande VI : `<s>`</span><span class="sxs-lookup"><span data-stu-id="16183-391">Vi command mode: `<s>`</span></span>

### <a name="vijoinlines"></a><span data-ttu-id="16183-392">ViJoinLines</span><span class="sxs-lookup"><span data-stu-id="16183-392">ViJoinLines</span></span>

<span data-ttu-id="16183-393">Joint la ligne active et la ligne suivante.</span><span class="sxs-lookup"><span data-stu-id="16183-393">Joins the current line and the next line.</span></span>

- <span data-ttu-id="16183-394">Mode de commande VI : `<J>`</span><span class="sxs-lookup"><span data-stu-id="16183-394">Vi command mode: `<J>`</span></span>

### <a name="vireplaceline"></a><span data-ttu-id="16183-395">ViReplaceLine</span><span class="sxs-lookup"><span data-stu-id="16183-395">ViReplaceLine</span></span>

<span data-ttu-id="16183-396">Effacez l’intégralité de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="16183-396">Erase the entire command line.</span></span>

- <span data-ttu-id="16183-397">Mode de commande VI : `<S>` , `<c,c>`</span><span class="sxs-lookup"><span data-stu-id="16183-397">Vi command mode: `<S>`, `<c,c>`</span></span>

### <a name="vireplacetobeforechar"></a><span data-ttu-id="16183-398">ViReplaceToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="16183-398">ViReplaceToBeforeChar</span></span>

<span data-ttu-id="16183-399">Remplace jusqu’au caractère donné.</span><span class="sxs-lookup"><span data-stu-id="16183-399">Replaces until given character.</span></span>

- <span data-ttu-id="16183-400">Mode de commande VI : `<c,t>`</span><span class="sxs-lookup"><span data-stu-id="16183-400">Vi command mode: `<c,t>`</span></span>

### <a name="vireplacetobeforecharbackward"></a><span data-ttu-id="16183-401">ViReplaceToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="16183-401">ViReplaceToBeforeCharBackward</span></span>

<span data-ttu-id="16183-402">Remplace jusqu’au caractère donné.</span><span class="sxs-lookup"><span data-stu-id="16183-402">Replaces until given character.</span></span>

- <span data-ttu-id="16183-403">Mode de commande VI : `<c,T>`</span><span class="sxs-lookup"><span data-stu-id="16183-403">Vi command mode: `<c,T>`</span></span>

### <a name="vireplacetochar"></a><span data-ttu-id="16183-404">ViReplaceToChar</span><span class="sxs-lookup"><span data-stu-id="16183-404">ViReplaceToChar</span></span>

<span data-ttu-id="16183-405">Supprime jusqu’au caractère donné.</span><span class="sxs-lookup"><span data-stu-id="16183-405">Deletes until given character.</span></span>

- <span data-ttu-id="16183-406">Mode de commande VI : `<c,f>`</span><span class="sxs-lookup"><span data-stu-id="16183-406">Vi command mode: `<c,f>`</span></span>

### <a name="vireplacetocharbackward"></a><span data-ttu-id="16183-407">ViReplaceToCharBackward</span><span class="sxs-lookup"><span data-stu-id="16183-407">ViReplaceToCharBackward</span></span>

<span data-ttu-id="16183-408">Remplace jusqu’au caractère donné.</span><span class="sxs-lookup"><span data-stu-id="16183-408">Replaces until given character.</span></span>

- <span data-ttu-id="16183-409">Mode de commande VI : `<c,F>`</span><span class="sxs-lookup"><span data-stu-id="16183-409">Vi command mode: `<c,F>`</span></span>

### <a name="viyankbeginningofline"></a><span data-ttu-id="16183-410">ViYankBeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="16183-410">ViYankBeginningOfLine</span></span>

<span data-ttu-id="16183-411">Yank entre le début de la mémoire tampon et le curseur.</span><span class="sxs-lookup"><span data-stu-id="16183-411">Yank from the beginning of the buffer to the cursor.</span></span>

- <span data-ttu-id="16183-412">Mode de commande VI : `<y,0>`</span><span class="sxs-lookup"><span data-stu-id="16183-412">Vi command mode: `<y,0>`</span></span>

### <a name="viyankendofglob"></a><span data-ttu-id="16183-413">ViYankEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="16183-413">ViYankEndOfGlob</span></span>

<span data-ttu-id="16183-414">Yank du curseur jusqu’à la fin du ou des mots.</span><span class="sxs-lookup"><span data-stu-id="16183-414">Yank from the cursor to the end of the WORD(s).</span></span>

- <span data-ttu-id="16183-415">Mode de commande VI : `<y,E>`</span><span class="sxs-lookup"><span data-stu-id="16183-415">Vi command mode: `<y,E>`</span></span>

### <a name="viyankendofword"></a><span data-ttu-id="16183-416">ViYankEndOfWord</span><span class="sxs-lookup"><span data-stu-id="16183-416">ViYankEndOfWord</span></span>

<span data-ttu-id="16183-417">Yank du curseur jusqu’à la fin du ou des mots.</span><span class="sxs-lookup"><span data-stu-id="16183-417">Yank from the cursor to the end of the word(s).</span></span>

- <span data-ttu-id="16183-418">Mode de commande VI : `<y,e>`</span><span class="sxs-lookup"><span data-stu-id="16183-418">Vi command mode: `<y,e>`</span></span>

### <a name="viyankleft"></a><span data-ttu-id="16183-419">ViYankLeft</span><span class="sxs-lookup"><span data-stu-id="16183-419">ViYankLeft</span></span>

<span data-ttu-id="16183-420">Yank caractère (s) à gauche du curseur.</span><span class="sxs-lookup"><span data-stu-id="16183-420">Yank character(s) to the left of the cursor.</span></span>

- <span data-ttu-id="16183-421">Mode de commande VI : `<y,h>`</span><span class="sxs-lookup"><span data-stu-id="16183-421">Vi command mode: `<y,h>`</span></span>

### <a name="viyankline"></a><span data-ttu-id="16183-422">ViYankLine</span><span class="sxs-lookup"><span data-stu-id="16183-422">ViYankLine</span></span>

<span data-ttu-id="16183-423">Yank la mémoire tampon entière.</span><span class="sxs-lookup"><span data-stu-id="16183-423">Yank the entire buffer.</span></span>

- <span data-ttu-id="16183-424">Mode de commande VI : `<y,y>`</span><span class="sxs-lookup"><span data-stu-id="16183-424">Vi command mode: `<y,y>`</span></span>

### <a name="viyanknextglob"></a><span data-ttu-id="16183-425">ViYankNextGlob</span><span class="sxs-lookup"><span data-stu-id="16183-425">ViYankNextGlob</span></span>

<span data-ttu-id="16183-426">Yank à partir d’un curseur jusqu’au début du ou des mots suivants.</span><span class="sxs-lookup"><span data-stu-id="16183-426">Yank from cursor to the start of the next WORD(s).</span></span>

- <span data-ttu-id="16183-427">Mode de commande VI : `<y,W>`</span><span class="sxs-lookup"><span data-stu-id="16183-427">Vi command mode: `<y,W>`</span></span>

### <a name="viyanknextword"></a><span data-ttu-id="16183-428">ViYankNextWord</span><span class="sxs-lookup"><span data-stu-id="16183-428">ViYankNextWord</span></span>

<span data-ttu-id="16183-429">Yank le ou les mots après le curseur.</span><span class="sxs-lookup"><span data-stu-id="16183-429">Yank the word(s) after the cursor.</span></span>

- <span data-ttu-id="16183-430">Mode de commande VI : `<y,w>`</span><span class="sxs-lookup"><span data-stu-id="16183-430">Vi command mode: `<y,w>`</span></span>

### <a name="viyankpercent"></a><span data-ttu-id="16183-431">ViYankPercent</span><span class="sxs-lookup"><span data-stu-id="16183-431">ViYankPercent</span></span>

<span data-ttu-id="16183-432">Yank à/à partir de l’accolade correspondante.</span><span class="sxs-lookup"><span data-stu-id="16183-432">Yank to/from matching brace.</span></span>

- <span data-ttu-id="16183-433">Mode de commande VI : `<y,%>`</span><span class="sxs-lookup"><span data-stu-id="16183-433">Vi command mode: `<y,%>`</span></span>

### <a name="viyankpreviousglob"></a><span data-ttu-id="16183-434">ViYankPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="16183-434">ViYankPreviousGlob</span></span>

<span data-ttu-id="16183-435">Yank entre le début du ou des mots et le curseur.</span><span class="sxs-lookup"><span data-stu-id="16183-435">Yank from beginning of the WORD(s) to cursor.</span></span>

- <span data-ttu-id="16183-436">Mode de commande VI : `<y,B>`</span><span class="sxs-lookup"><span data-stu-id="16183-436">Vi command mode: `<y,B>`</span></span>

### <a name="viyankpreviousword"></a><span data-ttu-id="16183-437">ViYankPreviousWord</span><span class="sxs-lookup"><span data-stu-id="16183-437">ViYankPreviousWord</span></span>

<span data-ttu-id="16183-438">Yank le ou les mots avant le curseur.</span><span class="sxs-lookup"><span data-stu-id="16183-438">Yank the word(s) before the cursor.</span></span>

- <span data-ttu-id="16183-439">Mode de commande VI : `<y,b>`</span><span class="sxs-lookup"><span data-stu-id="16183-439">Vi command mode: `<y,b>`</span></span>

### <a name="viyankright"></a><span data-ttu-id="16183-440">ViYankRight</span><span class="sxs-lookup"><span data-stu-id="16183-440">ViYankRight</span></span>

<span data-ttu-id="16183-441">Yank caractère (s) situé sous et à droite du curseur.</span><span class="sxs-lookup"><span data-stu-id="16183-441">Yank character(s) under and to the right of the cursor.</span></span>

- <span data-ttu-id="16183-442">Mode de commande VI : `<y,l>` , `<y,Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="16183-442">Vi command mode: `<y,l>`, `<y,Spacebar>`</span></span>

### <a name="viyanktoendofline"></a><span data-ttu-id="16183-443">ViYankToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="16183-443">ViYankToEndOfLine</span></span>

<span data-ttu-id="16183-444">Yank du curseur jusqu’à la fin de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="16183-444">Yank from the cursor to the end of the buffer.</span></span>

- <span data-ttu-id="16183-445">Mode de commande VI : `<y,$>`</span><span class="sxs-lookup"><span data-stu-id="16183-445">Vi command mode: `<y,$>`</span></span>

### <a name="viyanktofirstchar"></a><span data-ttu-id="16183-446">ViYankToFirstChar</span><span class="sxs-lookup"><span data-stu-id="16183-446">ViYankToFirstChar</span></span>

<span data-ttu-id="16183-447">Yank du premier caractère autre qu’un espace blanc au curseur.</span><span class="sxs-lookup"><span data-stu-id="16183-447">Yank from the first non-whitespace character to the cursor.</span></span>

- <span data-ttu-id="16183-448">Mode de commande VI : `<y,^>`</span><span class="sxs-lookup"><span data-stu-id="16183-448">Vi command mode: `<y,^>`</span></span>

### <a name="yank"></a><span data-ttu-id="16183-449">Yank</span><span class="sxs-lookup"><span data-stu-id="16183-449">Yank</span></span>

<span data-ttu-id="16183-450">Ajoutez le texte le plus récemment supprimé à l’entrée.</span><span class="sxs-lookup"><span data-stu-id="16183-450">Add the most recently killed text to the input.</span></span>

- <span data-ttu-id="16183-451">Emacs- `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="16183-451">Emacs: `<Ctrl+y>`</span></span>

### <a name="yanklastarg"></a><span data-ttu-id="16183-452">YankLastArg</span><span class="sxs-lookup"><span data-stu-id="16183-452">YankLastArg</span></span>

<span data-ttu-id="16183-453">Yank le dernier argument de la ligne d’historique précédente.</span><span class="sxs-lookup"><span data-stu-id="16183-453">Yank the last argument from the previous history line.</span></span> <span data-ttu-id="16183-454">Avec un argument, la première fois qu’il est appelé, se comporte comme YankNthArg.</span><span class="sxs-lookup"><span data-stu-id="16183-454">With an argument, the first time it is invoked, behaves just like YankNthArg.</span></span> <span data-ttu-id="16183-455">Si elle est appelée plusieurs fois, elle itère au sein de l’historique et ARG définit la direction (négatif inverse la direction).</span><span class="sxs-lookup"><span data-stu-id="16183-455">If invoked multiple times, instead it iterates through history and arg sets the direction (negative reverses the direction.)</span></span>

- <span data-ttu-id="16183-456">Cmd `<Alt+.>`</span><span class="sxs-lookup"><span data-stu-id="16183-456">Cmd: `<Alt+.>`</span></span>
- <span data-ttu-id="16183-457">Emacs : `<Alt+.>` , `<Alt+_>` , `<Escape,.>` , `<Escape,_>`</span><span class="sxs-lookup"><span data-stu-id="16183-457">Emacs: `<Alt+.>`, `<Alt+_>`, `<Escape,.>`, `<Escape,_>`</span></span>

### <a name="yankntharg"></a><span data-ttu-id="16183-458">YankNthArg</span><span class="sxs-lookup"><span data-stu-id="16183-458">YankNthArg</span></span>

<span data-ttu-id="16183-459">Yank le premier argument (après la commande) à partir de la ligne précédente de l’historique.</span><span class="sxs-lookup"><span data-stu-id="16183-459">Yank the first argument (after the command) from the previous history line.</span></span>
<span data-ttu-id="16183-460">Avec un argument, Yank le nième argument (à partir de 0), si l’argument est négatif, commencez par le dernier argument.</span><span class="sxs-lookup"><span data-stu-id="16183-460">With an argument, yank the nth argument (starting from 0), if the argument is negative, start from the last argument.</span></span>

- <span data-ttu-id="16183-461">Emacs- `<Ctrl+Alt+y>` , `<Escape,Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="16183-461">Emacs: `<Ctrl+Alt+y>`, `<Escape,Ctrl+y>`</span></span>

### <a name="yankpop"></a><span data-ttu-id="16183-462">YankPop</span><span class="sxs-lookup"><span data-stu-id="16183-462">YankPop</span></span>

<span data-ttu-id="16183-463">Si l’opération précédente était Yank ou YankPop, remplacez le texte précédemment extrait par le texte supprimé suivant de l’instruction KILL-Ring.</span><span class="sxs-lookup"><span data-stu-id="16183-463">If the previous operation was Yank or YankPop, replace the previously yanked text with the next killed text from the kill-ring.</span></span>

- <span data-ttu-id="16183-464">Emacs- `<Alt+y>` , `<Escape,y>`</span><span class="sxs-lookup"><span data-stu-id="16183-464">Emacs: `<Alt+y>`, `<Escape,y>`</span></span>

## <a name="cursor-movement-functions"></a><span data-ttu-id="16183-465">Fonctions de déplacement de curseur</span><span class="sxs-lookup"><span data-stu-id="16183-465">Cursor movement functions</span></span>

### <a name="backwardchar"></a><span data-ttu-id="16183-466">BackwardChar</span><span class="sxs-lookup"><span data-stu-id="16183-466">BackwardChar</span></span>

<span data-ttu-id="16183-467">Déplacer le curseur d’un caractère vers la gauche.</span><span class="sxs-lookup"><span data-stu-id="16183-467">Move the cursor one character to the left.</span></span> <span data-ttu-id="16183-468">Cela peut déplacer le curseur vers la ligne précédente de l’entrée multiligne.</span><span class="sxs-lookup"><span data-stu-id="16183-468">This may move the cursor to the previous line of multi-line input.</span></span>

- <span data-ttu-id="16183-469">Cmd `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="16183-469">Cmd: `<LeftArrow>`</span></span>
- <span data-ttu-id="16183-470">Emacs- `<LeftArrow>` , `<Ctrl+b>`</span><span class="sxs-lookup"><span data-stu-id="16183-470">Emacs: `<LeftArrow>`, `<Ctrl+b>`</span></span>

### <a name="backwardword"></a><span data-ttu-id="16183-471">BackwardWord</span><span class="sxs-lookup"><span data-stu-id="16183-471">BackwardWord</span></span>

<span data-ttu-id="16183-472">Ramener le curseur au début du mot actuel, ou si entre les mots, le début du mot précédent.</span><span class="sxs-lookup"><span data-stu-id="16183-472">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="16183-473">Les limites de mots sont définies par un jeu de caractères configurable.</span><span class="sxs-lookup"><span data-stu-id="16183-473">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="16183-474">Cmd `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="16183-474">Cmd: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="16183-475">Emacs- `<Alt+b>` , `<Escape,b>`</span><span class="sxs-lookup"><span data-stu-id="16183-475">Emacs: `<Alt+b>`, `<Escape,b>`</span></span>
- <span data-ttu-id="16183-476">Mode d’insertion VI : `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="16183-476">Vi insert mode: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="16183-477">Mode de commande VI : `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="16183-477">Vi command mode: `<Ctrl+LeftArrow>`</span></span>

### <a name="beginningofline"></a><span data-ttu-id="16183-478">BeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="16183-478">BeginningOfLine</span></span>

<span data-ttu-id="16183-479">Si l’entrée comporte plusieurs lignes, se déplacer au début de la ligne active ou, le cas échéant, au début de la ligne, se déplacer au début de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="16183-479">If the input has multiple lines, move to the start of the current line, or if already at the start of the line, move to the start of the input.</span></span> <span data-ttu-id="16183-480">Si l’entrée comporte une seule ligne, accédez au début de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="16183-480">If the input has a single line, move to the start of the input.</span></span>

- <span data-ttu-id="16183-481">Cmd `<Home>`</span><span class="sxs-lookup"><span data-stu-id="16183-481">Cmd: `<Home>`</span></span>
- <span data-ttu-id="16183-482">Emacs- `<Home>` , `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="16183-482">Emacs: `<Home>`, `<Ctrl+a>`</span></span>
- <span data-ttu-id="16183-483">Mode d’insertion VI : `<Home>`</span><span class="sxs-lookup"><span data-stu-id="16183-483">Vi insert mode: `<Home>`</span></span>
- <span data-ttu-id="16183-484">Mode de commande VI : `<Home>`</span><span class="sxs-lookup"><span data-stu-id="16183-484">Vi command mode: `<Home>`</span></span>

### <a name="endofline"></a><span data-ttu-id="16183-485">EndOfLine</span><span class="sxs-lookup"><span data-stu-id="16183-485">EndOfLine</span></span>

<span data-ttu-id="16183-486">Si l’entrée comporte plusieurs lignes, passez à la fin de la ligne active ou, si elle se trouve déjà à la fin de la ligne, à la fin de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="16183-486">If the input has multiple lines, move to the end of the current line, or if already at the end of the line, move to the end of the input.</span></span> <span data-ttu-id="16183-487">Si l’entrée comporte une seule ligne, passez à la fin de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="16183-487">If the input has a single line, move to the end of the input.</span></span>

- <span data-ttu-id="16183-488">Cmd `<End>`</span><span class="sxs-lookup"><span data-stu-id="16183-488">Cmd: `<End>`</span></span>
- <span data-ttu-id="16183-489">Emacs- `<End>` , `<Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="16183-489">Emacs: `<End>`, `<Ctrl+e>`</span></span>
- <span data-ttu-id="16183-490">Mode d’insertion VI : `<End>`</span><span class="sxs-lookup"><span data-stu-id="16183-490">Vi insert mode: `<End>`</span></span>

### <a name="forwardchar"></a><span data-ttu-id="16183-491">ForwardChar</span><span class="sxs-lookup"><span data-stu-id="16183-491">ForwardChar</span></span>

<span data-ttu-id="16183-492">Déplacer le curseur d’un caractère vers la droite.</span><span class="sxs-lookup"><span data-stu-id="16183-492">Move the cursor one character to the right.</span></span> <span data-ttu-id="16183-493">Cela peut déplacer le curseur à la ligne suivante de l’entrée multiligne.</span><span class="sxs-lookup"><span data-stu-id="16183-493">This may move the cursor to the next line of multi-line input.</span></span>

- <span data-ttu-id="16183-494">Cmd `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="16183-494">Cmd: `<RightArrow>`</span></span>
- <span data-ttu-id="16183-495">Emacs- `<RightArrow>` , `<Ctrl+f>`</span><span class="sxs-lookup"><span data-stu-id="16183-495">Emacs: `<RightArrow>`, `<Ctrl+f>`</span></span>

### <a name="forwardword"></a><span data-ttu-id="16183-496">ForwardWord</span><span class="sxs-lookup"><span data-stu-id="16183-496">ForwardWord</span></span>

<span data-ttu-id="16183-497">Déplacer le curseur vers l’avant jusqu’à la fin du mot actuel, ou si entre les mots, à la fin du mot suivant.</span><span class="sxs-lookup"><span data-stu-id="16183-497">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="16183-498">Les limites de mots sont définies par un jeu de caractères configurable.</span><span class="sxs-lookup"><span data-stu-id="16183-498">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="16183-499">Emacs- `<Alt+f>` , `<Escape,f>`</span><span class="sxs-lookup"><span data-stu-id="16183-499">Emacs: `<Alt+f>`, `<Escape,f>`</span></span>

### <a name="gotobrace"></a><span data-ttu-id="16183-500">GotoBrace</span><span class="sxs-lookup"><span data-stu-id="16183-500">GotoBrace</span></span>

<span data-ttu-id="16183-501">Atteindre l’accolade correspondante, les parenthèses ou les crochets.</span><span class="sxs-lookup"><span data-stu-id="16183-501">Go to the matching brace, parenthesis, or square bracket.</span></span>

- <span data-ttu-id="16183-502">Cmd `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="16183-502">Cmd: `<Ctrl+]>`</span></span>
- <span data-ttu-id="16183-503">Mode d’insertion VI : `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="16183-503">Vi insert mode: `<Ctrl+]>`</span></span>
- <span data-ttu-id="16183-504">Mode de commande VI : `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="16183-504">Vi command mode: `<Ctrl+]>`</span></span>

### <a name="gotocolumn"></a><span data-ttu-id="16183-505">GotoColumn</span><span class="sxs-lookup"><span data-stu-id="16183-505">GotoColumn</span></span>

<span data-ttu-id="16183-506">Accédez à la colonne indiquée par arg.</span><span class="sxs-lookup"><span data-stu-id="16183-506">Move to the column indicated by arg.</span></span>

- <span data-ttu-id="16183-507">Mode de commande VI : `<|>`</span><span class="sxs-lookup"><span data-stu-id="16183-507">Vi command mode: `<|>`</span></span>

### <a name="gotofirstnonblankofline"></a><span data-ttu-id="16183-508">GotoFirstNonBlankOfLine</span><span class="sxs-lookup"><span data-stu-id="16183-508">GotoFirstNonBlankOfLine</span></span>

<span data-ttu-id="16183-509">Placez le curseur sur le premier caractère non vide de la ligne.</span><span class="sxs-lookup"><span data-stu-id="16183-509">Move the cursor to the first non-blank character in the line.</span></span>

- <span data-ttu-id="16183-510">Mode de commande VI : `<^>` , `<_>`</span><span class="sxs-lookup"><span data-stu-id="16183-510">Vi command mode: `<^>`, `<_>`</span></span>

### <a name="movetoendofline"></a><span data-ttu-id="16183-511">MoveToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="16183-511">MoveToEndOfLine</span></span>

<span data-ttu-id="16183-512">Placez le curseur à la fin de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="16183-512">Move the cursor to the end of the input.</span></span>

- <span data-ttu-id="16183-513">Mode de commande VI : `<End>` , `<$>`</span><span class="sxs-lookup"><span data-stu-id="16183-513">Vi command mode: `<End>`, `<$>`</span></span>

### <a name="nextline"></a><span data-ttu-id="16183-514">NextLine</span><span class="sxs-lookup"><span data-stu-id="16183-514">NextLine</span></span>

<span data-ttu-id="16183-515">Déplacer le curseur sur la ligne suivante.</span><span class="sxs-lookup"><span data-stu-id="16183-515">Move the cursor to the next line.</span></span>

- <span data-ttu-id="16183-516">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="16183-516">Function is unbound.</span></span>

### <a name="nextword"></a><span data-ttu-id="16183-517">NextWord</span><span class="sxs-lookup"><span data-stu-id="16183-517">NextWord</span></span>

<span data-ttu-id="16183-518">Déplacer le curseur vers l’avant jusqu’au début du mot suivant.</span><span class="sxs-lookup"><span data-stu-id="16183-518">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="16183-519">Les limites de mots sont définies par un jeu de caractères configurable.</span><span class="sxs-lookup"><span data-stu-id="16183-519">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="16183-520">Cmd `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="16183-520">Cmd: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="16183-521">Mode d’insertion VI : `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="16183-521">Vi insert mode: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="16183-522">Mode de commande VI : `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="16183-522">Vi command mode: `<Ctrl+RightArrow>`</span></span>

### <a name="nextwordend"></a><span data-ttu-id="16183-523">NextWordEnd</span><span class="sxs-lookup"><span data-stu-id="16183-523">NextWordEnd</span></span>

<span data-ttu-id="16183-524">Déplacer le curseur vers l’avant jusqu’à la fin du mot actuel, ou si entre les mots, à la fin du mot suivant.</span><span class="sxs-lookup"><span data-stu-id="16183-524">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="16183-525">Les limites de mots sont définies par un jeu de caractères configurable.</span><span class="sxs-lookup"><span data-stu-id="16183-525">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="16183-526">Mode de commande VI : `<e>`</span><span class="sxs-lookup"><span data-stu-id="16183-526">Vi command mode: `<e>`</span></span>

### <a name="previousline"></a><span data-ttu-id="16183-527">PreviousLine</span><span class="sxs-lookup"><span data-stu-id="16183-527">PreviousLine</span></span>

<span data-ttu-id="16183-528">Placez le curseur sur la ligne précédente.</span><span class="sxs-lookup"><span data-stu-id="16183-528">Move the cursor to the previous line.</span></span>

- <span data-ttu-id="16183-529">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="16183-529">Function is unbound.</span></span>

### <a name="shellbackwardword"></a><span data-ttu-id="16183-530">ShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="16183-530">ShellBackwardWord</span></span>

<span data-ttu-id="16183-531">Ramener le curseur au début du mot actuel, ou si entre les mots, le début du mot précédent.</span><span class="sxs-lookup"><span data-stu-id="16183-531">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="16183-532">Les limites de mots sont définies par les jetons PowerShell.</span><span class="sxs-lookup"><span data-stu-id="16183-532">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="16183-533">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="16183-533">Function is unbound.</span></span>

### <a name="shellforwardword"></a><span data-ttu-id="16183-534">ShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="16183-534">ShellForwardWord</span></span>

<span data-ttu-id="16183-535">Déplacer le curseur vers l’avant jusqu’au début du mot suivant.</span><span class="sxs-lookup"><span data-stu-id="16183-535">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="16183-536">Les limites de mots sont définies par les jetons PowerShell.</span><span class="sxs-lookup"><span data-stu-id="16183-536">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="16183-537">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="16183-537">Function is unbound.</span></span>

### <a name="shellnextword"></a><span data-ttu-id="16183-538">ShellNextWord</span><span class="sxs-lookup"><span data-stu-id="16183-538">ShellNextWord</span></span>

<span data-ttu-id="16183-539">Déplacer le curseur vers l’avant jusqu’à la fin du mot actuel, ou si entre les mots, à la fin du mot suivant.</span><span class="sxs-lookup"><span data-stu-id="16183-539">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="16183-540">Les limites de mots sont définies par les jetons PowerShell.</span><span class="sxs-lookup"><span data-stu-id="16183-540">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="16183-541">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="16183-541">Function is unbound.</span></span>

### <a name="vibackwardchar"></a><span data-ttu-id="16183-542">ViBackwardChar</span><span class="sxs-lookup"><span data-stu-id="16183-542">ViBackwardChar</span></span>

<span data-ttu-id="16183-543">Déplacer le curseur d’un caractère vers la gauche en mode d’édition VI.</span><span class="sxs-lookup"><span data-stu-id="16183-543">Move the cursor one character to the left in the Vi edit mode.</span></span> <span data-ttu-id="16183-544">Cela peut déplacer le curseur vers la ligne précédente de l’entrée multiligne.</span><span class="sxs-lookup"><span data-stu-id="16183-544">This may move the cursor to the previous line of multi-line input.</span></span>

- <span data-ttu-id="16183-545">Mode d’insertion VI : `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="16183-545">Vi insert mode: `<LeftArrow>`</span></span>
- <span data-ttu-id="16183-546">Mode de commande VI : `<LeftArrow>` , `<Backspace>` , `<h>`</span><span class="sxs-lookup"><span data-stu-id="16183-546">Vi command mode: `<LeftArrow>`, `<Backspace>`, `<h>`</span></span>

### <a name="vibackwardword"></a><span data-ttu-id="16183-547">ViBackwardWord</span><span class="sxs-lookup"><span data-stu-id="16183-547">ViBackwardWord</span></span>

<span data-ttu-id="16183-548">Ramener le curseur au début du mot actuel, ou si entre les mots, le début du mot précédent.</span><span class="sxs-lookup"><span data-stu-id="16183-548">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="16183-549">Les limites de mots sont définies par un jeu de caractères configurable.</span><span class="sxs-lookup"><span data-stu-id="16183-549">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="16183-550">Mode de commande VI : `<b>`</span><span class="sxs-lookup"><span data-stu-id="16183-550">Vi command mode: `<b>`</span></span>

### <a name="viforwardchar"></a><span data-ttu-id="16183-551">ViForwardChar</span><span class="sxs-lookup"><span data-stu-id="16183-551">ViForwardChar</span></span>

<span data-ttu-id="16183-552">Déplacer le curseur d’un caractère vers la droite en mode d’édition VI.</span><span class="sxs-lookup"><span data-stu-id="16183-552">Move the cursor one character to the right in the Vi edit mode.</span></span> <span data-ttu-id="16183-553">Cela peut déplacer le curseur à la ligne suivante de l’entrée multiligne.</span><span class="sxs-lookup"><span data-stu-id="16183-553">This may move the cursor to the next line of multi-line input.</span></span>

- <span data-ttu-id="16183-554">Mode d’insertion VI : `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="16183-554">Vi insert mode: `<RightArrow>`</span></span>
- <span data-ttu-id="16183-555">Mode de commande VI : `<RightArrow>` , `<Spacebar>` , `<l>`</span><span class="sxs-lookup"><span data-stu-id="16183-555">Vi command mode: `<RightArrow>`, `<Spacebar>`, `<l>`</span></span>

### <a name="viendofglob"></a><span data-ttu-id="16183-556">ViEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="16183-556">ViEndOfGlob</span></span>

<span data-ttu-id="16183-557">Déplace le curseur à la fin du mot, en utilisant uniquement des espaces blancs comme délimiteurs.</span><span class="sxs-lookup"><span data-stu-id="16183-557">Moves the cursor to the end of the word, using only white space as delimiters.</span></span>

- <span data-ttu-id="16183-558">Mode de commande VI : `<E>`</span><span class="sxs-lookup"><span data-stu-id="16183-558">Vi command mode: `<E>`</span></span>

### <a name="viendofpreviousglob"></a><span data-ttu-id="16183-559">ViEndOfPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="16183-559">ViEndOfPreviousGlob</span></span>

<span data-ttu-id="16183-560">Passe à la fin du mot précédent, en utilisant uniquement un espace blanc comme délimiteur de mot.</span><span class="sxs-lookup"><span data-stu-id="16183-560">Moves to the end of the previous word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="16183-561">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="16183-561">Function is unbound.</span></span>

### <a name="vigotobrace"></a><span data-ttu-id="16183-562">ViGotoBrace</span><span class="sxs-lookup"><span data-stu-id="16183-562">ViGotoBrace</span></span>

<span data-ttu-id="16183-563">Semblable à GotoBrace, mais est basé sur un caractère et non sur un jeton.</span><span class="sxs-lookup"><span data-stu-id="16183-563">Similar to GotoBrace, but is character based instead of token based.</span></span>

- <span data-ttu-id="16183-564">Mode de commande VI : `<%>`</span><span class="sxs-lookup"><span data-stu-id="16183-564">Vi command mode: `<%>`</span></span>

### <a name="vinextglob"></a><span data-ttu-id="16183-565">ViNextGlob</span><span class="sxs-lookup"><span data-stu-id="16183-565">ViNextGlob</span></span>

<span data-ttu-id="16183-566">Passe au mot suivant, en utilisant uniquement un espace blanc comme délimiteur de mot.</span><span class="sxs-lookup"><span data-stu-id="16183-566">Moves to the next word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="16183-567">Mode de commande VI : `<W>`</span><span class="sxs-lookup"><span data-stu-id="16183-567">Vi command mode: `<W>`</span></span>

### <a name="vinextword"></a><span data-ttu-id="16183-568">ViNextWord</span><span class="sxs-lookup"><span data-stu-id="16183-568">ViNextWord</span></span>

<span data-ttu-id="16183-569">Déplacer le curseur vers l’avant jusqu’au début du mot suivant.</span><span class="sxs-lookup"><span data-stu-id="16183-569">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="16183-570">Les limites de mots sont définies par un jeu de caractères configurable.</span><span class="sxs-lookup"><span data-stu-id="16183-570">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="16183-571">Mode de commande VI : `<w>`</span><span class="sxs-lookup"><span data-stu-id="16183-571">Vi command mode: `<w>`</span></span>

## <a name="history-functions"></a><span data-ttu-id="16183-572">Fonctions d’historique</span><span class="sxs-lookup"><span data-stu-id="16183-572">History functions</span></span>

### <a name="beginningofhistory"></a><span data-ttu-id="16183-573">BeginningOfHistory</span><span class="sxs-lookup"><span data-stu-id="16183-573">BeginningOfHistory</span></span>

<span data-ttu-id="16183-574">Accéder au premier élément de l’historique.</span><span class="sxs-lookup"><span data-stu-id="16183-574">Move to the first item in the history.</span></span>

- <span data-ttu-id="16183-575">Emacs- `<Alt+<>`</span><span class="sxs-lookup"><span data-stu-id="16183-575">Emacs: `<Alt+<>`</span></span>

### <a name="clearhistory"></a><span data-ttu-id="16183-576">ClearHistory</span><span class="sxs-lookup"><span data-stu-id="16183-576">ClearHistory</span></span>

<span data-ttu-id="16183-577">Efface l’historique dans PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="16183-577">Clears history in PSReadLine.</span></span> <span data-ttu-id="16183-578">Cela n’affecte pas l’historique PowerShell.</span><span class="sxs-lookup"><span data-stu-id="16183-578">This does not affect PowerShell history.</span></span>

- <span data-ttu-id="16183-579">Cmd `<Alt+F7>`</span><span class="sxs-lookup"><span data-stu-id="16183-579">Cmd: `<Alt+F7>`</span></span>

### <a name="endofhistory"></a><span data-ttu-id="16183-580">EndOfHistory</span><span class="sxs-lookup"><span data-stu-id="16183-580">EndOfHistory</span></span>

<span data-ttu-id="16183-581">Accéder au dernier élément (l’entrée en cours) dans l’historique.</span><span class="sxs-lookup"><span data-stu-id="16183-581">Move to the last item (the current input) in the history.</span></span>

- <span data-ttu-id="16183-582">Emacs- `<Alt+>>`</span><span class="sxs-lookup"><span data-stu-id="16183-582">Emacs: `<Alt+>>`</span></span>

### <a name="forwardsearchhistory"></a><span data-ttu-id="16183-583">ForwardSearchHistory</span><span class="sxs-lookup"><span data-stu-id="16183-583">ForwardSearchHistory</span></span>

<span data-ttu-id="16183-584">Effectuer une recherche incrémentielle par progression dans l’historique.</span><span class="sxs-lookup"><span data-stu-id="16183-584">Perform an incremental forward search through history.</span></span>

- <span data-ttu-id="16183-585">Cmd `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="16183-585">Cmd: `<Ctrl+s>`</span></span>
- <span data-ttu-id="16183-586">Emacs- `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="16183-586">Emacs: `<Ctrl+s>`</span></span>

### <a name="historysearchbackward"></a><span data-ttu-id="16183-587">HistorySearchBackward</span><span class="sxs-lookup"><span data-stu-id="16183-587">HistorySearchBackward</span></span>

<span data-ttu-id="16183-588">Remplacez l’entrée actuelle par l’élément « Previous » de l’historique PSReadLine qui correspond aux caractères entre le début et l’entrée et le curseur.</span><span class="sxs-lookup"><span data-stu-id="16183-588">Replace the current input with the 'previous' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="16183-589">Cmd `<F8>`</span><span class="sxs-lookup"><span data-stu-id="16183-589">Cmd: `<F8>`</span></span>

### <a name="historysearchforward"></a><span data-ttu-id="16183-590">HistorySearchForward</span><span class="sxs-lookup"><span data-stu-id="16183-590">HistorySearchForward</span></span>

<span data-ttu-id="16183-591">Remplacez l’entrée actuelle par l’élément « Next » de l’historique PSReadLine qui correspond aux caractères entre le début et l’entrée et le curseur.</span><span class="sxs-lookup"><span data-stu-id="16183-591">Replace the current input with the 'next' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="16183-592">Cmd `<Shift+F8>`</span><span class="sxs-lookup"><span data-stu-id="16183-592">Cmd: `<Shift+F8>`</span></span>

### <a name="nexthistory"></a><span data-ttu-id="16183-593">NextHistory</span><span class="sxs-lookup"><span data-stu-id="16183-593">NextHistory</span></span>

<span data-ttu-id="16183-594">Remplacez l’entrée actuelle par l’élément « Next » de l’historique PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="16183-594">Replace the current input with the 'next' item from PSReadLine history.</span></span>

- <span data-ttu-id="16183-595">Cmd `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="16183-595">Cmd: `<DownArrow>`</span></span>
- <span data-ttu-id="16183-596">Emacs- `<DownArrow>` , `<Ctrl+n>`</span><span class="sxs-lookup"><span data-stu-id="16183-596">Emacs: `<DownArrow>`, `<Ctrl+n>`</span></span>
- <span data-ttu-id="16183-597">Mode d’insertion VI : `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="16183-597">Vi insert mode: `<DownArrow>`</span></span>
- <span data-ttu-id="16183-598">Mode de commande VI : `<DownArrow>` , `<j>` , `<+>`</span><span class="sxs-lookup"><span data-stu-id="16183-598">Vi command mode: `<DownArrow>`, `<j>`, `<+>`</span></span>

### <a name="previoushistory"></a><span data-ttu-id="16183-599">PreviousHistory</span><span class="sxs-lookup"><span data-stu-id="16183-599">PreviousHistory</span></span>

<span data-ttu-id="16183-600">Remplacez l’entrée actuelle par l’élément « Previous » de l’historique PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="16183-600">Replace the current input with the 'previous' item from PSReadLine history.</span></span>

- <span data-ttu-id="16183-601">Cmd `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="16183-601">Cmd: `<UpArrow>`</span></span>
- <span data-ttu-id="16183-602">Emacs- `<UpArrow>` , `<Ctrl+p>`</span><span class="sxs-lookup"><span data-stu-id="16183-602">Emacs: `<UpArrow>`, `<Ctrl+p>`</span></span>
- <span data-ttu-id="16183-603">Mode d’insertion VI : `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="16183-603">Vi insert mode: `<UpArrow>`</span></span>
- <span data-ttu-id="16183-604">Mode de commande VI : `<UpArrow>` , `<k>` , `<->`</span><span class="sxs-lookup"><span data-stu-id="16183-604">Vi command mode: `<UpArrow>`, `<k>`, `<->`</span></span>

### <a name="reversesearchhistory"></a><span data-ttu-id="16183-605">ReverseSearchHistory</span><span class="sxs-lookup"><span data-stu-id="16183-605">ReverseSearchHistory</span></span>

<span data-ttu-id="16183-606">Effectuer une recherche incrémentielle incrémentielle dans l’historique.</span><span class="sxs-lookup"><span data-stu-id="16183-606">Perform an incremental backward search through history.</span></span>

- <span data-ttu-id="16183-607">Cmd `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="16183-607">Cmd: `<Ctrl+r>`</span></span>
- <span data-ttu-id="16183-608">Emacs- `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="16183-608">Emacs: `<Ctrl+r>`</span></span>

### <a name="visearchhistorybackward"></a><span data-ttu-id="16183-609">ViSearchHistoryBackward</span><span class="sxs-lookup"><span data-stu-id="16183-609">ViSearchHistoryBackward</span></span>

<span data-ttu-id="16183-610">Demande une chaîne de recherche et lance la recherche sur AcceptLine.</span><span class="sxs-lookup"><span data-stu-id="16183-610">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="16183-611">Mode d’insertion VI : `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="16183-611">Vi insert mode: `<Ctrl+r>`</span></span>
- <span data-ttu-id="16183-612">Mode de commande VI : `</>` , `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="16183-612">Vi command mode: `</>`, `<Ctrl+r>`</span></span>

## <a name="completion-functions"></a><span data-ttu-id="16183-613">Fonctions d’achèvement</span><span class="sxs-lookup"><span data-stu-id="16183-613">Completion functions</span></span>

### <a name="complete"></a><span data-ttu-id="16183-614">Terminé</span><span class="sxs-lookup"><span data-stu-id="16183-614">Complete</span></span>

<span data-ttu-id="16183-615">Tentative d’exécution de l’opération sur le texte entourant le curseur.</span><span class="sxs-lookup"><span data-stu-id="16183-615">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="16183-616">S’il existe plusieurs saisies semi-automatiques possibles, le plus long préfixe non ambigu est utilisé pour la finalisation.</span><span class="sxs-lookup"><span data-stu-id="16183-616">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="16183-617">Si vous essayez de terminer la saisie semi-automatique la plus longue, une liste des saisies semi-automatiques possibles s’affiche.</span><span class="sxs-lookup"><span data-stu-id="16183-617">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="16183-618">Emacs- `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="16183-618">Emacs: `<Tab>`</span></span>

### <a name="menucomplete"></a><span data-ttu-id="16183-619">MenuComplete</span><span class="sxs-lookup"><span data-stu-id="16183-619">MenuComplete</span></span>

<span data-ttu-id="16183-620">Tentative d’exécution de l’opération sur le texte entourant le curseur.</span><span class="sxs-lookup"><span data-stu-id="16183-620">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="16183-621">S’il existe plusieurs saisies semi-automatiques possibles, le plus long préfixe non ambigu est utilisé pour la finalisation.</span><span class="sxs-lookup"><span data-stu-id="16183-621">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="16183-622">Si vous essayez de terminer la saisie semi-automatique la plus longue, une liste des saisies semi-automatiques possibles s’affiche.</span><span class="sxs-lookup"><span data-stu-id="16183-622">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="16183-623">Cmd : `<Ctrl+@>` , `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="16183-623">Cmd: `<Ctrl+@>`, `<Ctrl+Spacebar>`</span></span>
- <span data-ttu-id="16183-624">Emacs- `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="16183-624">Emacs: `<Ctrl+Spacebar>`</span></span>

### <a name="possiblecompletions"></a><span data-ttu-id="16183-625">PossibleCompletions</span><span class="sxs-lookup"><span data-stu-id="16183-625">PossibleCompletions</span></span>

<span data-ttu-id="16183-626">Affiche la liste des saisies semi-automatiques possibles.</span><span class="sxs-lookup"><span data-stu-id="16183-626">Display the list of possible completions.</span></span>

- <span data-ttu-id="16183-627">Emacs- `<Alt+=>`</span><span class="sxs-lookup"><span data-stu-id="16183-627">Emacs: `<Alt+=>`</span></span>
- <span data-ttu-id="16183-628">Mode d’insertion VI : `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="16183-628">Vi insert mode: `<Ctrl+Spacebar>`</span></span>
- <span data-ttu-id="16183-629">Mode de commande VI : `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="16183-629">Vi command mode: `<Ctrl+Spacebar>`</span></span>

### <a name="tabcompletenext"></a><span data-ttu-id="16183-630">TabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="16183-630">TabCompleteNext</span></span>

<span data-ttu-id="16183-631">Tente de terminer le texte entourant le curseur avec la prochaine saisie semi-automatique disponible.</span><span class="sxs-lookup"><span data-stu-id="16183-631">Attempt to complete the text surrounding the cursor with the next available completion.</span></span>

- <span data-ttu-id="16183-632">Cmd `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="16183-632">Cmd: `<Tab>`</span></span>
- <span data-ttu-id="16183-633">Mode de commande VI : `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="16183-633">Vi command mode: `<Tab>`</span></span>

### <a name="tabcompleteprevious"></a><span data-ttu-id="16183-634">TabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="16183-634">TabCompletePrevious</span></span>

<span data-ttu-id="16183-635">Tente de terminer le texte entourant le curseur avec l’achèvement disponible précédent.</span><span class="sxs-lookup"><span data-stu-id="16183-635">Attempt to complete the text surrounding the cursor with the previous available completion.</span></span>

- <span data-ttu-id="16183-636">Cmd `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="16183-636">Cmd: `<Shift+Tab>`</span></span>
- <span data-ttu-id="16183-637">Mode de commande VI : `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="16183-637">Vi command mode: `<Shift+Tab>`</span></span>

### <a name="vitabcompletenext"></a><span data-ttu-id="16183-638">ViTabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="16183-638">ViTabCompleteNext</span></span>

<span data-ttu-id="16183-639">Met fin au groupe d’édition actuel, si nécessaire, et appelle TabCompleteNext.</span><span class="sxs-lookup"><span data-stu-id="16183-639">Ends the current edit group, if needed, and invokes TabCompleteNext.</span></span>

- <span data-ttu-id="16183-640">Mode d’insertion VI : `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="16183-640">Vi insert mode: `<Tab>`</span></span>

### <a name="vitabcompleteprevious"></a><span data-ttu-id="16183-641">ViTabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="16183-641">ViTabCompletePrevious</span></span>

<span data-ttu-id="16183-642">Met fin au groupe d’édition actuel, si nécessaire, et appelle TabCompletePrevious.</span><span class="sxs-lookup"><span data-stu-id="16183-642">Ends the current edit group, if needed, and invokes TabCompletePrevious.</span></span>

- <span data-ttu-id="16183-643">Mode d’insertion VI : `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="16183-643">Vi insert mode: `<Shift+Tab>`</span></span>

## <a name="prediction-functions"></a><span data-ttu-id="16183-644">Fonctions de prédiction</span><span class="sxs-lookup"><span data-stu-id="16183-644">Prediction functions</span></span>

### <a name="acceptnextsuggestionword"></a><span data-ttu-id="16183-645">AcceptNextSuggestionWord</span><span class="sxs-lookup"><span data-stu-id="16183-645">AcceptNextSuggestionWord</span></span>

<span data-ttu-id="16183-646">Si vous utilisez `InlineView` comme style de vue pour la prédiction, acceptez le mot suivant de la suggestion en ligne.</span><span class="sxs-lookup"><span data-stu-id="16183-646">When using `InlineView` as the view style for prediction, accept the next word of the inline suggestion.</span></span>

- <span data-ttu-id="16183-647">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="16183-647">Function is unbound.</span></span>

### <a name="acceptsuggestion"></a><span data-ttu-id="16183-648">AcceptSuggestion</span><span class="sxs-lookup"><span data-stu-id="16183-648">AcceptSuggestion</span></span>

<span data-ttu-id="16183-649">Si vous utilisez `InlineView` comme style de vue pour la prédiction, acceptez la suggestion en ligne actuelle.</span><span class="sxs-lookup"><span data-stu-id="16183-649">When using `InlineView` as the view style for prediction, accept the current inline suggestion.</span></span>

- <span data-ttu-id="16183-650">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="16183-650">Function is unbound.</span></span>

### <a name="nextsuggestion"></a><span data-ttu-id="16183-651">NextSuggestion</span><span class="sxs-lookup"><span data-stu-id="16183-651">NextSuggestion</span></span>

<span data-ttu-id="16183-652">Lorsque `ListView` vous utilisez comme style de vue pour la prédiction, accédez à la suggestion suivante dans la liste.</span><span class="sxs-lookup"><span data-stu-id="16183-652">When using `ListView` as the view style for prediction, navigate to the next suggestion in the list.</span></span>

- <span data-ttu-id="16183-653">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="16183-653">Function is unbound.</span></span>

### <a name="previoussuggestion"></a><span data-ttu-id="16183-654">PreviousSuggestion</span><span class="sxs-lookup"><span data-stu-id="16183-654">PreviousSuggestion</span></span>

<span data-ttu-id="16183-655">Lorsque `ListView` vous utilisez comme style de vue pour la prédiction, accédez à la suggestion précédente dans la liste.</span><span class="sxs-lookup"><span data-stu-id="16183-655">When using `ListView` as the view style for prediction, navigate to the previous suggestion in the list.</span></span>

- <span data-ttu-id="16183-656">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="16183-656">Function is unbound.</span></span>

### <a name="switchpredictionview"></a><span data-ttu-id="16183-657">SwitchPredictionView</span><span class="sxs-lookup"><span data-stu-id="16183-657">SwitchPredictionView</span></span>

<span data-ttu-id="16183-658">Changez le style d’affichage pour la prédiction entre `InlineView` et `ListView` .</span><span class="sxs-lookup"><span data-stu-id="16183-658">Switch the view style for prediction between `InlineView` and `ListView`.</span></span>

- <span data-ttu-id="16183-659">Cmd `<F2>`</span><span class="sxs-lookup"><span data-stu-id="16183-659">Cmd: `<F2>`</span></span>

## <a name="miscellaneous-functions"></a><span data-ttu-id="16183-660">Fonctions diverses</span><span class="sxs-lookup"><span data-stu-id="16183-660">Miscellaneous functions</span></span>

### <a name="capturescreen"></a><span data-ttu-id="16183-661">CaptureScreen</span><span class="sxs-lookup"><span data-stu-id="16183-661">CaptureScreen</span></span>

<span data-ttu-id="16183-662">Démarrer la capture d’écran interactive-flèches haut et bas sélectionnez lignes, entrez copie le texte sélectionné dans le presse-papiers en tant que texte et html.</span><span class="sxs-lookup"><span data-stu-id="16183-662">Start interactive screen capture - up/down arrows select lines, enter copies selected text to clipboard as text and html.</span></span>

- <span data-ttu-id="16183-663">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="16183-663">Function is unbound.</span></span>

### <a name="clearscreen"></a><span data-ttu-id="16183-664">ClearScreen</span><span class="sxs-lookup"><span data-stu-id="16183-664">ClearScreen</span></span>

<span data-ttu-id="16183-665">Effacez l’écran et dessinez la ligne active en haut de l’écran.</span><span class="sxs-lookup"><span data-stu-id="16183-665">Clear the screen and draw the current line at the top of the screen.</span></span>

- <span data-ttu-id="16183-666">Cmd `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="16183-666">Cmd: `<Ctrl+l>`</span></span>
- <span data-ttu-id="16183-667">Emacs- `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="16183-667">Emacs: `<Ctrl+l>`</span></span>
- <span data-ttu-id="16183-668">Mode d’insertion VI : `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="16183-668">Vi insert mode: `<Ctrl+l>`</span></span>
- <span data-ttu-id="16183-669">Mode de commande VI : `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="16183-669">Vi command mode: `<Ctrl+l>`</span></span>

### <a name="digitargument"></a><span data-ttu-id="16183-670">DigitArgument</span><span class="sxs-lookup"><span data-stu-id="16183-670">DigitArgument</span></span>

<span data-ttu-id="16183-671">Démarrez un nouvel argument digit à passer à d’autres fonctions.</span><span class="sxs-lookup"><span data-stu-id="16183-671">Start a new digit argument to pass to other functions.</span></span>

- <span data-ttu-id="16183-672">Cmd : `<Alt+0>` ,,,,, `<Alt+1>` `<Alt+2>` `<Alt+3>` `<Alt+4>` `<Alt+5>` , `<Alt+6>` , `<Alt+7>` , `<Alt+8>` , `<Alt+9>` , `<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="16183-672">Cmd: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="16183-673">Emacs-,,,,,,,,, `<Alt+0>` `<Alt+1>` `<Alt+2>` `<Alt+3>` `<Alt+4>` `<Alt+5>` `<Alt+6>` `<Alt+7>` `<Alt+8>` , `<Alt+9>` , `<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="16183-673">Emacs: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="16183-674">Mode de commande VI : `<0>` , `<1>` ,, `<2>` `<3>` , `<4>` , `<5>` , `<6>` , `<7>` , `<8>` , `<9>`</span><span class="sxs-lookup"><span data-stu-id="16183-674">Vi command mode: `<0>`, `<1>`, `<2>`, `<3>`, `<4>`, `<5>`, `<6>`, `<7>`, `<8>`, `<9>`</span></span>

### <a name="invokeprompt"></a><span data-ttu-id="16183-675">InvokePrompt</span><span class="sxs-lookup"><span data-stu-id="16183-675">InvokePrompt</span></span>

<span data-ttu-id="16183-676">Efface l’invite en cours et appelle la fonction prompt pour réafficher l’invite.</span><span class="sxs-lookup"><span data-stu-id="16183-676">Erases the current prompt and calls the prompt function to redisplay the prompt.</span></span> <span data-ttu-id="16183-677">Utile pour les gestionnaires de clés personnalisés qui changent d’État, par exemple modifier le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="16183-677">Useful for custom key handlers that change state, e.g. change the current directory.</span></span>

- <span data-ttu-id="16183-678">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="16183-678">Function is unbound.</span></span>

### <a name="scrolldisplaydown"></a><span data-ttu-id="16183-679">ScrollDisplayDown</span><span class="sxs-lookup"><span data-stu-id="16183-679">ScrollDisplayDown</span></span>

<span data-ttu-id="16183-680">Faites défiler l’écran vers le volet d’affichage.</span><span class="sxs-lookup"><span data-stu-id="16183-680">Scroll the display down one screen.</span></span>

- <span data-ttu-id="16183-681">Cmd `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="16183-681">Cmd: `<PageDown>`</span></span>
- <span data-ttu-id="16183-682">Emacs- `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="16183-682">Emacs: `<PageDown>`</span></span>

### <a name="scrolldisplaydownline"></a><span data-ttu-id="16183-683">ScrollDisplayDownLine</span><span class="sxs-lookup"><span data-stu-id="16183-683">ScrollDisplayDownLine</span></span>

<span data-ttu-id="16183-684">Faites défiler l’affichage d’une ligne vers le dessous.</span><span class="sxs-lookup"><span data-stu-id="16183-684">Scroll the display down one line.</span></span>

- <span data-ttu-id="16183-685">Cmd `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="16183-685">Cmd: `<Ctrl+PageDown>`</span></span>
- <span data-ttu-id="16183-686">Emacs- `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="16183-686">Emacs: `<Ctrl+PageDown>`</span></span>

### <a name="scrolldisplaytocursor"></a><span data-ttu-id="16183-687">ScrollDisplayToCursor</span><span class="sxs-lookup"><span data-stu-id="16183-687">ScrollDisplayToCursor</span></span>

<span data-ttu-id="16183-688">Faites défiler l’affichage jusqu’au curseur.</span><span class="sxs-lookup"><span data-stu-id="16183-688">Scroll the display to the cursor.</span></span>

- <span data-ttu-id="16183-689">Emacs- `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="16183-689">Emacs: `<Ctrl+End>`</span></span>

### <a name="scrolldisplaytop"></a><span data-ttu-id="16183-690">ScrollDisplayTop</span><span class="sxs-lookup"><span data-stu-id="16183-690">ScrollDisplayTop</span></span>

<span data-ttu-id="16183-691">Faites défiler l’affichage vers le haut.</span><span class="sxs-lookup"><span data-stu-id="16183-691">Scroll the display to the top.</span></span>

- <span data-ttu-id="16183-692">Emacs- `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="16183-692">Emacs: `<Ctrl+Home>`</span></span>

### <a name="scrolldisplayup"></a><span data-ttu-id="16183-693">ScrollDisplayUp</span><span class="sxs-lookup"><span data-stu-id="16183-693">ScrollDisplayUp</span></span>

<span data-ttu-id="16183-694">Faites défiler l’écran afficher vers le haut.</span><span class="sxs-lookup"><span data-stu-id="16183-694">Scroll the display up one screen.</span></span>

- <span data-ttu-id="16183-695">Cmd `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="16183-695">Cmd: `<PageUp>`</span></span>
- <span data-ttu-id="16183-696">Emacs- `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="16183-696">Emacs: `<PageUp>`</span></span>

### <a name="scrolldisplayupline"></a><span data-ttu-id="16183-697">ScrollDisplayUpLine</span><span class="sxs-lookup"><span data-stu-id="16183-697">ScrollDisplayUpLine</span></span>

<span data-ttu-id="16183-698">Faites défiler l’affichage d’une ligne vers le haut.</span><span class="sxs-lookup"><span data-stu-id="16183-698">Scroll the display up one line.</span></span>

- <span data-ttu-id="16183-699">Cmd `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="16183-699">Cmd: `<Ctrl+PageUp>`</span></span>
- <span data-ttu-id="16183-700">Emacs- `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="16183-700">Emacs: `<Ctrl+PageUp>`</span></span>

### <a name="selfinsert"></a><span data-ttu-id="16183-701">SelfInsert</span><span class="sxs-lookup"><span data-stu-id="16183-701">SelfInsert</span></span>

<span data-ttu-id="16183-702">Insérez la clé.</span><span class="sxs-lookup"><span data-stu-id="16183-702">Insert the key.</span></span>

- <span data-ttu-id="16183-703">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="16183-703">Function is unbound.</span></span>

### <a name="showcommandhelp"></a><span data-ttu-id="16183-704">ShowCommandHelp</span><span class="sxs-lookup"><span data-stu-id="16183-704">ShowCommandHelp</span></span>

<span data-ttu-id="16183-705">Fournit une vue d’ensemble de l’aide de l’applet de commande sur une autre mémoire tampon d’écran à l’aide d’un radiomessagerie de **Microsoft. PowerShell. téléavertisseur**.</span><span class="sxs-lookup"><span data-stu-id="16183-705">Provides a view of full cmdlet help on alternate screen buffer using a Pager from **Microsoft.PowerShell.Pager**.</span></span>

- <span data-ttu-id="16183-706">Cmd `<F1>`</span><span class="sxs-lookup"><span data-stu-id="16183-706">Cmd: `<F1>`</span></span>
- <span data-ttu-id="16183-707">Emacs- `<F1>`</span><span class="sxs-lookup"><span data-stu-id="16183-707">Emacs: `<F1>`</span></span>
- <span data-ttu-id="16183-708">Mode d’insertion VI : `<F1>`</span><span class="sxs-lookup"><span data-stu-id="16183-708">Vi insert mode: `<F1>`</span></span>
- <span data-ttu-id="16183-709">Mode de commande VI : `<F1>`</span><span class="sxs-lookup"><span data-stu-id="16183-709">Vi command mode: `<F1>`</span></span>

### <a name="showkeybindings"></a><span data-ttu-id="16183-710">ShowKeyBindings</span><span class="sxs-lookup"><span data-stu-id="16183-710">ShowKeyBindings</span></span>

<span data-ttu-id="16183-711">Affiche toutes les clés liées.</span><span class="sxs-lookup"><span data-stu-id="16183-711">Show all bound keys.</span></span>

- <span data-ttu-id="16183-712">Cmd `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="16183-712">Cmd: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="16183-713">Emacs- `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="16183-713">Emacs: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="16183-714">Mode d’insertion VI : `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="16183-714">Vi insert mode: `<Ctrl+Alt+?>`</span></span>

### <a name="showparameterhelp"></a><span data-ttu-id="16183-715">ShowParameterHelp</span><span class="sxs-lookup"><span data-stu-id="16183-715">ShowParameterHelp</span></span>

<span data-ttu-id="16183-716">Fournit une aide dynamique pour les paramètres en l’affiche sous la ligne de commande actuelle, comme `MenuComplete` .</span><span class="sxs-lookup"><span data-stu-id="16183-716">Provides dynamic help for parameters by showing it below the current command line like `MenuComplete`.</span></span>

- <span data-ttu-id="16183-717">Cmd `<Alt+h>`</span><span class="sxs-lookup"><span data-stu-id="16183-717">Cmd: `<Alt+h>`</span></span>
- <span data-ttu-id="16183-718">Emacs- `<Alt+h>`</span><span class="sxs-lookup"><span data-stu-id="16183-718">Emacs: `<Alt+h>`</span></span>
- <span data-ttu-id="16183-719">Mode d’insertion VI : `<Alt+h>`</span><span class="sxs-lookup"><span data-stu-id="16183-719">Vi insert mode: `<Alt+h>`</span></span>
- <span data-ttu-id="16183-720">Mode de commande VI : `<Alt+h>`</span><span class="sxs-lookup"><span data-stu-id="16183-720">Vi command mode: `<Alt+h>`</span></span>

### <a name="vicommandmode"></a><span data-ttu-id="16183-721">ViCommandMode</span><span class="sxs-lookup"><span data-stu-id="16183-721">ViCommandMode</span></span>

<span data-ttu-id="16183-722">Basculez le mode d’opération actuel de Vi-Insert à VI-Command.</span><span class="sxs-lookup"><span data-stu-id="16183-722">Switch the current operating mode from Vi-Insert to Vi-Command.</span></span>

- <span data-ttu-id="16183-723">Mode d’insertion VI : `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="16183-723">Vi insert mode: `<Escape>`</span></span>

### <a name="vidigitargumentinchord"></a><span data-ttu-id="16183-724">ViDigitArgumentInChord</span><span class="sxs-lookup"><span data-stu-id="16183-724">ViDigitArgumentInChord</span></span>

<span data-ttu-id="16183-725">Démarrez un nouvel argument digit à passer à d’autres fonctions dans l’un des cordes de VI.</span><span class="sxs-lookup"><span data-stu-id="16183-725">Start a new digit argument to pass to other functions while in one of vi's chords.</span></span>

- <span data-ttu-id="16183-726">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="16183-726">Function is unbound.</span></span>

### <a name="vieditvisually"></a><span data-ttu-id="16183-727">ViEditVisually</span><span class="sxs-lookup"><span data-stu-id="16183-727">ViEditVisually</span></span>

<span data-ttu-id="16183-728">Modifiez la ligne de commande dans un éditeur de texte spécifié par $env : EDITOR ou $env : VISUAL.</span><span class="sxs-lookup"><span data-stu-id="16183-728">Edit the command line in a text editor specified by $env:EDITOR or $env:VISUAL.</span></span>

- <span data-ttu-id="16183-729">Emacs- `<Ctrl+x,Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="16183-729">Emacs: `<Ctrl+x,Ctrl+e>`</span></span>
- <span data-ttu-id="16183-730">Mode de commande VI : `<v>`</span><span class="sxs-lookup"><span data-stu-id="16183-730">Vi command mode: `<v>`</span></span>

### <a name="viexit"></a><span data-ttu-id="16183-731">ViExit</span><span class="sxs-lookup"><span data-stu-id="16183-731">ViExit</span></span>

<span data-ttu-id="16183-732">Quitte l’interpréteur de commandes.</span><span class="sxs-lookup"><span data-stu-id="16183-732">Exits the shell.</span></span>

- <span data-ttu-id="16183-733">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="16183-733">Function is unbound.</span></span>

### <a name="viinsertmode"></a><span data-ttu-id="16183-734">ViInsertMode</span><span class="sxs-lookup"><span data-stu-id="16183-734">ViInsertMode</span></span>

<span data-ttu-id="16183-735">Basculez en mode insertion.</span><span class="sxs-lookup"><span data-stu-id="16183-735">Switch to Insert mode.</span></span>

- <span data-ttu-id="16183-736">Mode de commande VI : `<i>`</span><span class="sxs-lookup"><span data-stu-id="16183-736">Vi command mode: `<i>`</span></span>

### <a name="whatiskey"></a><span data-ttu-id="16183-737">WhatIsKey</span><span class="sxs-lookup"><span data-stu-id="16183-737">WhatIsKey</span></span>

<span data-ttu-id="16183-738">Lisez une clé et dites-moi à quoi la clé est liée.</span><span class="sxs-lookup"><span data-stu-id="16183-738">Read a key and tell me what the key is bound to.</span></span>

- <span data-ttu-id="16183-739">Cmd `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="16183-739">Cmd: `<Alt+?>`</span></span>
- <span data-ttu-id="16183-740">Emacs- `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="16183-740">Emacs: `<Alt+?>`</span></span>

## <a name="selection-functions"></a><span data-ttu-id="16183-741">Fonctions de sélection</span><span class="sxs-lookup"><span data-stu-id="16183-741">Selection functions</span></span>

### <a name="exchangepointandmark"></a><span data-ttu-id="16183-742">ExchangePointAndMark</span><span class="sxs-lookup"><span data-stu-id="16183-742">ExchangePointAndMark</span></span>

<span data-ttu-id="16183-743">Le curseur est placé à l’emplacement de la marque et la marque est déplacée vers l’emplacement du curseur.</span><span class="sxs-lookup"><span data-stu-id="16183-743">The cursor is placed at the location of the mark and the mark is moved to the location of the cursor.</span></span>

- <span data-ttu-id="16183-744">Emacs- `<Ctrl+x,Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="16183-744">Emacs: `<Ctrl+x,Ctrl+x>`</span></span>

### <a name="selectall"></a><span data-ttu-id="16183-745">SelectAll</span><span class="sxs-lookup"><span data-stu-id="16183-745">SelectAll</span></span>

<span data-ttu-id="16183-746">Sélectionnez la ligne entière.</span><span class="sxs-lookup"><span data-stu-id="16183-746">Select the entire line.</span></span>

- <span data-ttu-id="16183-747">Cmd `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="16183-747">Cmd: `<Ctrl+a>`</span></span>

### <a name="selectbackwardchar"></a><span data-ttu-id="16183-748">SelectBackwardChar</span><span class="sxs-lookup"><span data-stu-id="16183-748">SelectBackwardChar</span></span>

<span data-ttu-id="16183-749">Ajustez la sélection actuelle pour inclure le caractère précédent.</span><span class="sxs-lookup"><span data-stu-id="16183-749">Adjust the current selection to include the previous character.</span></span>

- <span data-ttu-id="16183-750">Cmd `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="16183-750">Cmd: `<Shift+LeftArrow>`</span></span>
- <span data-ttu-id="16183-751">Emacs- `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="16183-751">Emacs: `<Shift+LeftArrow>`</span></span>

### <a name="selectbackwardsline"></a><span data-ttu-id="16183-752">SelectBackwardsLine</span><span class="sxs-lookup"><span data-stu-id="16183-752">SelectBackwardsLine</span></span>

<span data-ttu-id="16183-753">Ajustez la sélection actuelle à inclure à partir du curseur jusqu’au début de la ligne.</span><span class="sxs-lookup"><span data-stu-id="16183-753">Adjust the current selection to include from the cursor to the start of the line.</span></span>

- <span data-ttu-id="16183-754">Cmd `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="16183-754">Cmd: `<Shift+Home>`</span></span>
- <span data-ttu-id="16183-755">Emacs- `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="16183-755">Emacs: `<Shift+Home>`</span></span>

### <a name="selectbackwardword"></a><span data-ttu-id="16183-756">SelectBackwardWord</span><span class="sxs-lookup"><span data-stu-id="16183-756">SelectBackwardWord</span></span>

<span data-ttu-id="16183-757">Ajustez la sélection actuelle pour inclure le mot précédent.</span><span class="sxs-lookup"><span data-stu-id="16183-757">Adjust the current selection to include the previous word.</span></span>

- <span data-ttu-id="16183-758">Cmd `<Shift+Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="16183-758">Cmd: `<Shift+Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="16183-759">Emacs- `<Alt+B>`</span><span class="sxs-lookup"><span data-stu-id="16183-759">Emacs: `<Alt+B>`</span></span>

### <a name="selectforwardchar"></a><span data-ttu-id="16183-760">SelectForwardChar</span><span class="sxs-lookup"><span data-stu-id="16183-760">SelectForwardChar</span></span>

<span data-ttu-id="16183-761">Ajustez la sélection actuelle pour inclure le caractère suivant.</span><span class="sxs-lookup"><span data-stu-id="16183-761">Adjust the current selection to include the next character.</span></span>

- <span data-ttu-id="16183-762">Cmd `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="16183-762">Cmd: `<Shift+RightArrow>`</span></span>
- <span data-ttu-id="16183-763">Emacs- `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="16183-763">Emacs: `<Shift+RightArrow>`</span></span>

### <a name="selectforwardword"></a><span data-ttu-id="16183-764">SelectForwardWord</span><span class="sxs-lookup"><span data-stu-id="16183-764">SelectForwardWord</span></span>

<span data-ttu-id="16183-765">Ajustez la sélection actuelle pour inclure le mot suivant à l’aide de ForwardWord.</span><span class="sxs-lookup"><span data-stu-id="16183-765">Adjust the current selection to include the next word using ForwardWord.</span></span>

- <span data-ttu-id="16183-766">Emacs- `<Alt+F>`</span><span class="sxs-lookup"><span data-stu-id="16183-766">Emacs: `<Alt+F>`</span></span>

### <a name="selectline"></a><span data-ttu-id="16183-767">SelectLine</span><span class="sxs-lookup"><span data-stu-id="16183-767">SelectLine</span></span>

<span data-ttu-id="16183-768">Ajustez la sélection actuelle à inclure à partir du curseur jusqu’à la fin de la ligne.</span><span class="sxs-lookup"><span data-stu-id="16183-768">Adjust the current selection to include from the cursor to the end of the line.</span></span>

- <span data-ttu-id="16183-769">Cmd `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="16183-769">Cmd: `<Shift+End>`</span></span>
- <span data-ttu-id="16183-770">Emacs- `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="16183-770">Emacs: `<Shift+End>`</span></span>

### <a name="selectnextword"></a><span data-ttu-id="16183-771">SelectNextWord</span><span class="sxs-lookup"><span data-stu-id="16183-771">SelectNextWord</span></span>

<span data-ttu-id="16183-772">Ajustez la sélection actuelle pour inclure le mot suivant.</span><span class="sxs-lookup"><span data-stu-id="16183-772">Adjust the current selection to include the next word.</span></span>

- <span data-ttu-id="16183-773">Cmd `<Shift+Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="16183-773">Cmd: `<Shift+Ctrl+RightArrow>`</span></span>

### <a name="selectshellbackwardword"></a><span data-ttu-id="16183-774">SelectShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="16183-774">SelectShellBackwardWord</span></span>

<span data-ttu-id="16183-775">Ajustez la sélection actuelle pour inclure le mot précédent à l’aide de ShellBackwardWord.</span><span class="sxs-lookup"><span data-stu-id="16183-775">Adjust the current selection to include the previous word using ShellBackwardWord.</span></span>

- <span data-ttu-id="16183-776">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="16183-776">Function is unbound.</span></span>

### <a name="selectshellforwardword"></a><span data-ttu-id="16183-777">SelectShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="16183-777">SelectShellForwardWord</span></span>

<span data-ttu-id="16183-778">Ajustez la sélection actuelle pour inclure le mot suivant à l’aide de ShellForwardWord.</span><span class="sxs-lookup"><span data-stu-id="16183-778">Adjust the current selection to include the next word using ShellForwardWord.</span></span>

- <span data-ttu-id="16183-779">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="16183-779">Function is unbound.</span></span>

### <a name="selectshellnextword"></a><span data-ttu-id="16183-780">SelectShellNextWord</span><span class="sxs-lookup"><span data-stu-id="16183-780">SelectShellNextWord</span></span>

<span data-ttu-id="16183-781">Ajustez la sélection actuelle pour inclure le mot suivant à l’aide de ShellNextWord.</span><span class="sxs-lookup"><span data-stu-id="16183-781">Adjust the current selection to include the next word using ShellNextWord.</span></span>

- <span data-ttu-id="16183-782">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="16183-782">Function is unbound.</span></span>

### <a name="setmark"></a><span data-ttu-id="16183-783">SetMark</span><span class="sxs-lookup"><span data-stu-id="16183-783">SetMark</span></span>

<span data-ttu-id="16183-784">Marquez l’emplacement actuel du curseur pour une utilisation dans une commande d’édition suivante.</span><span class="sxs-lookup"><span data-stu-id="16183-784">Mark the current location of the cursor for use in a subsequent editing command.</span></span>

- <span data-ttu-id="16183-785">Emacs- `<Ctrl+@>`</span><span class="sxs-lookup"><span data-stu-id="16183-785">Emacs: `<Ctrl+@>`</span></span>

## <a name="predictive-intellisense-functions"></a><span data-ttu-id="16183-786">Fonctions IntelliSense prédictives</span><span class="sxs-lookup"><span data-stu-id="16183-786">Predictive IntelliSense functions</span></span>

> [!NOTE]
> <span data-ttu-id="16183-787">La fonctionnalité IntelliSense prédictive doit être activée pour utiliser ces fonctions.</span><span class="sxs-lookup"><span data-stu-id="16183-787">Predictive IntelliSense needs to be enabled to use these functions.</span></span>

### <a name="acceptnextwordsuggestion"></a><span data-ttu-id="16183-788">AcceptNextWordSuggestion</span><span class="sxs-lookup"><span data-stu-id="16183-788">AcceptNextWordSuggestion</span></span>

<span data-ttu-id="16183-789">Accepte le mot suivant de la suggestion en ligne de la fonctionnalité IntelliSense prédictive.</span><span class="sxs-lookup"><span data-stu-id="16183-789">Accepts the next word of the inline suggestion from Predictive IntelliSense.</span></span>
<span data-ttu-id="16183-790">Cette fonction peut être liée à l’aide de <kbd>CTRL</kbd> + <kbd>F</kbd> en exécutant la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="16183-790">This function can be bound with <kbd>Ctrl</kbd>+<kbd>F</kbd> by running the following command.</span></span>

```powershell
Set-PSReadLineKeyHandler -Chord "Ctrl+f" -Function ForwardWord
```

### <a name="acceptsuggestion"></a><span data-ttu-id="16183-791">AcceptSuggestion</span><span class="sxs-lookup"><span data-stu-id="16183-791">AcceptSuggestion</span></span>

<span data-ttu-id="16183-792">Accepte la suggestion en ligne actuelle de la fonctionnalité IntelliSense prédictive en appuyant sur <kbd>flèche droite</kbd> lorsque le curseur se trouve à la fin de la ligne active.</span><span class="sxs-lookup"><span data-stu-id="16183-792">Accepts the current inline suggestion from Predictive IntelliSense by pressing <kbd>RightArrow</kbd> when the cursor is at the end of the current line.</span></span>

## <a name="search-functions"></a><span data-ttu-id="16183-793">Fonctions de recherche</span><span class="sxs-lookup"><span data-stu-id="16183-793">Search functions</span></span>

### <a name="charactersearch"></a><span data-ttu-id="16183-794">CharacterSearch</span><span class="sxs-lookup"><span data-stu-id="16183-794">CharacterSearch</span></span>

<span data-ttu-id="16183-795">Lisez un caractère et recherchez l’occurrence suivante de ce caractère.</span><span class="sxs-lookup"><span data-stu-id="16183-795">Read a character and search forward for the next occurrence of that character.</span></span>
<span data-ttu-id="16183-796">Si un argument est spécifié, effectuez une recherche vers l’avant (ou vers l’arrière si négatif) pour la nième occurrence.</span><span class="sxs-lookup"><span data-stu-id="16183-796">If an argument is specified, search forward (or backward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="16183-797">Cmd `<F3>`</span><span class="sxs-lookup"><span data-stu-id="16183-797">Cmd: `<F3>`</span></span>
- <span data-ttu-id="16183-798">Emacs- `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="16183-798">Emacs: `<Ctrl+]>`</span></span>
- <span data-ttu-id="16183-799">Mode d’insertion VI : `<F3>`</span><span class="sxs-lookup"><span data-stu-id="16183-799">Vi insert mode: `<F3>`</span></span>
- <span data-ttu-id="16183-800">Mode de commande VI : `<F3>`</span><span class="sxs-lookup"><span data-stu-id="16183-800">Vi command mode: `<F3>`</span></span>

### <a name="charactersearchbackward"></a><span data-ttu-id="16183-801">CharacterSearchBackward</span><span class="sxs-lookup"><span data-stu-id="16183-801">CharacterSearchBackward</span></span>

<span data-ttu-id="16183-802">Lisez un caractère et recherchez l’occurrence suivante de ce caractère.</span><span class="sxs-lookup"><span data-stu-id="16183-802">Read a character and search backward for the next occurrence of that character.</span></span> <span data-ttu-id="16183-803">Si un argument est spécifié, effectuez une recherche vers l’arrière (ou vers l’avant si négatif) pour la nième occurrence.</span><span class="sxs-lookup"><span data-stu-id="16183-803">If an argument is specified, search backward (or forward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="16183-804">Cmd `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="16183-804">Cmd: `<Shift+F3>`</span></span>
- <span data-ttu-id="16183-805">Emacs- `<Ctrl+Alt+]>`</span><span class="sxs-lookup"><span data-stu-id="16183-805">Emacs: `<Ctrl+Alt+]>`</span></span>
- <span data-ttu-id="16183-806">Mode d’insertion VI : `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="16183-806">Vi insert mode: `<Shift+F3>`</span></span>
- <span data-ttu-id="16183-807">Mode de commande VI : `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="16183-807">Vi command mode: `<Shift+F3>`</span></span>

### <a name="repeatlastcharsearch"></a><span data-ttu-id="16183-808">RepeatLastCharSearch</span><span class="sxs-lookup"><span data-stu-id="16183-808">RepeatLastCharSearch</span></span>

<span data-ttu-id="16183-809">Répète la dernière recherche de caractères enregistrée.</span><span class="sxs-lookup"><span data-stu-id="16183-809">Repeat the last recorded character search.</span></span>

- <span data-ttu-id="16183-810">Mode de commande VI : `<;>`</span><span class="sxs-lookup"><span data-stu-id="16183-810">Vi command mode: `<;>`</span></span>

### <a name="repeatlastcharsearchbackwards"></a><span data-ttu-id="16183-811">RepeatLastCharSearchBackwards</span><span class="sxs-lookup"><span data-stu-id="16183-811">RepeatLastCharSearchBackwards</span></span>

<span data-ttu-id="16183-812">Répète la dernière recherche de caractères enregistrée, mais dans la direction opposée.</span><span class="sxs-lookup"><span data-stu-id="16183-812">Repeat the last recorded character search, but in the opposite direction.</span></span>

- <span data-ttu-id="16183-813">Mode de commande VI : `<,>`</span><span class="sxs-lookup"><span data-stu-id="16183-813">Vi command mode: `<,>`</span></span>

### <a name="repeatsearch"></a><span data-ttu-id="16183-814">RepeatSearch</span><span class="sxs-lookup"><span data-stu-id="16183-814">RepeatSearch</span></span>

<span data-ttu-id="16183-815">Répétez la dernière recherche dans la même direction que précédemment.</span><span class="sxs-lookup"><span data-stu-id="16183-815">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="16183-816">Mode de commande VI : `<n>`</span><span class="sxs-lookup"><span data-stu-id="16183-816">Vi command mode: `<n>`</span></span>

### <a name="repeatsearchbackward"></a><span data-ttu-id="16183-817">RepeatSearchBackward</span><span class="sxs-lookup"><span data-stu-id="16183-817">RepeatSearchBackward</span></span>

<span data-ttu-id="16183-818">Répétez la dernière recherche dans la même direction que précédemment.</span><span class="sxs-lookup"><span data-stu-id="16183-818">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="16183-819">Mode de commande VI : `<N>`</span><span class="sxs-lookup"><span data-stu-id="16183-819">Vi command mode: `<N>`</span></span>

### <a name="searchchar"></a><span data-ttu-id="16183-820">SearchChar</span><span class="sxs-lookup"><span data-stu-id="16183-820">SearchChar</span></span>

<span data-ttu-id="16183-821">Lisez le caractère suivant, puis recherchez-le, à l’avenir, puis annulez un caractère.</span><span class="sxs-lookup"><span data-stu-id="16183-821">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="16183-822">Il s’agit de la fonctionnalité’t'.</span><span class="sxs-lookup"><span data-stu-id="16183-822">This is for 't' functionality.</span></span>

- <span data-ttu-id="16183-823">Mode de commande VI : `<f>`</span><span class="sxs-lookup"><span data-stu-id="16183-823">Vi command mode: `<f>`</span></span>

### <a name="searchcharbackward"></a><span data-ttu-id="16183-824">SearchCharBackward</span><span class="sxs-lookup"><span data-stu-id="16183-824">SearchCharBackward</span></span>

<span data-ttu-id="16183-825">Lisez le caractère suivant, puis recherchez-le, en accédant à l’arrière, puis en annulant un caractère.</span><span class="sxs-lookup"><span data-stu-id="16183-825">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="16183-826">Il s’agit de la fonctionnalité’t'.</span><span class="sxs-lookup"><span data-stu-id="16183-826">This is for 'T' functionality.</span></span>

- <span data-ttu-id="16183-827">Mode de commande VI : `<F>`</span><span class="sxs-lookup"><span data-stu-id="16183-827">Vi command mode: `<F>`</span></span>

### <a name="searchcharbackwardwithbackoff"></a><span data-ttu-id="16183-828">SearchCharBackwardWithBackoff</span><span class="sxs-lookup"><span data-stu-id="16183-828">SearchCharBackwardWithBackoff</span></span>

<span data-ttu-id="16183-829">Lisez le caractère suivant, puis recherchez-le, en accédant à l’arrière, puis en annulant un caractère.</span><span class="sxs-lookup"><span data-stu-id="16183-829">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="16183-830">Il s’agit de la fonctionnalité’t'.</span><span class="sxs-lookup"><span data-stu-id="16183-830">This is for 'T' functionality.</span></span>

- <span data-ttu-id="16183-831">Mode de commande VI : `<T>`</span><span class="sxs-lookup"><span data-stu-id="16183-831">Vi command mode: `<T>`</span></span>

### <a name="searchcharwithbackoff"></a><span data-ttu-id="16183-832">SearchCharWithBackoff</span><span class="sxs-lookup"><span data-stu-id="16183-832">SearchCharWithBackoff</span></span>

<span data-ttu-id="16183-833">Lisez le caractère suivant, puis recherchez-le, à l’avenir, puis annulez un caractère.</span><span class="sxs-lookup"><span data-stu-id="16183-833">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="16183-834">Il s’agit de la fonctionnalité’t'.</span><span class="sxs-lookup"><span data-stu-id="16183-834">This is for 't' functionality.</span></span>

- <span data-ttu-id="16183-835">Mode de commande VI : `<t>`</span><span class="sxs-lookup"><span data-stu-id="16183-835">Vi command mode: `<t>`</span></span>

### <a name="searchforward"></a><span data-ttu-id="16183-836">SearchForward</span><span class="sxs-lookup"><span data-stu-id="16183-836">SearchForward</span></span>

<span data-ttu-id="16183-837">Demande une chaîne de recherche et lance la recherche sur AcceptLine.</span><span class="sxs-lookup"><span data-stu-id="16183-837">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="16183-838">Mode d’insertion VI : `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="16183-838">Vi insert mode: `<Ctrl+s>`</span></span>
- <span data-ttu-id="16183-839">Mode de commande VI : `<?>` , `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="16183-839">Vi command mode: `<?>`, `<Ctrl+s>`</span></span>

## <a name="custom-key-bindings"></a><span data-ttu-id="16183-840">Combinaisons de touches personnalisées</span><span class="sxs-lookup"><span data-stu-id="16183-840">Custom Key Bindings</span></span>

<span data-ttu-id="16183-841">PSReadLine prend en charge les combinaisons de touches personnalisées à l’aide de l’applet de commande `Set-PSReadLineKeyHandler` .</span><span class="sxs-lookup"><span data-stu-id="16183-841">PSReadLine supports custom key bindings using the cmdlet `Set-PSReadLineKeyHandler`.</span></span> <span data-ttu-id="16183-842">La plupart des combinaisons de touches personnalisées appellent l’une des fonctions ci-dessus, par exemple</span><span class="sxs-lookup"><span data-stu-id="16183-842">Most custom key bindings call one of the above functions, for example</span></span>

```powershell
Set-PSReadLineKeyHandler -Key UpArrow -Function HistorySearchBackward
```

<span data-ttu-id="16183-843">Vous pouvez lier un ScriptBlock à une clé.</span><span class="sxs-lookup"><span data-stu-id="16183-843">You can bind a ScriptBlock to a key.</span></span> <span data-ttu-id="16183-844">Le ScriptBlock peut faire à peu près tout ce que vous voulez.</span><span class="sxs-lookup"><span data-stu-id="16183-844">The ScriptBlock can do pretty much anything you want.</span></span> <span data-ttu-id="16183-845">Voici quelques exemples utiles :</span><span class="sxs-lookup"><span data-stu-id="16183-845">Some useful examples include</span></span>

- <span data-ttu-id="16183-846">modifier la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="16183-846">edit the command line</span></span>
- <span data-ttu-id="16183-847">ouverture d’une nouvelle fenêtre (par exemple, aide)</span><span class="sxs-lookup"><span data-stu-id="16183-847">opening a new window (e.g. help)</span></span>
- <span data-ttu-id="16183-848">modifier les répertoires sans modifier la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="16183-848">change directories without changing the command line</span></span>

<span data-ttu-id="16183-849">Le ScriptBlock reçoit deux arguments :</span><span class="sxs-lookup"><span data-stu-id="16183-849">The ScriptBlock receives two arguments:</span></span>

- <span data-ttu-id="16183-850">`$key` -Objet **[ConsoleKeyInfo]** qui est la clé qui a déclenché la liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="16183-850">`$key` - A **[ConsoleKeyInfo]** object that is the key that triggered the custom binding.</span></span> <span data-ttu-id="16183-851">Si vous liez le même ScriptBlock à plusieurs clés et que vous devez effectuer des actions différentes en fonction de la clé, vous pouvez vérifier $key.</span><span class="sxs-lookup"><span data-stu-id="16183-851">If you bind the same ScriptBlock to multiple keys and need to perform different actions depending on the key, you can check $key.</span></span> <span data-ttu-id="16183-852">De nombreuses liaisons personnalisées ignorent cet argument.</span><span class="sxs-lookup"><span data-stu-id="16183-852">Many custom bindings ignore this argument.</span></span>

- <span data-ttu-id="16183-853">`$arg` : Argument arbitraire.</span><span class="sxs-lookup"><span data-stu-id="16183-853">`$arg` - An arbitrary argument.</span></span> <span data-ttu-id="16183-854">Le plus souvent, il s’agit d’un argument entier que l’utilisateur passe à partir des combinaisons de touches DigitArgument.</span><span class="sxs-lookup"><span data-stu-id="16183-854">Most often, this would be an integer argument that the user passes from the key bindings DigitArgument.</span></span> <span data-ttu-id="16183-855">Si votre liaison n’accepte pas d’arguments, il est raisonnable d’ignorer cet argument.</span><span class="sxs-lookup"><span data-stu-id="16183-855">If your binding doesn't accept arguments, it's reasonable to ignore this argument.</span></span>

<span data-ttu-id="16183-856">Jetons un coup d’œil à un exemple qui ajoute une ligne de commande à l’historique sans l’exécuter.</span><span class="sxs-lookup"><span data-stu-id="16183-856">Let's take a look at an example that adds a command line to history without executing it.</span></span> <span data-ttu-id="16183-857">Cela est utile lorsque vous vous rendez compte que vous avez oublié d’effectuer une opération, mais que vous ne voulez pas entrer à nouveau la ligne de commande que vous avez déjà entrée.</span><span class="sxs-lookup"><span data-stu-id="16183-857">This is useful when you realize you forgot to do something, but don't want to re-enter the command line you've already entered.</span></span>

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

<span data-ttu-id="16183-858">Vous pouvez voir beaucoup plus d’exemples dans le fichier `SamplePSReadLineProfile.ps1` qui est installé dans le dossier du module PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="16183-858">You can see many more examples in the file `SamplePSReadLineProfile.ps1` which is installed in the PSReadLine module folder.</span></span>

<span data-ttu-id="16183-859">La plupart des combinaisons de touches utilisent des fonctions d’assistance pour la modification de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="16183-859">Most key bindings use some helper functions for editing the command line.</span></span>
<span data-ttu-id="16183-860">Ces API sont documentées dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="16183-860">Those APIs are documented in the next section.</span></span>

## <a name="custom-key-binding-support-apis"></a><span data-ttu-id="16183-861">API de prise en charge de la liaison de clé personnalisée</span><span class="sxs-lookup"><span data-stu-id="16183-861">Custom Key Binding Support APIs</span></span>

<span data-ttu-id="16183-862">Les fonctions suivantes sont publiques dans Microsoft. PowerShell. PSConsoleReadLine, mais ne peuvent pas être directement liées à une clé.</span><span class="sxs-lookup"><span data-stu-id="16183-862">The following functions are public in Microsoft.PowerShell.PSConsoleReadLine, but cannot be directly bound to a key.</span></span> <span data-ttu-id="16183-863">La plupart sont utiles dans les combinaisons de touches personnalisées.</span><span class="sxs-lookup"><span data-stu-id="16183-863">Most are useful in custom key bindings.</span></span>

```csharp
void AddToHistory(string command)
```

<span data-ttu-id="16183-864">Ajoutez une ligne de commande à l’historique sans l’exécuter.</span><span class="sxs-lookup"><span data-stu-id="16183-864">Add a command line to history without executing it.</span></span>

```csharp
void ClearKillRing()
```

<span data-ttu-id="16183-865">Effacez le point d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="16183-865">Clear the kill-ring.</span></span>  <span data-ttu-id="16183-866">Cela est principalement utilisé pour les tests.</span><span class="sxs-lookup"><span data-stu-id="16183-866">This is mostly used for testing.</span></span>

```csharp
void Delete(int start, int length)
```

<span data-ttu-id="16183-867">Supprimer les caractères de longueur du début.</span><span class="sxs-lookup"><span data-stu-id="16183-867">Delete length characters from start.</span></span>  <span data-ttu-id="16183-868">Cette opération prend en charge les opérations d’annulation et de rétablissement.</span><span class="sxs-lookup"><span data-stu-id="16183-868">This operation supports undo/redo.</span></span>

```csharp
void Ding()
```

<span data-ttu-id="16183-869">Effectuez l’action Ding en fonction des préférences de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="16183-869">Perform the Ding action based on the users preference.</span></span>

```csharp
void GetBufferState([ref] string input, [ref] int cursor)
void GetBufferState([ref] Ast ast, [ref] Token[] tokens,
  [ref] ParseError[] parseErrors, [ref] int cursor)
```

<span data-ttu-id="16183-870">Ces deux fonctions récupèrent des informations utiles sur l’état actuel de la mémoire tampon d’entrée.</span><span class="sxs-lookup"><span data-stu-id="16183-870">These two functions retrieve useful information about the current state of the input buffer.</span></span>  <span data-ttu-id="16183-871">La première est plus couramment utilisée dans les cas simples.</span><span class="sxs-lookup"><span data-stu-id="16183-871">The first is more commonly used for simple cases.</span></span>  <span data-ttu-id="16183-872">Le second est utilisé si votre liaison fait une opération plus avancée avec l’AST.</span><span class="sxs-lookup"><span data-stu-id="16183-872">The second is used if your binding is doing something more advanced with the Ast.</span></span>

```csharp
IEnumerable[Microsoft.PowerShell.KeyHandler]
  GetKeyHandlers(bool includeBound, bool includeUnbound)

IEnumerable[Microsoft.PowerShell.KeyHandler]
  GetKeyHandlers(string[] Chord)
```

<span data-ttu-id="16183-873">Ces deux fonctions sont utilisées par `Get-PSReadLineKeyHandler` .</span><span class="sxs-lookup"><span data-stu-id="16183-873">These two functions are used by `Get-PSReadLineKeyHandler`.</span></span> <span data-ttu-id="16183-874">La première est utilisée pour récupérer toutes les combinaisons de touches.</span><span class="sxs-lookup"><span data-stu-id="16183-874">The first is used to get all key bindings.</span></span> <span data-ttu-id="16183-875">Le second est utilisé pour recevoir des combinaisons de touches spécifiques.</span><span class="sxs-lookup"><span data-stu-id="16183-875">The second is used to get specific key bindings.</span></span>

```csharp
Microsoft.PowerShell.PSConsoleReadLineOptions GetOptions()
```

<span data-ttu-id="16183-876">Cette fonction est utilisée par Get-PSReadLineOption et n’est probablement pas trop utile dans une liaison de clé personnalisée.</span><span class="sxs-lookup"><span data-stu-id="16183-876">This function is used by Get-PSReadLineOption and probably isn't too useful in a custom key binding.</span></span>

```csharp
void GetSelectionState([ref] int start, [ref] int length)
```

<span data-ttu-id="16183-877">Si aucune sélection n’est effectuée sur la ligne de commande,-1 est retourné à la fois en début et en longueur.</span><span class="sxs-lookup"><span data-stu-id="16183-877">If there is no selection on the command line, -1 will be returned in both start and length.</span></span> <span data-ttu-id="16183-878">Si une sélection est effectuée sur la ligne de commande, le début et la longueur de la sélection sont retournés.</span><span class="sxs-lookup"><span data-stu-id="16183-878">If there is a selection on the command line, the start and length of the selection are returned.</span></span>

```csharp
void Insert(char c)
void Insert(string s)
```

<span data-ttu-id="16183-879">Insérez un caractère ou une chaîne au niveau du curseur.</span><span class="sxs-lookup"><span data-stu-id="16183-879">Insert a character or string at the cursor.</span></span>  <span data-ttu-id="16183-880">Cette opération prend en charge les opérations d’annulation et de rétablissement.</span><span class="sxs-lookup"><span data-stu-id="16183-880">This operation supports undo/redo.</span></span>

```csharp
string ReadLine(runspace remoteRunspace,
  System.Management.Automation.EngineIntrinsics engineIntrinsics)
```

<span data-ttu-id="16183-881">Il s’agit du point d’entrée principal de PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="16183-881">This is the main entry point to PSReadLine.</span></span> <span data-ttu-id="16183-882">Comme il ne prend pas en charge la récursivité, il n’est pas utile dans une liaison de clé personnalisée.</span><span class="sxs-lookup"><span data-stu-id="16183-882">It does not support recursion, so is not useful in a custom key binding.</span></span>

```csharp
void RemoveKeyHandler(string[] key)
```

<span data-ttu-id="16183-883">Cette fonction est utilisée par Remove-PSReadLineKeyHandler et n’est probablement pas trop utile dans une liaison de clé personnalisée.</span><span class="sxs-lookup"><span data-stu-id="16183-883">This function is used by Remove-PSReadLineKeyHandler and probably isn't too useful in a custom key binding.</span></span>

```csharp
void Replace(int start, int length, string replacement)
```

<span data-ttu-id="16183-884">Remplacez une partie de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="16183-884">Replace some of the input.</span></span> <span data-ttu-id="16183-885">Cette opération prend en charge les opérations d’annulation et de rétablissement.</span><span class="sxs-lookup"><span data-stu-id="16183-885">This operation supports undo/redo.</span></span> <span data-ttu-id="16183-886">C’est préférable à Delete, suivi de Insert, car il est traité comme une action unique pour Undo.</span><span class="sxs-lookup"><span data-stu-id="16183-886">This is preferred over Delete followed by Insert because it is treated as a single action for undo.</span></span>

```csharp
void SetCursorPosition(int cursor)
```

<span data-ttu-id="16183-887">Déplacer le curseur vers l’offset donné.</span><span class="sxs-lookup"><span data-stu-id="16183-887">Move the cursor to the given offset.</span></span> <span data-ttu-id="16183-888">Le déplacement du curseur n’est pas suivi pour l’annulation.</span><span class="sxs-lookup"><span data-stu-id="16183-888">Cursor movement is not tracked for undo.</span></span>

```csharp
void SetOptions(Microsoft.PowerShell.SetPSReadLineOption options)
```

<span data-ttu-id="16183-889">Cette fonction est une méthode d’assistance utilisée par l’applet de commande Set-PSReadLineOption, mais peut être utile pour une combinaison de touches personnalisée qui souhaite modifier temporairement un paramètre.</span><span class="sxs-lookup"><span data-stu-id="16183-889">This function is a helper method used by the cmdlet Set-PSReadLineOption, but might be useful to a custom key binding that wants to temporarily change a setting.</span></span>

```csharp
bool TryGetArgAsInt(System.Object arg, [ref] int numericArg,
  int defaultNumericArg)
```

<span data-ttu-id="16183-890">Cette méthode d’assistance est utilisée pour les liaisons personnalisées qui respectent DigitArgument.</span><span class="sxs-lookup"><span data-stu-id="16183-890">This helper method is used for custom bindings that honor DigitArgument.</span></span> <span data-ttu-id="16183-891">Un appel classique ressemble à ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="16183-891">A typical call looks like</span></span>

```powershell
[int]$numericArg = 0
[Microsoft.PowerShell.PSConsoleReadLine]::TryGetArgAsInt($arg,
  [ref]$numericArg, 1)
```

## <a name="notes"></a><span data-ttu-id="16183-892">Remarques</span><span class="sxs-lookup"><span data-stu-id="16183-892">Notes</span></span>

### <a name="command-history"></a><span data-ttu-id="16183-893">Historique des commandes</span><span class="sxs-lookup"><span data-stu-id="16183-893">Command History</span></span>

<span data-ttu-id="16183-894">PSReadLine gère un fichier d’historique contenant toutes les commandes et données que vous avez entrées à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="16183-894">PSReadLine maintains a history file containing all the commands and data you have entered from the command line.</span></span> <span data-ttu-id="16183-895">Cela peut contenir des données sensibles, y compris des mots de passe.</span><span class="sxs-lookup"><span data-stu-id="16183-895">This may contain sensitive data including passwords.</span></span> <span data-ttu-id="16183-896">Par exemple, si vous utilisez l’applet de commande, `ConvertTo-SecureString` le mot de passe est enregistré dans le fichier d’historique sous forme de texte brut.</span><span class="sxs-lookup"><span data-stu-id="16183-896">For example, if you use the `ConvertTo-SecureString` cmdlet the password is logged in the history file as plain text.</span></span> <span data-ttu-id="16183-897">Les fichiers d’historique sont un fichier nommé `$($host.Name)_history.txt` .</span><span class="sxs-lookup"><span data-stu-id="16183-897">The history files is a file named `$($host.Name)_history.txt`.</span></span> <span data-ttu-id="16183-898">Sur les systèmes Windows, le fichier d’historique est stocké à l’adresse `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine` .</span><span class="sxs-lookup"><span data-stu-id="16183-898">On Windows systems the history file is stored at `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine`.</span></span> <span data-ttu-id="16183-899">Sur les systèmes non-Windows, les fichiers d’historique sont stockés dans `$env:XDG_DATA_HOME/powershell/PSReadLine` ou `$env:HOME/.local/share/powershell/PSReadLine` .</span><span class="sxs-lookup"><span data-stu-id="16183-899">On non-Windows systems, the history files is stored at `$env:XDG_DATA_HOME/powershell/PSReadLine` or `$env:HOME/.local/share/powershell/PSReadLine`.</span></span>

### <a name="feedback--contributing-to-psreadline"></a><span data-ttu-id="16183-900">Commentaires & contribution à PSReadLine</span><span class="sxs-lookup"><span data-stu-id="16183-900">Feedback & Contributing To PSReadLine</span></span>

[<span data-ttu-id="16183-901">PSReadLine sur GitHub</span><span class="sxs-lookup"><span data-stu-id="16183-901">PSReadLine on GitHub</span></span>](https://github.com/PowerShell/PSReadLine)

<span data-ttu-id="16183-902">N’hésitez pas à envoyer une demande de tirage ou à envoyer des commentaires sur la page GitHub.</span><span class="sxs-lookup"><span data-stu-id="16183-902">Feel free to submit a pull request or submit feedback on the GitHub page.</span></span>

## <a name="see-also"></a><span data-ttu-id="16183-903">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="16183-903">See Also</span></span>

<span data-ttu-id="16183-904">PSReadLine est fortement influencé par la bibliothèque GNU [ReadLine](https://tiswww.case.edu/php/chet/readline/rltop.html) .</span><span class="sxs-lookup"><span data-stu-id="16183-904">PSReadLine is heavily influenced by the GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) library.</span></span>
