---
description: PSReadLine fournit une expérience d’édition de ligne de commande améliorée dans la console PowerShell.
Locale: en-US
ms.date: 11/23/2020
online version: https://docs.microsoft.com/powershell/module/psreadline/about/about_psreadline?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: À propos de PSReadLine
ms.openlocfilehash: ddc88dda3514e4279b6d91b023e26da88f645af7
ms.sourcegitcommit: 1dfd5554b70c7e8f4e3df19e29c384a9c0a4b227
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/03/2021
ms.locfileid: "101685219"
---
# <a name="psreadline"></a><span data-ttu-id="eded8-103">PSReadLine</span><span class="sxs-lookup"><span data-stu-id="eded8-103">PSReadLine</span></span>

## <a name="about_psreadline"></a><span data-ttu-id="eded8-104">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="eded8-104">about_PSReadLine</span></span>

## <a name="short-description"></a><span data-ttu-id="eded8-105">Description courte</span><span class="sxs-lookup"><span data-stu-id="eded8-105">Short Description</span></span>

<span data-ttu-id="eded8-106">PSReadLine fournit une expérience d’édition de ligne de commande améliorée dans la console PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eded8-106">PSReadLine provides an improved command-line editing experience in the PowerShell console.</span></span>

## <a name="long-description"></a><span data-ttu-id="eded8-107">Description longue</span><span class="sxs-lookup"><span data-stu-id="eded8-107">Long Description</span></span>

<span data-ttu-id="eded8-108">PSReadLine 2,2 fournit une expérience d’édition de ligne de commande puissante pour la console PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eded8-108">PSReadLine 2.2 provides a powerful command-line editing experience for the PowerShell console.</span></span> <span data-ttu-id="eded8-109">Elle offre les possibilités suivantes :</span><span class="sxs-lookup"><span data-stu-id="eded8-109">It provides:</span></span>

- <span data-ttu-id="eded8-110">Coloration de la syntaxe de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="eded8-110">Syntax coloring of the command line</span></span>
- <span data-ttu-id="eded8-111">Indication visuelle des erreurs de syntaxe</span><span class="sxs-lookup"><span data-stu-id="eded8-111">A visual indication of syntax errors</span></span>
- <span data-ttu-id="eded8-112">Une meilleure expérience multi-ligne (modification et historique)</span><span class="sxs-lookup"><span data-stu-id="eded8-112">A better multi-line experience (both editing and history)</span></span>
- <span data-ttu-id="eded8-113">Combinaisons de touches personnalisables</span><span class="sxs-lookup"><span data-stu-id="eded8-113">Customizable key bindings</span></span>
- <span data-ttu-id="eded8-114">Modes cmd et Emacs</span><span class="sxs-lookup"><span data-stu-id="eded8-114">Cmd and Emacs modes</span></span>
- <span data-ttu-id="eded8-115">Nombreuses options de configuration</span><span class="sxs-lookup"><span data-stu-id="eded8-115">Many configuration options</span></span>
- <span data-ttu-id="eded8-116">Saisie semi-automatique du style bash (facultatif en mode cmd, par défaut en mode emacs)</span><span class="sxs-lookup"><span data-stu-id="eded8-116">Bash style completion (optional in Cmd mode, default in Emacs mode)</span></span>
- <span data-ttu-id="eded8-117">Emacs-Yank/Kill-Ring</span><span class="sxs-lookup"><span data-stu-id="eded8-117">Emacs yank/kill-ring</span></span>
- <span data-ttu-id="eded8-118">Mouvement « mot » basé sur un jeton PowerShell et Kill</span><span class="sxs-lookup"><span data-stu-id="eded8-118">PowerShell token based "word" movement and kill</span></span>
- <span data-ttu-id="eded8-119">IntelliSense prédictif</span><span class="sxs-lookup"><span data-stu-id="eded8-119">Predictive IntelliSense</span></span>

<span data-ttu-id="eded8-120">PSReadLine 2.2.0 a ajouté deux nouvelles fonctionnalités IntelliSense prédictives :</span><span class="sxs-lookup"><span data-stu-id="eded8-120">PSReadLine 2.2.0 added two new predictive IntelliSense features:</span></span>

- <span data-ttu-id="eded8-121">Ajout du paramètre **PredictionViewStyle** pour permettre la sélection du nouveau `ListView` .</span><span class="sxs-lookup"><span data-stu-id="eded8-121">Added the **PredictionViewStyle** parameter to allow for the selection of the new `ListView`.</span></span>
- <span data-ttu-id="eded8-122">Connexion de PSReadLine aux `CommandPrediction` API introduites dans PS 7,1 pour permettre à un utilisateur de pouvoir importer un module de prédiction qui peut restituer les suggestions à partir d’une source personnalisée.</span><span class="sxs-lookup"><span data-stu-id="eded8-122">Connected PSReadLine to the `CommandPrediction` APIs introduced in PS 7.1 to allow a user can import a predictor module that can render the suggestions from a custom source.</span></span>

<span data-ttu-id="eded8-123">PSReadLine nécessite PowerShell 3,0 ou une version plus récente.</span><span class="sxs-lookup"><span data-stu-id="eded8-123">PSReadLine requires PowerShell 3.0, or newer.</span></span> <span data-ttu-id="eded8-124">PSReadLine fonctionne avec l’hôte de console, Visual Studio Code et le terminal de fenêtre par défaut.</span><span class="sxs-lookup"><span data-stu-id="eded8-124">PSReadLine works with default console host, Visual Studio Code, and Window Terminal.</span></span> <span data-ttu-id="eded8-125">Il ne fonctionne pas dans PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="eded8-125">It does not work in PowerShell ISE.</span></span>

<span data-ttu-id="eded8-126">PSReadLine 2.2.0 est fourni avec PowerShell 7,2 et est pris en charge dans toutes les versions prises en charge de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eded8-126">PSReadLine 2.2.0 ships with PowerShell 7.2 and is supported in all supported versions of PowerShell.</span></span> <span data-ttu-id="eded8-127">Vous pouvez l’installer à partir du PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="eded8-127">It is available to install from the PowerShell Gallery.</span></span>
<span data-ttu-id="eded8-128">Pour installer PSReadLine 2.2.0 dans une version prise en charge de PowerShell, exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="eded8-128">To install PSReadLine 2.2.0 in a supported version of PowerShell run the following command.</span></span>

```powershell
Install-Module -Name PSReadLine -AllowPrerelease
```

> [!NOTE]
> <span data-ttu-id="eded8-129">À compter de PowerShell 7,0, PowerShell ignore le chargement automatique de PSReadLine sur Windows si un programme de lecture d’écran est détecté.</span><span class="sxs-lookup"><span data-stu-id="eded8-129">Beginning with PowerShell 7.0, PowerShell skips auto-loading PSReadLine on Windows if a screen reader program is detected.</span></span> <span data-ttu-id="eded8-130">Actuellement, PSReadLine ne fonctionne pas correctement avec les lecteurs d’écran.</span><span class="sxs-lookup"><span data-stu-id="eded8-130">Currently, PSReadLine doesn't work well with the screen readers.</span></span> <span data-ttu-id="eded8-131">Le rendu et la mise en forme par défaut de PowerShell 7,0 sur Windows fonctionnent correctement.</span><span class="sxs-lookup"><span data-stu-id="eded8-131">The default rendering and formatting of PowerShell 7.0 on Windows works properly.</span></span> <span data-ttu-id="eded8-132">Vous pouvez charger le module manuellement, si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="eded8-132">You can manually load the module if necessary.</span></span>

## <a name="predictive-intellisense"></a><span data-ttu-id="eded8-133">IntelliSense prédictif</span><span class="sxs-lookup"><span data-stu-id="eded8-133">Predictive IntelliSense</span></span>

<span data-ttu-id="eded8-134">La fonctionnalité IntelliSense prédictive est un ajout au concept de saisie semi-automatique via la touche Tab qui aide l’utilisateur à exécuter correctement les commandes.</span><span class="sxs-lookup"><span data-stu-id="eded8-134">Predictive IntelliSense is an addition to the concept of tab completion that assists the user in successfully completing commands.</span></span> <span data-ttu-id="eded8-135">Il permet aux utilisateurs de découvrir, de modifier et d’exécuter des commandes complètes basées sur des prédictions correspondantes à partir de l’historique de l’utilisateur et d’autres plug-ins spécifiques au domaine.</span><span class="sxs-lookup"><span data-stu-id="eded8-135">It enables users to discover, edit, and execute full commands based on matching predictions from the user's history and additional domain specific plugins.</span></span>

### <a name="enable-predictive-intellisense"></a><span data-ttu-id="eded8-136">Activer la fonctionnalité IntelliSense prédictive</span><span class="sxs-lookup"><span data-stu-id="eded8-136">Enable Predictive IntelliSense</span></span>

<span data-ttu-id="eded8-137">La fonctionnalité IntelliSense prédictive est désactivée par défaut.</span><span class="sxs-lookup"><span data-stu-id="eded8-137">Predictive IntelliSense is disabled by default.</span></span> <span data-ttu-id="eded8-138">Pour activer les prédictions, exécutez simplement la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="eded8-138">To enable predictions, just run the following command:</span></span>

```powershell
Set-PSReadLineOption -PredictionSource History
```

<span data-ttu-id="eded8-139">Le paramètre **PredictionSource** peut également accepter des plug-ins pour des exigences personnalisées et spécifiques à un domaine.</span><span class="sxs-lookup"><span data-stu-id="eded8-139">The **PredictionSource** parameter can also accept plugins for domain specific and custom requirements.</span></span>

<span data-ttu-id="eded8-140">Pour désactiver IntelliSense prédictif, il suffit d’exécuter :</span><span class="sxs-lookup"><span data-stu-id="eded8-140">To disable Predictive IntelliSense, just run:</span></span>

```powershell
Set-PSReadLineOption -PredictionSource None
```

<span data-ttu-id="eded8-141">Les fonctions suivantes sont disponibles dans la classe **[Microsoft. PowerShell. PSConsoleReadLine]**.</span><span class="sxs-lookup"><span data-stu-id="eded8-141">The following functions are available in the class **[Microsoft.PowerShell.PSConsoleReadLine]**.</span></span>

## <a name="basic-editing-functions"></a><span data-ttu-id="eded8-142">Fonctions d’édition de base</span><span class="sxs-lookup"><span data-stu-id="eded8-142">Basic editing functions</span></span>

### <a name="abort"></a><span data-ttu-id="eded8-143">Abandon</span><span class="sxs-lookup"><span data-stu-id="eded8-143">Abort</span></span>

<span data-ttu-id="eded8-144">Annuler l’action en cours, par exemple, recherche de l’historique incrémentiel.</span><span class="sxs-lookup"><span data-stu-id="eded8-144">Abort current action, e.g. incremental history search.</span></span>

- <span data-ttu-id="eded8-145">Emacs- `<Ctrl+g>`</span><span class="sxs-lookup"><span data-stu-id="eded8-145">Emacs: `<Ctrl+g>`</span></span>

### <a name="acceptandgetnext"></a><span data-ttu-id="eded8-146">AcceptAndGetNext</span><span class="sxs-lookup"><span data-stu-id="eded8-146">AcceptAndGetNext</span></span>

<span data-ttu-id="eded8-147">Tentative d’exécution de l’entrée en cours.</span><span class="sxs-lookup"><span data-stu-id="eded8-147">Attempt to execute the current input.</span></span> <span data-ttu-id="eded8-148">Si elle peut être exécutée (par exemple, AcceptLine), rappelez l’élément suivant de l’historique la prochaine fois que ReadLine est appelé.</span><span class="sxs-lookup"><span data-stu-id="eded8-148">If it can be executed (like AcceptLine), then recall the next item from history the next time ReadLine is called.</span></span>

- <span data-ttu-id="eded8-149">Emacs- `<Ctrl+o>`</span><span class="sxs-lookup"><span data-stu-id="eded8-149">Emacs: `<Ctrl+o>`</span></span>

### <a name="acceptline"></a><span data-ttu-id="eded8-150">AcceptLine</span><span class="sxs-lookup"><span data-stu-id="eded8-150">AcceptLine</span></span>

<span data-ttu-id="eded8-151">Tentative d’exécution de l’entrée en cours.</span><span class="sxs-lookup"><span data-stu-id="eded8-151">Attempt to execute the current input.</span></span> <span data-ttu-id="eded8-152">Si l’entrée actuelle est incomplète (par exemple, il manque une parenthèse fermante, un crochet ou un guillemet, l’invite de continuation est affichée sur la ligne suivante et PSReadLine attend que les clés modifient l’entrée actuelle.</span><span class="sxs-lookup"><span data-stu-id="eded8-152">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="eded8-153">Cmd `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="eded8-153">Cmd: `<Enter>`</span></span>
- <span data-ttu-id="eded8-154">Emacs- `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="eded8-154">Emacs: `<Enter>`</span></span>
- <span data-ttu-id="eded8-155">Mode d’insertion VI : `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="eded8-155">Vi insert mode: `<Enter>`</span></span>

### <a name="addline"></a><span data-ttu-id="eded8-156">AddLine</span><span class="sxs-lookup"><span data-stu-id="eded8-156">AddLine</span></span>

<span data-ttu-id="eded8-157">L’invite de continuation est affichée sur la ligne suivante et PSReadLine attend que les clés modifient l’entrée actuelle.</span><span class="sxs-lookup"><span data-stu-id="eded8-157">The continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span> <span data-ttu-id="eded8-158">Cela est utile pour entrer une entrée multiligne sous la forme d’une commande unique, même lorsqu’une seule ligne est complète en entrée.</span><span class="sxs-lookup"><span data-stu-id="eded8-158">This is useful to enter multi-line input as a single command even when a single line is complete input by itself.</span></span>

- <span data-ttu-id="eded8-159">Cmd `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="eded8-159">Cmd: `<Shift+Enter>`</span></span>
- <span data-ttu-id="eded8-160">Emacs- `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="eded8-160">Emacs: `<Shift+Enter>`</span></span>
- <span data-ttu-id="eded8-161">Mode d’insertion VI : `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="eded8-161">Vi insert mode: `<Shift+Enter>`</span></span>
- <span data-ttu-id="eded8-162">Mode de commande VI : `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="eded8-162">Vi command mode: `<Shift+Enter>`</span></span>

### <a name="backwarddeletechar"></a><span data-ttu-id="eded8-163">BackwardDeleteChar</span><span class="sxs-lookup"><span data-stu-id="eded8-163">BackwardDeleteChar</span></span>

<span data-ttu-id="eded8-164">Supprimez le caractère avant le curseur.</span><span class="sxs-lookup"><span data-stu-id="eded8-164">Delete the character before the cursor.</span></span>

- <span data-ttu-id="eded8-165">Cmd : `<Backspace>` , `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="eded8-165">Cmd: `<Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="eded8-166">Emacs : `<Backspace>` , `<Ctrl+Backspace>` , `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="eded8-166">Emacs: `<Backspace>`, `<Ctrl+Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="eded8-167">Mode d’insertion VI : `<Backspace>`</span><span class="sxs-lookup"><span data-stu-id="eded8-167">Vi insert mode: `<Backspace>`</span></span>
- <span data-ttu-id="eded8-168">Mode de commande VI : `<X>` , `<d,h>`</span><span class="sxs-lookup"><span data-stu-id="eded8-168">Vi command mode: `<X>`, `<d,h>`</span></span>

### <a name="backwarddeleteinput"></a><span data-ttu-id="eded8-169">BackwardDeleteInput</span><span class="sxs-lookup"><span data-stu-id="eded8-169">BackwardDeleteInput</span></span>

<span data-ttu-id="eded8-170">Comme BackwardKillInput-supprime le texte du point jusqu’au début de l’entrée, mais ne place pas le texte supprimé dans l’anneau d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="eded8-170">Like BackwardKillInput - deletes text from the point to the start of the input, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="eded8-171">Cmd `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="eded8-171">Cmd: `<Ctrl+Home>`</span></span>
- <span data-ttu-id="eded8-172">Mode d’insertion VI : `<Ctrl+u>` , `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="eded8-172">Vi insert mode: `<Ctrl+u>`, `<Ctrl+Home>`</span></span>
- <span data-ttu-id="eded8-173">Mode de commande VI : `<Ctrl+u>` , `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="eded8-173">Vi command mode: `<Ctrl+u>`, `<Ctrl+Home>`</span></span>

### <a name="backwarddeleteline"></a><span data-ttu-id="eded8-174">BackwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="eded8-174">BackwardDeleteLine</span></span>

<span data-ttu-id="eded8-175">Comme BackwardKillLine-supprime le texte du point jusqu’au début de la ligne, mais ne place pas le texte supprimé dans l’anneau d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="eded8-175">Like BackwardKillLine - deletes text from the point to the start of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="eded8-176">Mode de commande VI : `<d,0>`</span><span class="sxs-lookup"><span data-stu-id="eded8-176">Vi command mode: `<d,0>`</span></span>

### <a name="backwarddeleteword"></a><span data-ttu-id="eded8-177">BackwardDeleteWord</span><span class="sxs-lookup"><span data-stu-id="eded8-177">BackwardDeleteWord</span></span>

<span data-ttu-id="eded8-178">Supprime le mot précédent.</span><span class="sxs-lookup"><span data-stu-id="eded8-178">Deletes the previous word.</span></span>

- <span data-ttu-id="eded8-179">Mode de commande VI : `<Ctrl+w>` , `<d,b>`</span><span class="sxs-lookup"><span data-stu-id="eded8-179">Vi command mode: `<Ctrl+w>`, `<d,b>`</span></span>

### <a name="backwardkillinput"></a><span data-ttu-id="eded8-180">BackwardKillInput</span><span class="sxs-lookup"><span data-stu-id="eded8-180">BackwardKillInput</span></span>

<span data-ttu-id="eded8-181">Effacez le texte du début de l’entrée jusqu’au curseur.</span><span class="sxs-lookup"><span data-stu-id="eded8-181">Clear the text from the start of the input to the cursor.</span></span> <span data-ttu-id="eded8-182">Le texte effacé est placé dans le Kill-Ring.</span><span class="sxs-lookup"><span data-stu-id="eded8-182">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="eded8-183">Emacs- `<Ctrl+u>` , `<Ctrl+x,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="eded8-183">Emacs: `<Ctrl+u>`, `<Ctrl+x,Backspace>`</span></span>

### <a name="backwardkillline"></a><span data-ttu-id="eded8-184">BackwardKillLine</span><span class="sxs-lookup"><span data-stu-id="eded8-184">BackwardKillLine</span></span>

<span data-ttu-id="eded8-185">Efface le texte du début de la ligne logique actuelle jusqu’au curseur.</span><span class="sxs-lookup"><span data-stu-id="eded8-185">Clear the text from the start of the current logical line to the cursor.</span></span> <span data-ttu-id="eded8-186">Le texte effacé est placé dans le Kill-Ring.</span><span class="sxs-lookup"><span data-stu-id="eded8-186">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="eded8-187">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="eded8-187">Function is unbound.</span></span>

### <a name="backwardkillword"></a><span data-ttu-id="eded8-188">BackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="eded8-188">BackwardKillWord</span></span>

<span data-ttu-id="eded8-189">Efface l’entrée du début du mot actuel jusqu’au curseur.</span><span class="sxs-lookup"><span data-stu-id="eded8-189">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="eded8-190">Si le curseur se trouve entre des mots, l’entrée est effacée du début du mot précédent au curseur.</span><span class="sxs-lookup"><span data-stu-id="eded8-190">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="eded8-191">Le texte effacé est placé dans le Kill-Ring.</span><span class="sxs-lookup"><span data-stu-id="eded8-191">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="eded8-192">Cmd : `<Ctrl+Backspace>` , `<Ctrl+w>`</span><span class="sxs-lookup"><span data-stu-id="eded8-192">Cmd: `<Ctrl+Backspace>`, `<Ctrl+w>`</span></span>
- <span data-ttu-id="eded8-193">Emacs- `<Alt+Backspace>` , `<Escape,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="eded8-193">Emacs: `<Alt+Backspace>`, `<Escape,Backspace>`</span></span>
- <span data-ttu-id="eded8-194">Mode d’insertion VI : `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="eded8-194">Vi insert mode: `<Ctrl+Backspace>`</span></span>
- <span data-ttu-id="eded8-195">Mode de commande VI : `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="eded8-195">Vi command mode: `<Ctrl+Backspace>`</span></span>

### <a name="cancelline"></a><span data-ttu-id="eded8-196">CancelLine</span><span class="sxs-lookup"><span data-stu-id="eded8-196">CancelLine</span></span>

<span data-ttu-id="eded8-197">Annule l’entrée actuelle, en laissant l’entrée à l’écran, mais retourne à l’hôte afin que l’invite soit de nouveau évaluée.</span><span class="sxs-lookup"><span data-stu-id="eded8-197">Cancel the current input, leaving the input on the screen, but returns back to the host so the prompt is evaluated again.</span></span>

- <span data-ttu-id="eded8-198">Mode d’insertion VI : `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="eded8-198">Vi insert mode: `<Ctrl+c>`</span></span>
- <span data-ttu-id="eded8-199">Mode de commande VI : `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="eded8-199">Vi command mode: `<Ctrl+c>`</span></span>

### <a name="copy"></a><span data-ttu-id="eded8-200">Copier</span><span class="sxs-lookup"><span data-stu-id="eded8-200">Copy</span></span>

<span data-ttu-id="eded8-201">Copier la région sélectionnée dans le presse-papiers du système.</span><span class="sxs-lookup"><span data-stu-id="eded8-201">Copy selected region to the system clipboard.</span></span> <span data-ttu-id="eded8-202">Si aucune région n’est sélectionnée, copiez la ligne entière.</span><span class="sxs-lookup"><span data-stu-id="eded8-202">If no region is selected, copy the whole line.</span></span>

- <span data-ttu-id="eded8-203">Cmd `<Ctrl+C>`</span><span class="sxs-lookup"><span data-stu-id="eded8-203">Cmd: `<Ctrl+C>`</span></span>

### <a name="copyorcancelline"></a><span data-ttu-id="eded8-204">CopyOrCancelLine</span><span class="sxs-lookup"><span data-stu-id="eded8-204">CopyOrCancelLine</span></span>

<span data-ttu-id="eded8-205">Si le texte est sélectionné, copiez-le dans le presse-papiers, sinon, annulez la ligne.</span><span class="sxs-lookup"><span data-stu-id="eded8-205">If text is selected, copy to the clipboard, otherwise cancel the line.</span></span>

- <span data-ttu-id="eded8-206">Cmd `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="eded8-206">Cmd: `<Ctrl+c>`</span></span>
- <span data-ttu-id="eded8-207">Emacs- `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="eded8-207">Emacs: `<Ctrl+c>`</span></span>

### <a name="cut"></a><span data-ttu-id="eded8-208">Couper</span><span class="sxs-lookup"><span data-stu-id="eded8-208">Cut</span></span>

<span data-ttu-id="eded8-209">Supprimer la zone sélectionnée en plaçant le texte supprimé dans le presse-papiers du système.</span><span class="sxs-lookup"><span data-stu-id="eded8-209">Delete selected region placing deleted text in the system clipboard.</span></span>

- <span data-ttu-id="eded8-210">Cmd `<Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="eded8-210">Cmd: `<Ctrl+x>`</span></span>

### <a name="deletechar"></a><span data-ttu-id="eded8-211">DeleteChar</span><span class="sxs-lookup"><span data-stu-id="eded8-211">DeleteChar</span></span>

<span data-ttu-id="eded8-212">Supprimez le caractère sous le curseur.</span><span class="sxs-lookup"><span data-stu-id="eded8-212">Delete the character under the cursor.</span></span>

- <span data-ttu-id="eded8-213">Cmd `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="eded8-213">Cmd: `<Delete>`</span></span>
- <span data-ttu-id="eded8-214">Emacs- `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="eded8-214">Emacs: `<Delete>`</span></span>
- <span data-ttu-id="eded8-215">Mode d’insertion VI : `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="eded8-215">Vi insert mode: `<Delete>`</span></span>
- <span data-ttu-id="eded8-216">Mode de commande VI : `<Delete>` , `<x>` , `<d,l>` , `<d,Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="eded8-216">Vi command mode: `<Delete>`, `<x>`, `<d,l>`, `<d,Spacebar>`</span></span>

### <a name="deletecharorexit"></a><span data-ttu-id="eded8-217">DeleteCharOrExit</span><span class="sxs-lookup"><span data-stu-id="eded8-217">DeleteCharOrExit</span></span>

<span data-ttu-id="eded8-218">Supprimez le caractère sous le curseur, ou si la ligne est vide, quittez le processus.</span><span class="sxs-lookup"><span data-stu-id="eded8-218">Delete the character under the cursor, or if the line is empty, exit the process.</span></span>

- <span data-ttu-id="eded8-219">Emacs- `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="eded8-219">Emacs: `<Ctrl+d>`</span></span>

### <a name="deleteendofbuffer"></a><span data-ttu-id="eded8-220">DeleteEndOfBuffer</span><span class="sxs-lookup"><span data-stu-id="eded8-220">DeleteEndOfBuffer</span></span>

<span data-ttu-id="eded8-221">Supprime à la fin de la mémoire tampon multiligne.</span><span class="sxs-lookup"><span data-stu-id="eded8-221">Deletes to the end of the multiline buffer.</span></span>

- <span data-ttu-id="eded8-222">Mode de commande VI : `<d,G>`</span><span class="sxs-lookup"><span data-stu-id="eded8-222">Vi command mode: `<d,G>`</span></span>

### <a name="deleteendofword"></a><span data-ttu-id="eded8-223">DeleteEndOfWord</span><span class="sxs-lookup"><span data-stu-id="eded8-223">DeleteEndOfWord</span></span>

<span data-ttu-id="eded8-224">Supprimer à la fin du mot.</span><span class="sxs-lookup"><span data-stu-id="eded8-224">Delete to the end of the word.</span></span>

- <span data-ttu-id="eded8-225">Mode de commande VI : `<d,e>`</span><span class="sxs-lookup"><span data-stu-id="eded8-225">Vi command mode: `<d,e>`</span></span>

### <a name="deleteline"></a><span data-ttu-id="eded8-226">DeleteLine</span><span class="sxs-lookup"><span data-stu-id="eded8-226">DeleteLine</span></span>

<span data-ttu-id="eded8-227">Supprime la ligne logique actuelle d’une mémoire tampon multiligne, ce qui permet d’annuler.</span><span class="sxs-lookup"><span data-stu-id="eded8-227">Deletes the current logical line of a multiline buffer, enabling undo.</span></span>

- <span data-ttu-id="eded8-228">Mode de commande VI : `<d,d>` , `<d,_>`</span><span class="sxs-lookup"><span data-stu-id="eded8-228">Vi command mode: `<d,d>`, `<d,_>`</span></span>

### <a name="deletepreviouslines"></a><span data-ttu-id="eded8-229">DeletePreviousLines</span><span class="sxs-lookup"><span data-stu-id="eded8-229">DeletePreviousLines</span></span>

<span data-ttu-id="eded8-230">Supprime les lignes logiques requises précédentes et la ligne logique actuelle dans une mémoire tampon multiligne.</span><span class="sxs-lookup"><span data-stu-id="eded8-230">Deletes the previous requested logical lines and the current logical line in a multiline buffer.</span></span>

- <span data-ttu-id="eded8-231">Mode de commande VI : `<d,k>`</span><span class="sxs-lookup"><span data-stu-id="eded8-231">Vi command mode: `<d,k>`</span></span>

### <a name="deleterelativelines"></a><span data-ttu-id="eded8-232">DeleteRelativeLines</span><span class="sxs-lookup"><span data-stu-id="eded8-232">DeleteRelativeLines</span></span>

<span data-ttu-id="eded8-233">Supprime du début de la mémoire tampon jusqu’à la ligne logique actuelle dans une mémoire tampon multiligne.</span><span class="sxs-lookup"><span data-stu-id="eded8-233">Deletes from the beginning of the buffer to the current logical line in a multiline buffer.</span></span>

<span data-ttu-id="eded8-234">Comme la plupart des commandes VI, la `<d,g,g>` commande peut être précédée d’un argument numérique qui spécifie un numéro de ligne absolu, qui, avec le numéro de ligne en cours, compose une plage de lignes à supprimer.</span><span class="sxs-lookup"><span data-stu-id="eded8-234">As most Vi commands, the `<d,g,g>` command can be prepended with a numeric argument that specifies an absolute line number, which, together with the current line number, make up a range of lines to be deleted.</span></span>
<span data-ttu-id="eded8-235">S’il n’est pas spécifié, l’argument numérique a la valeur par défaut 1, qui fait référence à la première ligne logique dans une mémoire tampon multiligne.</span><span class="sxs-lookup"><span data-stu-id="eded8-235">If not specified, the numeric argument defaults to 1, which refers to the first logical line in a multiline buffer.</span></span>

<span data-ttu-id="eded8-236">Le nombre réel de lignes à supprimer de la ligne multiligne est calculé comme étant la différence entre le numéro de ligne logique actuel et l’argument numérique spécifié, qui peut donc être négatif.</span><span class="sxs-lookup"><span data-stu-id="eded8-236">The actual number of lines to be deleted from the multiline is computed as the difference between the current logical line number and the specified numeric argument, which can thus be negative.</span></span> <span data-ttu-id="eded8-237">Par conséquent, la partie _relative_ du nom de la méthode.</span><span class="sxs-lookup"><span data-stu-id="eded8-237">Hence the _relative_ part of method name.</span></span>

- <span data-ttu-id="eded8-238">Mode de commande VI : `<d,g,g>`</span><span class="sxs-lookup"><span data-stu-id="eded8-238">Vi command mode: `<d,g,g>`</span></span>

### <a name="deletenextlines"></a><span data-ttu-id="eded8-239">DeleteNextLines</span><span class="sxs-lookup"><span data-stu-id="eded8-239">DeleteNextLines</span></span>

<span data-ttu-id="eded8-240">Supprime la ligne logique actuelle et les lignes logiques suivantes demandées dans une mémoire tampon multiligne.</span><span class="sxs-lookup"><span data-stu-id="eded8-240">Deletes the current logical line and the next requested logical lines in a multiline buffer.</span></span>

- <span data-ttu-id="eded8-241">Mode de commande VI : `<d,j>`</span><span class="sxs-lookup"><span data-stu-id="eded8-241">Vi command mode: `<d,j>`</span></span>

### <a name="deletelinetofirstchar"></a><span data-ttu-id="eded8-242">DeleteLineToFirstChar</span><span class="sxs-lookup"><span data-stu-id="eded8-242">DeleteLineToFirstChar</span></span>

<span data-ttu-id="eded8-243">Supprime du premier caractère non vide de la ligne logique actuelle dans une mémoire tampon multiligne.</span><span class="sxs-lookup"><span data-stu-id="eded8-243">Deletes from the first non-blank character of the current logical line in a multiline buffer.</span></span>

- <span data-ttu-id="eded8-244">Mode de commande VI : `<d,^>`</span><span class="sxs-lookup"><span data-stu-id="eded8-244">Vi command mode: `<d,^>`</span></span>

### <a name="deletetoend"></a><span data-ttu-id="eded8-245">DeleteToEnd</span><span class="sxs-lookup"><span data-stu-id="eded8-245">DeleteToEnd</span></span>

<span data-ttu-id="eded8-246">Supprimer à la fin de la ligne.</span><span class="sxs-lookup"><span data-stu-id="eded8-246">Delete to the end of the line.</span></span>

- <span data-ttu-id="eded8-247">Mode de commande VI : `<D>` , `<d,$>`</span><span class="sxs-lookup"><span data-stu-id="eded8-247">Vi command mode: `<D>`, `<d,$>`</span></span>

### <a name="deleteword"></a><span data-ttu-id="eded8-248">DeleteWord</span><span class="sxs-lookup"><span data-stu-id="eded8-248">DeleteWord</span></span>

<span data-ttu-id="eded8-249">Supprimer le mot suivant.</span><span class="sxs-lookup"><span data-stu-id="eded8-249">Delete the next word.</span></span>

- <span data-ttu-id="eded8-250">Mode de commande VI : `<d,w>`</span><span class="sxs-lookup"><span data-stu-id="eded8-250">Vi command mode: `<d,w>`</span></span>

### <a name="forwarddeleteinput"></a><span data-ttu-id="eded8-251">ForwardDeleteInput</span><span class="sxs-lookup"><span data-stu-id="eded8-251">ForwardDeleteInput</span></span>

<span data-ttu-id="eded8-252">Comme KillLine-supprime le texte du point jusqu’à la fin de l’entrée, mais ne place pas le texte supprimé dans l’anneau de suppression.</span><span class="sxs-lookup"><span data-stu-id="eded8-252">Like KillLine - deletes text from the point to the end of the input, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="eded8-253">Cmd `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="eded8-253">Cmd: `<Ctrl+End>`</span></span>
- <span data-ttu-id="eded8-254">Mode d’insertion VI : `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="eded8-254">Vi insert mode: `<Ctrl+End>`</span></span>
- <span data-ttu-id="eded8-255">Mode de commande VI : `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="eded8-255">Vi command mode: `<Ctrl+End>`</span></span>

### <a name="forwarddeleteline"></a><span data-ttu-id="eded8-256">ForwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="eded8-256">ForwardDeleteLine</span></span>

<span data-ttu-id="eded8-257">Supprime le texte du point jusqu’à la fin de la ligne logique actuelle, mais ne place pas le texte supprimé dans l’anneau d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="eded8-257">Deletes text from the point to the end of the current logical line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="eded8-258">La fonction est indépendante</span><span class="sxs-lookup"><span data-stu-id="eded8-258">Function is unbound</span></span>

### <a name="insertlineabove"></a><span data-ttu-id="eded8-259">InsertLineAbove</span><span class="sxs-lookup"><span data-stu-id="eded8-259">InsertLineAbove</span></span>

<span data-ttu-id="eded8-260">Une nouvelle ligne vide est créée au-dessus de la ligne active, quel que soit l’endroit où se trouve le curseur sur la ligne active.</span><span class="sxs-lookup"><span data-stu-id="eded8-260">A new empty line is created above the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="eded8-261">Le curseur se déplace au début de la nouvelle ligne.</span><span class="sxs-lookup"><span data-stu-id="eded8-261">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="eded8-262">Cmd `<Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="eded8-262">Cmd: `<Ctrl+Enter>`</span></span>

### <a name="insertlinebelow"></a><span data-ttu-id="eded8-263">InsertLineBelow</span><span class="sxs-lookup"><span data-stu-id="eded8-263">InsertLineBelow</span></span>

<span data-ttu-id="eded8-264">Une nouvelle ligne vide est créée sous la ligne active, quel que soit l’endroit où se trouve le curseur sur la ligne active.</span><span class="sxs-lookup"><span data-stu-id="eded8-264">A new empty line is created below the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="eded8-265">Le curseur se déplace au début de la nouvelle ligne.</span><span class="sxs-lookup"><span data-stu-id="eded8-265">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="eded8-266">Cmd `<Shift+Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="eded8-266">Cmd: `<Shift+Ctrl+Enter>`</span></span>

### <a name="invertcase"></a><span data-ttu-id="eded8-267">InvertCase</span><span class="sxs-lookup"><span data-stu-id="eded8-267">InvertCase</span></span>

<span data-ttu-id="eded8-268">Inverser la casse du caractère actuel et passer au suivant.</span><span class="sxs-lookup"><span data-stu-id="eded8-268">Invert the case of the current character and move to the next one.</span></span>

- <span data-ttu-id="eded8-269">Mode de commande VI : `<~>`</span><span class="sxs-lookup"><span data-stu-id="eded8-269">Vi command mode: `<~>`</span></span>

### <a name="killline"></a><span data-ttu-id="eded8-270">KillLine</span><span class="sxs-lookup"><span data-stu-id="eded8-270">KillLine</span></span>

<span data-ttu-id="eded8-271">Effacez l’entrée du curseur jusqu’à la fin de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="eded8-271">Clear the input from the cursor to the end of the input.</span></span> <span data-ttu-id="eded8-272">Le texte effacé est placé dans le Kill-Ring.</span><span class="sxs-lookup"><span data-stu-id="eded8-272">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="eded8-273">Emacs- `<Ctrl+k>`</span><span class="sxs-lookup"><span data-stu-id="eded8-273">Emacs: `<Ctrl+k>`</span></span>

### <a name="killregion"></a><span data-ttu-id="eded8-274">KillRegion</span><span class="sxs-lookup"><span data-stu-id="eded8-274">KillRegion</span></span>

<span data-ttu-id="eded8-275">Supprimer le texte situé entre le curseur et la marque.</span><span class="sxs-lookup"><span data-stu-id="eded8-275">Kill the text between the cursor and the mark.</span></span>

- <span data-ttu-id="eded8-276">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="eded8-276">Function is unbound.</span></span>

### <a name="killword"></a><span data-ttu-id="eded8-277">KillWord</span><span class="sxs-lookup"><span data-stu-id="eded8-277">KillWord</span></span>

<span data-ttu-id="eded8-278">Efface l’entrée du curseur jusqu’à la fin du mot actuel.</span><span class="sxs-lookup"><span data-stu-id="eded8-278">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="eded8-279">Si le curseur se trouve entre des mots, l’entrée est effacée du curseur jusqu’à la fin du mot suivant.</span><span class="sxs-lookup"><span data-stu-id="eded8-279">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="eded8-280">Le texte effacé est placé dans le Kill-Ring.</span><span class="sxs-lookup"><span data-stu-id="eded8-280">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="eded8-281">Cmd : `<Alt+d>` , `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="eded8-281">Cmd: `<Alt+d>`, `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="eded8-282">Emacs- `<Alt+d>` , `<Escape,d>`</span><span class="sxs-lookup"><span data-stu-id="eded8-282">Emacs: `<Alt+d>`, `<Escape,d>`</span></span>
- <span data-ttu-id="eded8-283">Mode d’insertion VI : `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="eded8-283">Vi insert mode: `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="eded8-284">Mode de commande VI : `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="eded8-284">Vi command mode: `<Ctrl+Delete>`</span></span>

### <a name="paste"></a><span data-ttu-id="eded8-285">Coller</span><span class="sxs-lookup"><span data-stu-id="eded8-285">Paste</span></span>

<span data-ttu-id="eded8-286">Collez le texte à partir du presse-papiers du système.</span><span class="sxs-lookup"><span data-stu-id="eded8-286">Paste text from the system clipboard.</span></span>

- <span data-ttu-id="eded8-287">Cmd : `<Ctrl+v>` , `<Shift+Insert>`</span><span class="sxs-lookup"><span data-stu-id="eded8-287">Cmd: `<Ctrl+v>`, `<Shift+Insert>`</span></span>
- <span data-ttu-id="eded8-288">Mode d’insertion VI : `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="eded8-288">Vi insert mode: `<Ctrl+v>`</span></span>
- <span data-ttu-id="eded8-289">Mode de commande VI : `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="eded8-289">Vi command mode: `<Ctrl+v>`</span></span>

> [!IMPORTANT]
> <span data-ttu-id="eded8-290">Lors de l’utilisation de la fonction **Paste** , le contenu entier de la mémoire tampon du presse-papiers est collé dans la mémoire tampon d’entrée de PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="eded8-290">When using the **Paste** function, the entire contents of the clipboard buffer is pasted into the input buffer of PSReadLine.</span></span> <span data-ttu-id="eded8-291">La mémoire tampon d’entrée est ensuite transmise à l’analyseur PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eded8-291">The input buffer is then passed to the PowerShell parser.</span></span> <span data-ttu-id="eded8-292">L’entrée collée à l’aide de la méthode de collage **avec le bouton droit** de la console de l’application de console est copiée dans la mémoire tampon d’entrée un caractère à la fois.</span><span class="sxs-lookup"><span data-stu-id="eded8-292">Input pasted using the console application's **right-click** paste method is copied to the input buffer one character at a time.</span></span> <span data-ttu-id="eded8-293">La mémoire tampon d’entrée est transmise à l’analyseur lorsqu’un caractère de saut de ligne est copié.</span><span class="sxs-lookup"><span data-stu-id="eded8-293">The input buffer is passed to the parser when a newline character is copied.</span></span> <span data-ttu-id="eded8-294">Par conséquent, l’entrée est analysée une ligne à la fois.</span><span class="sxs-lookup"><span data-stu-id="eded8-294">Therefore, the input is parsed one line at a time.</span></span> <span data-ttu-id="eded8-295">La différence entre les méthodes de collage entraîne un comportement d’exécution différent.</span><span class="sxs-lookup"><span data-stu-id="eded8-295">The difference between paste methods results in different execution behavior.</span></span>

### <a name="pasteafter"></a><span data-ttu-id="eded8-296">PasteAfter</span><span class="sxs-lookup"><span data-stu-id="eded8-296">PasteAfter</span></span>

<span data-ttu-id="eded8-297">Collez le presse-papiers après le curseur, en déplaçant le curseur à la fin du texte collé.</span><span class="sxs-lookup"><span data-stu-id="eded8-297">Paste the clipboard after the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="eded8-298">Mode de commande VI : `<p>`</span><span class="sxs-lookup"><span data-stu-id="eded8-298">Vi command mode: `<p>`</span></span>

### <a name="pastebefore"></a><span data-ttu-id="eded8-299">PasteBefore</span><span class="sxs-lookup"><span data-stu-id="eded8-299">PasteBefore</span></span>

<span data-ttu-id="eded8-300">Collez le presse-papiers avant le curseur, en déplaçant le curseur à la fin du texte collé.</span><span class="sxs-lookup"><span data-stu-id="eded8-300">Paste the clipboard before the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="eded8-301">Mode de commande VI : `<P>`</span><span class="sxs-lookup"><span data-stu-id="eded8-301">Vi command mode: `<P>`</span></span>

### <a name="prependandaccept"></a><span data-ttu-id="eded8-302">PrependAndAccept</span><span class="sxs-lookup"><span data-stu-id="eded8-302">PrependAndAccept</span></span>

<span data-ttu-id="eded8-303">Faites précéder un' # 'et acceptez la ligne.</span><span class="sxs-lookup"><span data-stu-id="eded8-303">Prepend a '#' and accept the line.</span></span>

- <span data-ttu-id="eded8-304">Mode de commande VI : `<#>`</span><span class="sxs-lookup"><span data-stu-id="eded8-304">Vi command mode: `<#>`</span></span>

### <a name="redo"></a><span data-ttu-id="eded8-305">Rétablir</span><span class="sxs-lookup"><span data-stu-id="eded8-305">Redo</span></span>

<span data-ttu-id="eded8-306">Annule une annulation.</span><span class="sxs-lookup"><span data-stu-id="eded8-306">Undo an undo.</span></span>

- <span data-ttu-id="eded8-307">Cmd `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="eded8-307">Cmd: `<Ctrl+y>`</span></span>
- <span data-ttu-id="eded8-308">Mode d’insertion VI : `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="eded8-308">Vi insert mode: `<Ctrl+y>`</span></span>
- <span data-ttu-id="eded8-309">Mode de commande VI : `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="eded8-309">Vi command mode: `<Ctrl+y>`</span></span>

### <a name="repeatlastcommand"></a><span data-ttu-id="eded8-310">RepeatLastCommand</span><span class="sxs-lookup"><span data-stu-id="eded8-310">RepeatLastCommand</span></span>

<span data-ttu-id="eded8-311">Répète la dernière modification de texte.</span><span class="sxs-lookup"><span data-stu-id="eded8-311">Repeat the last text modification.</span></span>

- <span data-ttu-id="eded8-312">Mode de commande VI : `<.>`</span><span class="sxs-lookup"><span data-stu-id="eded8-312">Vi command mode: `<.>`</span></span>

### <a name="revertline"></a><span data-ttu-id="eded8-313">RevertLine</span><span class="sxs-lookup"><span data-stu-id="eded8-313">RevertLine</span></span>

<span data-ttu-id="eded8-314">Rétablit toutes les entrées de l’entrée actuelle.</span><span class="sxs-lookup"><span data-stu-id="eded8-314">Reverts all of the input to the current input.</span></span>

- <span data-ttu-id="eded8-315">Cmd `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="eded8-315">Cmd: `<Escape>`</span></span>
- <span data-ttu-id="eded8-316">Emacs- `<Alt+r>` , `<Escape,r>`</span><span class="sxs-lookup"><span data-stu-id="eded8-316">Emacs: `<Alt+r>`, `<Escape,r>`</span></span>

### <a name="shellbackwardkillword"></a><span data-ttu-id="eded8-317">ShellBackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="eded8-317">ShellBackwardKillWord</span></span>

<span data-ttu-id="eded8-318">Efface l’entrée du début du mot actuel jusqu’au curseur.</span><span class="sxs-lookup"><span data-stu-id="eded8-318">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="eded8-319">Si le curseur se trouve entre des mots, l’entrée est effacée du début du mot précédent au curseur.</span><span class="sxs-lookup"><span data-stu-id="eded8-319">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="eded8-320">Le texte effacé est placé dans le Kill-Ring.</span><span class="sxs-lookup"><span data-stu-id="eded8-320">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="eded8-321">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="eded8-321">Function is unbound.</span></span>

### <a name="shellkillword"></a><span data-ttu-id="eded8-322">ShellKillWord</span><span class="sxs-lookup"><span data-stu-id="eded8-322">ShellKillWord</span></span>

<span data-ttu-id="eded8-323">Efface l’entrée du curseur jusqu’à la fin du mot actuel.</span><span class="sxs-lookup"><span data-stu-id="eded8-323">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="eded8-324">Si le curseur se trouve entre des mots, l’entrée est effacée du curseur jusqu’à la fin du mot suivant.</span><span class="sxs-lookup"><span data-stu-id="eded8-324">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="eded8-325">Le texte effacé est placé dans le Kill-Ring.</span><span class="sxs-lookup"><span data-stu-id="eded8-325">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="eded8-326">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="eded8-326">Function is unbound.</span></span>

### <a name="swapcharacters"></a><span data-ttu-id="eded8-327">SwapCharacters</span><span class="sxs-lookup"><span data-stu-id="eded8-327">SwapCharacters</span></span>

<span data-ttu-id="eded8-328">Permuter le caractère actuel et celui qui le précèdent.</span><span class="sxs-lookup"><span data-stu-id="eded8-328">Swap the current character and the one before it.</span></span>

- <span data-ttu-id="eded8-329">Emacs- `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="eded8-329">Emacs: `<Ctrl+t>`</span></span>
- <span data-ttu-id="eded8-330">Mode d’insertion VI : `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="eded8-330">Vi insert mode: `<Ctrl+t>`</span></span>
- <span data-ttu-id="eded8-331">Mode de commande VI : `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="eded8-331">Vi command mode: `<Ctrl+t>`</span></span>

### <a name="undo"></a><span data-ttu-id="eded8-332">Annuler</span><span class="sxs-lookup"><span data-stu-id="eded8-332">Undo</span></span>

<span data-ttu-id="eded8-333">Annuler une modification précédente.</span><span class="sxs-lookup"><span data-stu-id="eded8-333">Undo a previous edit.</span></span>

- <span data-ttu-id="eded8-334">Cmd `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="eded8-334">Cmd: `<Ctrl+z>`</span></span>
- <span data-ttu-id="eded8-335">Emacs- `<Ctrl+_>` , `<Ctrl+x,Ctrl+u>`</span><span class="sxs-lookup"><span data-stu-id="eded8-335">Emacs: `<Ctrl+_>`, `<Ctrl+x,Ctrl+u>`</span></span>
- <span data-ttu-id="eded8-336">Mode d’insertion VI : `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="eded8-336">Vi insert mode: `<Ctrl+z>`</span></span>
- <span data-ttu-id="eded8-337">Mode de commande VI : `<Ctrl+z>` , `<u>`</span><span class="sxs-lookup"><span data-stu-id="eded8-337">Vi command mode: `<Ctrl+z>`, `<u>`</span></span>

### <a name="undoall"></a><span data-ttu-id="eded8-338">UndoAll</span><span class="sxs-lookup"><span data-stu-id="eded8-338">UndoAll</span></span>

<span data-ttu-id="eded8-339">Annule toutes les modifications précédentes pour la ligne.</span><span class="sxs-lookup"><span data-stu-id="eded8-339">Undo all previous edits for line.</span></span>

- <span data-ttu-id="eded8-340">Mode de commande VI : `<U>`</span><span class="sxs-lookup"><span data-stu-id="eded8-340">Vi command mode: `<U>`</span></span>

### <a name="unixwordrubout"></a><span data-ttu-id="eded8-341">UnixWordRubout</span><span class="sxs-lookup"><span data-stu-id="eded8-341">UnixWordRubout</span></span>

<span data-ttu-id="eded8-342">Efface l’entrée du début du mot actuel jusqu’au curseur.</span><span class="sxs-lookup"><span data-stu-id="eded8-342">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="eded8-343">Si le curseur se trouve entre des mots, l’entrée est effacée du début du mot précédent au curseur.</span><span class="sxs-lookup"><span data-stu-id="eded8-343">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="eded8-344">Le texte effacé est placé dans le Kill-Ring.</span><span class="sxs-lookup"><span data-stu-id="eded8-344">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="eded8-345">Emacs- `<Ctrl+w>`</span><span class="sxs-lookup"><span data-stu-id="eded8-345">Emacs: `<Ctrl+w>`</span></span>

### <a name="validateandacceptline"></a><span data-ttu-id="eded8-346">ValidateAndAcceptLine</span><span class="sxs-lookup"><span data-stu-id="eded8-346">ValidateAndAcceptLine</span></span>

<span data-ttu-id="eded8-347">Tentative d’exécution de l’entrée en cours.</span><span class="sxs-lookup"><span data-stu-id="eded8-347">Attempt to execute the current input.</span></span> <span data-ttu-id="eded8-348">Si l’entrée actuelle est incomplète (par exemple, il manque une parenthèse fermante, un crochet ou un guillemet, l’invite de continuation est affichée sur la ligne suivante et PSReadLine attend que les clés modifient l’entrée actuelle.</span><span class="sxs-lookup"><span data-stu-id="eded8-348">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="eded8-349">Emacs- `<Ctrl+m>`</span><span class="sxs-lookup"><span data-stu-id="eded8-349">Emacs: `<Ctrl+m>`</span></span>

### <a name="viacceptline"></a><span data-ttu-id="eded8-350">ViAcceptLine</span><span class="sxs-lookup"><span data-stu-id="eded8-350">ViAcceptLine</span></span>

<span data-ttu-id="eded8-351">Acceptez la ligne et passez en mode insertion.</span><span class="sxs-lookup"><span data-stu-id="eded8-351">Accept the line and switch to Insert mode.</span></span>

- <span data-ttu-id="eded8-352">Mode de commande VI : `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="eded8-352">Vi command mode: `<Enter>`</span></span>

### <a name="viacceptlineorexit"></a><span data-ttu-id="eded8-353">ViAcceptLineOrExit</span><span class="sxs-lookup"><span data-stu-id="eded8-353">ViAcceptLineOrExit</span></span>

<span data-ttu-id="eded8-354">Comme DeleteCharOrExit en mode emacs, mais accepte la ligne au lieu de supprimer un caractère.</span><span class="sxs-lookup"><span data-stu-id="eded8-354">Like DeleteCharOrExit in Emacs mode, but accepts the line instead of deleting a character.</span></span>

- <span data-ttu-id="eded8-355">Mode d’insertion VI : `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="eded8-355">Vi insert mode: `<Ctrl+d>`</span></span>
- <span data-ttu-id="eded8-356">Mode de commande VI : `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="eded8-356">Vi command mode: `<Ctrl+d>`</span></span>

### <a name="viappendline"></a><span data-ttu-id="eded8-357">ViAppendLine</span><span class="sxs-lookup"><span data-stu-id="eded8-357">ViAppendLine</span></span>

<span data-ttu-id="eded8-358">Une nouvelle ligne est insérée au-dessous de la ligne active.</span><span class="sxs-lookup"><span data-stu-id="eded8-358">A new line is inserted below the current line.</span></span>

- <span data-ttu-id="eded8-359">Mode de commande VI : `<o>`</span><span class="sxs-lookup"><span data-stu-id="eded8-359">Vi command mode: `<o>`</span></span>

### <a name="vibackwarddeleteglob"></a><span data-ttu-id="eded8-360">ViBackwardDeleteGlob</span><span class="sxs-lookup"><span data-stu-id="eded8-360">ViBackwardDeleteGlob</span></span>

<span data-ttu-id="eded8-361">Supprime le mot précédent, en utilisant uniquement un espace blanc comme délimiteur de mot.</span><span class="sxs-lookup"><span data-stu-id="eded8-361">Deletes the previous word, using only white space as the word delimiter.</span></span>

- <span data-ttu-id="eded8-362">Mode de commande VI : `<d,B>`</span><span class="sxs-lookup"><span data-stu-id="eded8-362">Vi command mode: `<d,B>`</span></span>

### <a name="vibackwardglob"></a><span data-ttu-id="eded8-363">ViBackwardGlob</span><span class="sxs-lookup"><span data-stu-id="eded8-363">ViBackwardGlob</span></span>

<span data-ttu-id="eded8-364">Déplace le curseur au début du mot précédent, en utilisant uniquement des espaces blancs comme délimiteurs.</span><span class="sxs-lookup"><span data-stu-id="eded8-364">Moves the cursor back to the beginning of the previous word, using only white space as delimiters.</span></span>

- <span data-ttu-id="eded8-365">Mode de commande VI : `<B>`</span><span class="sxs-lookup"><span data-stu-id="eded8-365">Vi command mode: `<B>`</span></span>

### <a name="videletebrace"></a><span data-ttu-id="eded8-366">ViDeleteBrace</span><span class="sxs-lookup"><span data-stu-id="eded8-366">ViDeleteBrace</span></span>

<span data-ttu-id="eded8-367">Recherchez l’accolade correspondante, la parenthèse ou le crochet, et supprimez tout le contenu dans, y compris l’accolade.</span><span class="sxs-lookup"><span data-stu-id="eded8-367">Find the matching brace, parenthesis, or square bracket and delete all contents within, including the brace.</span></span>

- <span data-ttu-id="eded8-368">Mode de commande VI : `<d,%>`</span><span class="sxs-lookup"><span data-stu-id="eded8-368">Vi command mode: `<d,%>`</span></span>

### <a name="videleteendofglob"></a><span data-ttu-id="eded8-369">ViDeleteEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="eded8-369">ViDeleteEndOfGlob</span></span>

<span data-ttu-id="eded8-370">Supprimer à la fin du mot.</span><span class="sxs-lookup"><span data-stu-id="eded8-370">Delete to the end of the word.</span></span>

- <span data-ttu-id="eded8-371">Mode de commande VI : `<d,E>`</span><span class="sxs-lookup"><span data-stu-id="eded8-371">Vi command mode: `<d,E>`</span></span>

### <a name="videleteglob"></a><span data-ttu-id="eded8-372">ViDeleteGlob</span><span class="sxs-lookup"><span data-stu-id="eded8-372">ViDeleteGlob</span></span>

<span data-ttu-id="eded8-373">Supprime la glob suivante (mot blanc délimité par des espaces).</span><span class="sxs-lookup"><span data-stu-id="eded8-373">Delete the next glob (white space delimited word).</span></span>

- <span data-ttu-id="eded8-374">Mode de commande VI : `<d,W>`</span><span class="sxs-lookup"><span data-stu-id="eded8-374">Vi command mode: `<d,W>`</span></span>

### <a name="videletetobeforechar"></a><span data-ttu-id="eded8-375">ViDeleteToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="eded8-375">ViDeleteToBeforeChar</span></span>

<span data-ttu-id="eded8-376">Supprime jusqu’au caractère donné.</span><span class="sxs-lookup"><span data-stu-id="eded8-376">Deletes until given character.</span></span>

- <span data-ttu-id="eded8-377">Mode de commande VI : `<d,t>`</span><span class="sxs-lookup"><span data-stu-id="eded8-377">Vi command mode: `<d,t>`</span></span>

### <a name="videletetobeforecharbackward"></a><span data-ttu-id="eded8-378">ViDeleteToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="eded8-378">ViDeleteToBeforeCharBackward</span></span>

<span data-ttu-id="eded8-379">Supprime jusqu’au caractère donné.</span><span class="sxs-lookup"><span data-stu-id="eded8-379">Deletes until given character.</span></span>

- <span data-ttu-id="eded8-380">Mode de commande VI : `<d,T>`</span><span class="sxs-lookup"><span data-stu-id="eded8-380">Vi command mode: `<d,T>`</span></span>

### <a name="videletetochar"></a><span data-ttu-id="eded8-381">ViDeleteToChar</span><span class="sxs-lookup"><span data-stu-id="eded8-381">ViDeleteToChar</span></span>

<span data-ttu-id="eded8-382">Supprime jusqu’au caractère donné.</span><span class="sxs-lookup"><span data-stu-id="eded8-382">Deletes until given character.</span></span>

- <span data-ttu-id="eded8-383">Mode de commande VI : `<d,f>`</span><span class="sxs-lookup"><span data-stu-id="eded8-383">Vi command mode: `<d,f>`</span></span>

### <a name="videletetocharbackward"></a><span data-ttu-id="eded8-384">ViDeleteToCharBackward</span><span class="sxs-lookup"><span data-stu-id="eded8-384">ViDeleteToCharBackward</span></span>

<span data-ttu-id="eded8-385">Supprime vers l’arrière jusqu’au caractère donné.</span><span class="sxs-lookup"><span data-stu-id="eded8-385">Deletes backwards until given character.</span></span>

- <span data-ttu-id="eded8-386">Mode de commande VI : `<d,F>`</span><span class="sxs-lookup"><span data-stu-id="eded8-386">Vi command mode: `<d,F>`</span></span>

### <a name="viinsertatbegining"></a><span data-ttu-id="eded8-387">ViInsertAtBegining</span><span class="sxs-lookup"><span data-stu-id="eded8-387">ViInsertAtBegining</span></span>

<span data-ttu-id="eded8-388">Basculez en mode insertion et positionnez le curseur au début de la ligne.</span><span class="sxs-lookup"><span data-stu-id="eded8-388">Switch to Insert mode and position the cursor at the beginning of the line.</span></span>

- <span data-ttu-id="eded8-389">Mode de commande VI : `<I>`</span><span class="sxs-lookup"><span data-stu-id="eded8-389">Vi command mode: `<I>`</span></span>

### <a name="viinsertatend"></a><span data-ttu-id="eded8-390">ViInsertAtEnd</span><span class="sxs-lookup"><span data-stu-id="eded8-390">ViInsertAtEnd</span></span>

<span data-ttu-id="eded8-391">Basculez en mode insertion et positionnez le curseur à la fin de la ligne.</span><span class="sxs-lookup"><span data-stu-id="eded8-391">Switch to Insert mode and position the cursor at the end of the line.</span></span>

- <span data-ttu-id="eded8-392">Mode de commande VI : `<A>`</span><span class="sxs-lookup"><span data-stu-id="eded8-392">Vi command mode: `<A>`</span></span>

### <a name="viinsertline"></a><span data-ttu-id="eded8-393">ViInsertLine</span><span class="sxs-lookup"><span data-stu-id="eded8-393">ViInsertLine</span></span>

<span data-ttu-id="eded8-394">Une nouvelle ligne est insérée au-dessus de la ligne active.</span><span class="sxs-lookup"><span data-stu-id="eded8-394">A new line is inserted above the current line.</span></span>

- <span data-ttu-id="eded8-395">Mode de commande VI : `<O>`</span><span class="sxs-lookup"><span data-stu-id="eded8-395">Vi command mode: `<O>`</span></span>

### <a name="viinsertwithappend"></a><span data-ttu-id="eded8-396">ViInsertWithAppend</span><span class="sxs-lookup"><span data-stu-id="eded8-396">ViInsertWithAppend</span></span>

<span data-ttu-id="eded8-397">Ajouter à partir de la position de la ligne active.</span><span class="sxs-lookup"><span data-stu-id="eded8-397">Append from the current line position.</span></span>

- <span data-ttu-id="eded8-398">Mode de commande VI : `<a>`</span><span class="sxs-lookup"><span data-stu-id="eded8-398">Vi command mode: `<a>`</span></span>

### <a name="viinsertwithdelete"></a><span data-ttu-id="eded8-399">ViInsertWithDelete</span><span class="sxs-lookup"><span data-stu-id="eded8-399">ViInsertWithDelete</span></span>

<span data-ttu-id="eded8-400">Supprimez le caractère actuel et basculez en mode insertion.</span><span class="sxs-lookup"><span data-stu-id="eded8-400">Delete the current character and switch to Insert mode.</span></span>

- <span data-ttu-id="eded8-401">Mode de commande VI : `<s>`</span><span class="sxs-lookup"><span data-stu-id="eded8-401">Vi command mode: `<s>`</span></span>

### <a name="vijoinlines"></a><span data-ttu-id="eded8-402">ViJoinLines</span><span class="sxs-lookup"><span data-stu-id="eded8-402">ViJoinLines</span></span>

<span data-ttu-id="eded8-403">Joint la ligne active et la ligne suivante.</span><span class="sxs-lookup"><span data-stu-id="eded8-403">Joins the current line and the next line.</span></span>

- <span data-ttu-id="eded8-404">Mode de commande VI : `<J>`</span><span class="sxs-lookup"><span data-stu-id="eded8-404">Vi command mode: `<J>`</span></span>

### <a name="vireplaceline"></a><span data-ttu-id="eded8-405">ViReplaceLine</span><span class="sxs-lookup"><span data-stu-id="eded8-405">ViReplaceLine</span></span>

<span data-ttu-id="eded8-406">Effacez l’intégralité de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="eded8-406">Erase the entire command line.</span></span>

- <span data-ttu-id="eded8-407">Mode de commande VI : `<S>` , `<c,c>`</span><span class="sxs-lookup"><span data-stu-id="eded8-407">Vi command mode: `<S>`, `<c,c>`</span></span>

### <a name="vireplacetobeforechar"></a><span data-ttu-id="eded8-408">ViReplaceToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="eded8-408">ViReplaceToBeforeChar</span></span>

<span data-ttu-id="eded8-409">Remplace jusqu’au caractère donné.</span><span class="sxs-lookup"><span data-stu-id="eded8-409">Replaces until given character.</span></span>

- <span data-ttu-id="eded8-410">Mode de commande VI : `<c,t>`</span><span class="sxs-lookup"><span data-stu-id="eded8-410">Vi command mode: `<c,t>`</span></span>

### <a name="vireplacetobeforecharbackward"></a><span data-ttu-id="eded8-411">ViReplaceToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="eded8-411">ViReplaceToBeforeCharBackward</span></span>

<span data-ttu-id="eded8-412">Remplace jusqu’au caractère donné.</span><span class="sxs-lookup"><span data-stu-id="eded8-412">Replaces until given character.</span></span>

- <span data-ttu-id="eded8-413">Mode de commande VI : `<c,T>`</span><span class="sxs-lookup"><span data-stu-id="eded8-413">Vi command mode: `<c,T>`</span></span>

### <a name="vireplacetochar"></a><span data-ttu-id="eded8-414">ViReplaceToChar</span><span class="sxs-lookup"><span data-stu-id="eded8-414">ViReplaceToChar</span></span>

<span data-ttu-id="eded8-415">Supprime jusqu’au caractère donné.</span><span class="sxs-lookup"><span data-stu-id="eded8-415">Deletes until given character.</span></span>

- <span data-ttu-id="eded8-416">Mode de commande VI : `<c,f>`</span><span class="sxs-lookup"><span data-stu-id="eded8-416">Vi command mode: `<c,f>`</span></span>

### <a name="vireplacetocharbackward"></a><span data-ttu-id="eded8-417">ViReplaceToCharBackward</span><span class="sxs-lookup"><span data-stu-id="eded8-417">ViReplaceToCharBackward</span></span>

<span data-ttu-id="eded8-418">Remplace jusqu’au caractère donné.</span><span class="sxs-lookup"><span data-stu-id="eded8-418">Replaces until given character.</span></span>

- <span data-ttu-id="eded8-419">Mode de commande VI : `<c,F>`</span><span class="sxs-lookup"><span data-stu-id="eded8-419">Vi command mode: `<c,F>`</span></span>

### <a name="viyankbeginningofline"></a><span data-ttu-id="eded8-420">ViYankBeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="eded8-420">ViYankBeginningOfLine</span></span>

<span data-ttu-id="eded8-421">Yank entre le début de la mémoire tampon et le curseur.</span><span class="sxs-lookup"><span data-stu-id="eded8-421">Yank from the beginning of the buffer to the cursor.</span></span>

- <span data-ttu-id="eded8-422">Mode de commande VI : `<y,0>`</span><span class="sxs-lookup"><span data-stu-id="eded8-422">Vi command mode: `<y,0>`</span></span>

### <a name="viyankendofglob"></a><span data-ttu-id="eded8-423">ViYankEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="eded8-423">ViYankEndOfGlob</span></span>

<span data-ttu-id="eded8-424">Yank du curseur jusqu’à la fin du ou des mots.</span><span class="sxs-lookup"><span data-stu-id="eded8-424">Yank from the cursor to the end of the WORD(s).</span></span>

- <span data-ttu-id="eded8-425">Mode de commande VI : `<y,E>`</span><span class="sxs-lookup"><span data-stu-id="eded8-425">Vi command mode: `<y,E>`</span></span>

### <a name="viyankendofword"></a><span data-ttu-id="eded8-426">ViYankEndOfWord</span><span class="sxs-lookup"><span data-stu-id="eded8-426">ViYankEndOfWord</span></span>

<span data-ttu-id="eded8-427">Yank du curseur jusqu’à la fin du ou des mots.</span><span class="sxs-lookup"><span data-stu-id="eded8-427">Yank from the cursor to the end of the word(s).</span></span>

- <span data-ttu-id="eded8-428">Mode de commande VI : `<y,e>`</span><span class="sxs-lookup"><span data-stu-id="eded8-428">Vi command mode: `<y,e>`</span></span>

### <a name="viyankleft"></a><span data-ttu-id="eded8-429">ViYankLeft</span><span class="sxs-lookup"><span data-stu-id="eded8-429">ViYankLeft</span></span>

<span data-ttu-id="eded8-430">Yank caractère (s) à gauche du curseur.</span><span class="sxs-lookup"><span data-stu-id="eded8-430">Yank character(s) to the left of the cursor.</span></span>

- <span data-ttu-id="eded8-431">Mode de commande VI : `<y,h>`</span><span class="sxs-lookup"><span data-stu-id="eded8-431">Vi command mode: `<y,h>`</span></span>

### <a name="viyankline"></a><span data-ttu-id="eded8-432">ViYankLine</span><span class="sxs-lookup"><span data-stu-id="eded8-432">ViYankLine</span></span>

<span data-ttu-id="eded8-433">Yank la mémoire tampon entière.</span><span class="sxs-lookup"><span data-stu-id="eded8-433">Yank the entire buffer.</span></span>

- <span data-ttu-id="eded8-434">Mode de commande VI : `<y,y>`</span><span class="sxs-lookup"><span data-stu-id="eded8-434">Vi command mode: `<y,y>`</span></span>

### <a name="viyanknextglob"></a><span data-ttu-id="eded8-435">ViYankNextGlob</span><span class="sxs-lookup"><span data-stu-id="eded8-435">ViYankNextGlob</span></span>

<span data-ttu-id="eded8-436">Yank à partir d’un curseur jusqu’au début du ou des mots suivants.</span><span class="sxs-lookup"><span data-stu-id="eded8-436">Yank from cursor to the start of the next WORD(s).</span></span>

- <span data-ttu-id="eded8-437">Mode de commande VI : `<y,W>`</span><span class="sxs-lookup"><span data-stu-id="eded8-437">Vi command mode: `<y,W>`</span></span>

### <a name="viyanknextword"></a><span data-ttu-id="eded8-438">ViYankNextWord</span><span class="sxs-lookup"><span data-stu-id="eded8-438">ViYankNextWord</span></span>

<span data-ttu-id="eded8-439">Yank le ou les mots après le curseur.</span><span class="sxs-lookup"><span data-stu-id="eded8-439">Yank the word(s) after the cursor.</span></span>

- <span data-ttu-id="eded8-440">Mode de commande VI : `<y,w>`</span><span class="sxs-lookup"><span data-stu-id="eded8-440">Vi command mode: `<y,w>`</span></span>

### <a name="viyankpercent"></a><span data-ttu-id="eded8-441">ViYankPercent</span><span class="sxs-lookup"><span data-stu-id="eded8-441">ViYankPercent</span></span>

<span data-ttu-id="eded8-442">Yank à/à partir de l’accolade correspondante.</span><span class="sxs-lookup"><span data-stu-id="eded8-442">Yank to/from matching brace.</span></span>

- <span data-ttu-id="eded8-443">Mode de commande VI : `<y,%>`</span><span class="sxs-lookup"><span data-stu-id="eded8-443">Vi command mode: `<y,%>`</span></span>

### <a name="viyankpreviousglob"></a><span data-ttu-id="eded8-444">ViYankPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="eded8-444">ViYankPreviousGlob</span></span>

<span data-ttu-id="eded8-445">Yank entre le début du ou des mots et le curseur.</span><span class="sxs-lookup"><span data-stu-id="eded8-445">Yank from beginning of the WORD(s) to cursor.</span></span>

- <span data-ttu-id="eded8-446">Mode de commande VI : `<y,B>`</span><span class="sxs-lookup"><span data-stu-id="eded8-446">Vi command mode: `<y,B>`</span></span>

### <a name="viyankpreviousword"></a><span data-ttu-id="eded8-447">ViYankPreviousWord</span><span class="sxs-lookup"><span data-stu-id="eded8-447">ViYankPreviousWord</span></span>

<span data-ttu-id="eded8-448">Yank le ou les mots avant le curseur.</span><span class="sxs-lookup"><span data-stu-id="eded8-448">Yank the word(s) before the cursor.</span></span>

- <span data-ttu-id="eded8-449">Mode de commande VI : `<y,b>`</span><span class="sxs-lookup"><span data-stu-id="eded8-449">Vi command mode: `<y,b>`</span></span>

### <a name="viyankright"></a><span data-ttu-id="eded8-450">ViYankRight</span><span class="sxs-lookup"><span data-stu-id="eded8-450">ViYankRight</span></span>

<span data-ttu-id="eded8-451">Yank caractère (s) situé sous et à droite du curseur.</span><span class="sxs-lookup"><span data-stu-id="eded8-451">Yank character(s) under and to the right of the cursor.</span></span>

- <span data-ttu-id="eded8-452">Mode de commande VI : `<y,l>` , `<y,Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="eded8-452">Vi command mode: `<y,l>`, `<y,Spacebar>`</span></span>

### <a name="viyanktoendofline"></a><span data-ttu-id="eded8-453">ViYankToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="eded8-453">ViYankToEndOfLine</span></span>

<span data-ttu-id="eded8-454">Yank du curseur jusqu’à la fin de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="eded8-454">Yank from the cursor to the end of the buffer.</span></span>

- <span data-ttu-id="eded8-455">Mode de commande VI : `<y,$>`</span><span class="sxs-lookup"><span data-stu-id="eded8-455">Vi command mode: `<y,$>`</span></span>

### <a name="viyanktofirstchar"></a><span data-ttu-id="eded8-456">ViYankToFirstChar</span><span class="sxs-lookup"><span data-stu-id="eded8-456">ViYankToFirstChar</span></span>

<span data-ttu-id="eded8-457">Yank du premier caractère autre qu’un espace blanc au curseur.</span><span class="sxs-lookup"><span data-stu-id="eded8-457">Yank from the first non-whitespace character to the cursor.</span></span>

- <span data-ttu-id="eded8-458">Mode de commande VI : `<y,^>`</span><span class="sxs-lookup"><span data-stu-id="eded8-458">Vi command mode: `<y,^>`</span></span>

### <a name="yank"></a><span data-ttu-id="eded8-459">Yank</span><span class="sxs-lookup"><span data-stu-id="eded8-459">Yank</span></span>

<span data-ttu-id="eded8-460">Ajoutez le texte le plus récemment supprimé à l’entrée.</span><span class="sxs-lookup"><span data-stu-id="eded8-460">Add the most recently killed text to the input.</span></span>

- <span data-ttu-id="eded8-461">Emacs- `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="eded8-461">Emacs: `<Ctrl+y>`</span></span>

### <a name="yanklastarg"></a><span data-ttu-id="eded8-462">YankLastArg</span><span class="sxs-lookup"><span data-stu-id="eded8-462">YankLastArg</span></span>

<span data-ttu-id="eded8-463">Yank le dernier argument de la ligne d’historique précédente.</span><span class="sxs-lookup"><span data-stu-id="eded8-463">Yank the last argument from the previous history line.</span></span> <span data-ttu-id="eded8-464">Avec un argument, la première fois qu’il est appelé, se comporte comme YankNthArg.</span><span class="sxs-lookup"><span data-stu-id="eded8-464">With an argument, the first time it is invoked, behaves just like YankNthArg.</span></span> <span data-ttu-id="eded8-465">Si elle est appelée plusieurs fois, elle itère au sein de l’historique et ARG définit la direction (négatif inverse la direction).</span><span class="sxs-lookup"><span data-stu-id="eded8-465">If invoked multiple times, instead it iterates through history and arg sets the direction (negative reverses the direction.)</span></span>

- <span data-ttu-id="eded8-466">Cmd `<Alt+.>`</span><span class="sxs-lookup"><span data-stu-id="eded8-466">Cmd: `<Alt+.>`</span></span>
- <span data-ttu-id="eded8-467">Emacs : `<Alt+.>` , `<Alt+_>` , `<Escape,.>` , `<Escape,_>`</span><span class="sxs-lookup"><span data-stu-id="eded8-467">Emacs: `<Alt+.>`, `<Alt+_>`, `<Escape,.>`, `<Escape,_>`</span></span>

### <a name="yankntharg"></a><span data-ttu-id="eded8-468">YankNthArg</span><span class="sxs-lookup"><span data-stu-id="eded8-468">YankNthArg</span></span>

<span data-ttu-id="eded8-469">Yank le premier argument (après la commande) à partir de la ligne précédente de l’historique.</span><span class="sxs-lookup"><span data-stu-id="eded8-469">Yank the first argument (after the command) from the previous history line.</span></span>
<span data-ttu-id="eded8-470">Avec un argument, Yank le nième argument (à partir de 0), si l’argument est négatif, commencez par le dernier argument.</span><span class="sxs-lookup"><span data-stu-id="eded8-470">With an argument, yank the nth argument (starting from 0), if the argument is negative, start from the last argument.</span></span>

- <span data-ttu-id="eded8-471">Emacs- `<Ctrl+Alt+y>` , `<Escape,Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="eded8-471">Emacs: `<Ctrl+Alt+y>`, `<Escape,Ctrl+y>`</span></span>

### <a name="yankpop"></a><span data-ttu-id="eded8-472">YankPop</span><span class="sxs-lookup"><span data-stu-id="eded8-472">YankPop</span></span>

<span data-ttu-id="eded8-473">Si l’opération précédente était Yank ou YankPop, remplacez le texte précédemment extrait par le texte supprimé suivant de l’instruction KILL-Ring.</span><span class="sxs-lookup"><span data-stu-id="eded8-473">If the previous operation was Yank or YankPop, replace the previously yanked text with the next killed text from the kill-ring.</span></span>

- <span data-ttu-id="eded8-474">Emacs- `<Alt+y>` , `<Escape,y>`</span><span class="sxs-lookup"><span data-stu-id="eded8-474">Emacs: `<Alt+y>`, `<Escape,y>`</span></span>

## <a name="cursor-movement-functions"></a><span data-ttu-id="eded8-475">Fonctions de déplacement de curseur</span><span class="sxs-lookup"><span data-stu-id="eded8-475">Cursor movement functions</span></span>

### <a name="backwardchar"></a><span data-ttu-id="eded8-476">BackwardChar</span><span class="sxs-lookup"><span data-stu-id="eded8-476">BackwardChar</span></span>

<span data-ttu-id="eded8-477">Déplacer le curseur d’un caractère vers la gauche.</span><span class="sxs-lookup"><span data-stu-id="eded8-477">Move the cursor one character to the left.</span></span> <span data-ttu-id="eded8-478">Cela peut déplacer le curseur vers la ligne précédente de l’entrée multiligne.</span><span class="sxs-lookup"><span data-stu-id="eded8-478">This may move the cursor to the previous line of multi-line input.</span></span>

- <span data-ttu-id="eded8-479">Cmd `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="eded8-479">Cmd: `<LeftArrow>`</span></span>
- <span data-ttu-id="eded8-480">Emacs- `<LeftArrow>` , `<Ctrl+b>`</span><span class="sxs-lookup"><span data-stu-id="eded8-480">Emacs: `<LeftArrow>`, `<Ctrl+b>`</span></span>

### <a name="backwardword"></a><span data-ttu-id="eded8-481">BackwardWord</span><span class="sxs-lookup"><span data-stu-id="eded8-481">BackwardWord</span></span>

<span data-ttu-id="eded8-482">Ramener le curseur au début du mot actuel, ou si entre les mots, le début du mot précédent.</span><span class="sxs-lookup"><span data-stu-id="eded8-482">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="eded8-483">Les limites de mots sont définies par un jeu de caractères configurable.</span><span class="sxs-lookup"><span data-stu-id="eded8-483">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="eded8-484">Cmd `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="eded8-484">Cmd: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="eded8-485">Emacs- `<Alt+b>` , `<Escape,b>`</span><span class="sxs-lookup"><span data-stu-id="eded8-485">Emacs: `<Alt+b>`, `<Escape,b>`</span></span>
- <span data-ttu-id="eded8-486">Mode d’insertion VI : `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="eded8-486">Vi insert mode: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="eded8-487">Mode de commande VI : `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="eded8-487">Vi command mode: `<Ctrl+LeftArrow>`</span></span>

### <a name="beginningofline"></a><span data-ttu-id="eded8-488">BeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="eded8-488">BeginningOfLine</span></span>

<span data-ttu-id="eded8-489">Si l’entrée comporte plusieurs lignes, se déplacer au début de la ligne active ou, le cas échéant, au début de la ligne, se déplacer au début de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="eded8-489">If the input has multiple lines, move to the start of the current line, or if already at the start of the line, move to the start of the input.</span></span> <span data-ttu-id="eded8-490">Si l’entrée comporte une seule ligne, accédez au début de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="eded8-490">If the input has a single line, move to the start of the input.</span></span>

- <span data-ttu-id="eded8-491">Cmd `<Home>`</span><span class="sxs-lookup"><span data-stu-id="eded8-491">Cmd: `<Home>`</span></span>
- <span data-ttu-id="eded8-492">Emacs- `<Home>` , `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="eded8-492">Emacs: `<Home>`, `<Ctrl+a>`</span></span>
- <span data-ttu-id="eded8-493">Mode d’insertion VI : `<Home>`</span><span class="sxs-lookup"><span data-stu-id="eded8-493">Vi insert mode: `<Home>`</span></span>
- <span data-ttu-id="eded8-494">Mode de commande VI : `<Home>`</span><span class="sxs-lookup"><span data-stu-id="eded8-494">Vi command mode: `<Home>`</span></span>

### <a name="endofline"></a><span data-ttu-id="eded8-495">EndOfLine</span><span class="sxs-lookup"><span data-stu-id="eded8-495">EndOfLine</span></span>

<span data-ttu-id="eded8-496">Si l’entrée comporte plusieurs lignes, passez à la fin de la ligne active ou, si elle se trouve déjà à la fin de la ligne, à la fin de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="eded8-496">If the input has multiple lines, move to the end of the current line, or if already at the end of the line, move to the end of the input.</span></span> <span data-ttu-id="eded8-497">Si l’entrée comporte une seule ligne, passez à la fin de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="eded8-497">If the input has a single line, move to the end of the input.</span></span>

- <span data-ttu-id="eded8-498">Cmd `<End>`</span><span class="sxs-lookup"><span data-stu-id="eded8-498">Cmd: `<End>`</span></span>
- <span data-ttu-id="eded8-499">Emacs- `<End>` , `<Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="eded8-499">Emacs: `<End>`, `<Ctrl+e>`</span></span>
- <span data-ttu-id="eded8-500">Mode d’insertion VI : `<End>`</span><span class="sxs-lookup"><span data-stu-id="eded8-500">Vi insert mode: `<End>`</span></span>

### <a name="forwardchar"></a><span data-ttu-id="eded8-501">ForwardChar</span><span class="sxs-lookup"><span data-stu-id="eded8-501">ForwardChar</span></span>

<span data-ttu-id="eded8-502">Déplacer le curseur d’un caractère vers la droite.</span><span class="sxs-lookup"><span data-stu-id="eded8-502">Move the cursor one character to the right.</span></span> <span data-ttu-id="eded8-503">Cela peut déplacer le curseur à la ligne suivante de l’entrée multiligne.</span><span class="sxs-lookup"><span data-stu-id="eded8-503">This may move the cursor to the next line of multi-line input.</span></span>

- <span data-ttu-id="eded8-504">Cmd `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="eded8-504">Cmd: `<RightArrow>`</span></span>
- <span data-ttu-id="eded8-505">Emacs- `<RightArrow>` , `<Ctrl+f>`</span><span class="sxs-lookup"><span data-stu-id="eded8-505">Emacs: `<RightArrow>`, `<Ctrl+f>`</span></span>

### <a name="forwardword"></a><span data-ttu-id="eded8-506">ForwardWord</span><span class="sxs-lookup"><span data-stu-id="eded8-506">ForwardWord</span></span>

<span data-ttu-id="eded8-507">Déplacer le curseur vers l’avant jusqu’à la fin du mot actuel, ou si entre les mots, à la fin du mot suivant.</span><span class="sxs-lookup"><span data-stu-id="eded8-507">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="eded8-508">Les limites de mots sont définies par un jeu de caractères configurable.</span><span class="sxs-lookup"><span data-stu-id="eded8-508">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="eded8-509">Emacs- `<Alt+f>` , `<Escape,f>`</span><span class="sxs-lookup"><span data-stu-id="eded8-509">Emacs: `<Alt+f>`, `<Escape,f>`</span></span>

### <a name="gotobrace"></a><span data-ttu-id="eded8-510">GotoBrace</span><span class="sxs-lookup"><span data-stu-id="eded8-510">GotoBrace</span></span>

<span data-ttu-id="eded8-511">Atteindre l’accolade correspondante, les parenthèses ou les crochets.</span><span class="sxs-lookup"><span data-stu-id="eded8-511">Go to the matching brace, parenthesis, or square bracket.</span></span>

- <span data-ttu-id="eded8-512">Cmd `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="eded8-512">Cmd: `<Ctrl+]>`</span></span>
- <span data-ttu-id="eded8-513">Mode d’insertion VI : `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="eded8-513">Vi insert mode: `<Ctrl+]>`</span></span>
- <span data-ttu-id="eded8-514">Mode de commande VI : `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="eded8-514">Vi command mode: `<Ctrl+]>`</span></span>

### <a name="gotocolumn"></a><span data-ttu-id="eded8-515">GotoColumn</span><span class="sxs-lookup"><span data-stu-id="eded8-515">GotoColumn</span></span>

<span data-ttu-id="eded8-516">Accédez à la colonne indiquée par arg.</span><span class="sxs-lookup"><span data-stu-id="eded8-516">Move to the column indicated by arg.</span></span>

- <span data-ttu-id="eded8-517">Mode de commande VI : `<|>`</span><span class="sxs-lookup"><span data-stu-id="eded8-517">Vi command mode: `<|>`</span></span>

### <a name="gotofirstnonblankofline"></a><span data-ttu-id="eded8-518">GotoFirstNonBlankOfLine</span><span class="sxs-lookup"><span data-stu-id="eded8-518">GotoFirstNonBlankOfLine</span></span>

<span data-ttu-id="eded8-519">Placez le curseur sur le premier caractère non vide de la ligne.</span><span class="sxs-lookup"><span data-stu-id="eded8-519">Move the cursor to the first non-blank character in the line.</span></span>

- <span data-ttu-id="eded8-520">Mode de commande VI : `<^>` , `<_>`</span><span class="sxs-lookup"><span data-stu-id="eded8-520">Vi command mode: `<^>`, `<_>`</span></span>

### <a name="movetoendofline"></a><span data-ttu-id="eded8-521">MoveToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="eded8-521">MoveToEndOfLine</span></span>

<span data-ttu-id="eded8-522">Placez le curseur à la fin de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="eded8-522">Move the cursor to the end of the input.</span></span>

- <span data-ttu-id="eded8-523">Mode de commande VI : `<End>` , `<$>`</span><span class="sxs-lookup"><span data-stu-id="eded8-523">Vi command mode: `<End>`, `<$>`</span></span>

### <a name="nextline"></a><span data-ttu-id="eded8-524">NextLine</span><span class="sxs-lookup"><span data-stu-id="eded8-524">NextLine</span></span>

<span data-ttu-id="eded8-525">Déplacer le curseur sur la ligne suivante.</span><span class="sxs-lookup"><span data-stu-id="eded8-525">Move the cursor to the next line.</span></span>

- <span data-ttu-id="eded8-526">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="eded8-526">Function is unbound.</span></span>

### <a name="nextword"></a><span data-ttu-id="eded8-527">NextWord</span><span class="sxs-lookup"><span data-stu-id="eded8-527">NextWord</span></span>

<span data-ttu-id="eded8-528">Déplacer le curseur vers l’avant jusqu’au début du mot suivant.</span><span class="sxs-lookup"><span data-stu-id="eded8-528">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="eded8-529">Les limites de mots sont définies par un jeu de caractères configurable.</span><span class="sxs-lookup"><span data-stu-id="eded8-529">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="eded8-530">Cmd `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="eded8-530">Cmd: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="eded8-531">Mode d’insertion VI : `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="eded8-531">Vi insert mode: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="eded8-532">Mode de commande VI : `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="eded8-532">Vi command mode: `<Ctrl+RightArrow>`</span></span>

### <a name="nextwordend"></a><span data-ttu-id="eded8-533">NextWordEnd</span><span class="sxs-lookup"><span data-stu-id="eded8-533">NextWordEnd</span></span>

<span data-ttu-id="eded8-534">Déplacer le curseur vers l’avant jusqu’à la fin du mot actuel, ou si entre les mots, à la fin du mot suivant.</span><span class="sxs-lookup"><span data-stu-id="eded8-534">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="eded8-535">Les limites de mots sont définies par un jeu de caractères configurable.</span><span class="sxs-lookup"><span data-stu-id="eded8-535">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="eded8-536">Mode de commande VI : `<e>`</span><span class="sxs-lookup"><span data-stu-id="eded8-536">Vi command mode: `<e>`</span></span>

### <a name="previousline"></a><span data-ttu-id="eded8-537">PreviousLine</span><span class="sxs-lookup"><span data-stu-id="eded8-537">PreviousLine</span></span>

<span data-ttu-id="eded8-538">Placez le curseur sur la ligne précédente.</span><span class="sxs-lookup"><span data-stu-id="eded8-538">Move the cursor to the previous line.</span></span>

- <span data-ttu-id="eded8-539">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="eded8-539">Function is unbound.</span></span>

### <a name="shellbackwardword"></a><span data-ttu-id="eded8-540">ShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="eded8-540">ShellBackwardWord</span></span>

<span data-ttu-id="eded8-541">Ramener le curseur au début du mot actuel, ou si entre les mots, le début du mot précédent.</span><span class="sxs-lookup"><span data-stu-id="eded8-541">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="eded8-542">Les limites de mots sont définies par les jetons PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eded8-542">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="eded8-543">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="eded8-543">Function is unbound.</span></span>

### <a name="shellforwardword"></a><span data-ttu-id="eded8-544">ShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="eded8-544">ShellForwardWord</span></span>

<span data-ttu-id="eded8-545">Déplacer le curseur vers l’avant jusqu’au début du mot suivant.</span><span class="sxs-lookup"><span data-stu-id="eded8-545">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="eded8-546">Les limites de mots sont définies par les jetons PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eded8-546">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="eded8-547">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="eded8-547">Function is unbound.</span></span>

### <a name="shellnextword"></a><span data-ttu-id="eded8-548">ShellNextWord</span><span class="sxs-lookup"><span data-stu-id="eded8-548">ShellNextWord</span></span>

<span data-ttu-id="eded8-549">Déplacer le curseur vers l’avant jusqu’à la fin du mot actuel, ou si entre les mots, à la fin du mot suivant.</span><span class="sxs-lookup"><span data-stu-id="eded8-549">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="eded8-550">Les limites de mots sont définies par les jetons PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eded8-550">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="eded8-551">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="eded8-551">Function is unbound.</span></span>

### <a name="vibackwardchar"></a><span data-ttu-id="eded8-552">ViBackwardChar</span><span class="sxs-lookup"><span data-stu-id="eded8-552">ViBackwardChar</span></span>

<span data-ttu-id="eded8-553">Déplacer le curseur d’un caractère vers la gauche en mode d’édition VI.</span><span class="sxs-lookup"><span data-stu-id="eded8-553">Move the cursor one character to the left in the Vi edit mode.</span></span> <span data-ttu-id="eded8-554">Cela peut déplacer le curseur vers la ligne précédente de l’entrée multiligne.</span><span class="sxs-lookup"><span data-stu-id="eded8-554">This may move the cursor to the previous line of multi-line input.</span></span>

- <span data-ttu-id="eded8-555">Mode d’insertion VI : `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="eded8-555">Vi insert mode: `<LeftArrow>`</span></span>
- <span data-ttu-id="eded8-556">Mode de commande VI : `<LeftArrow>` , `<Backspace>` , `<h>`</span><span class="sxs-lookup"><span data-stu-id="eded8-556">Vi command mode: `<LeftArrow>`, `<Backspace>`, `<h>`</span></span>

### <a name="vibackwardword"></a><span data-ttu-id="eded8-557">ViBackwardWord</span><span class="sxs-lookup"><span data-stu-id="eded8-557">ViBackwardWord</span></span>

<span data-ttu-id="eded8-558">Ramener le curseur au début du mot actuel, ou si entre les mots, le début du mot précédent.</span><span class="sxs-lookup"><span data-stu-id="eded8-558">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="eded8-559">Les limites de mots sont définies par un jeu de caractères configurable.</span><span class="sxs-lookup"><span data-stu-id="eded8-559">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="eded8-560">Mode de commande VI : `<b>`</span><span class="sxs-lookup"><span data-stu-id="eded8-560">Vi command mode: `<b>`</span></span>

### <a name="viforwardchar"></a><span data-ttu-id="eded8-561">ViForwardChar</span><span class="sxs-lookup"><span data-stu-id="eded8-561">ViForwardChar</span></span>

<span data-ttu-id="eded8-562">Déplacer le curseur d’un caractère vers la droite en mode d’édition VI.</span><span class="sxs-lookup"><span data-stu-id="eded8-562">Move the cursor one character to the right in the Vi edit mode.</span></span> <span data-ttu-id="eded8-563">Cela peut déplacer le curseur à la ligne suivante de l’entrée multiligne.</span><span class="sxs-lookup"><span data-stu-id="eded8-563">This may move the cursor to the next line of multi-line input.</span></span>

- <span data-ttu-id="eded8-564">Mode d’insertion VI : `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="eded8-564">Vi insert mode: `<RightArrow>`</span></span>
- <span data-ttu-id="eded8-565">Mode de commande VI : `<RightArrow>` , `<Spacebar>` , `<l>`</span><span class="sxs-lookup"><span data-stu-id="eded8-565">Vi command mode: `<RightArrow>`, `<Spacebar>`, `<l>`</span></span>

### <a name="viendofglob"></a><span data-ttu-id="eded8-566">ViEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="eded8-566">ViEndOfGlob</span></span>

<span data-ttu-id="eded8-567">Déplace le curseur à la fin du mot, en utilisant uniquement des espaces blancs comme délimiteurs.</span><span class="sxs-lookup"><span data-stu-id="eded8-567">Moves the cursor to the end of the word, using only white space as delimiters.</span></span>

- <span data-ttu-id="eded8-568">Mode de commande VI : `<E>`</span><span class="sxs-lookup"><span data-stu-id="eded8-568">Vi command mode: `<E>`</span></span>

### <a name="viendofpreviousglob"></a><span data-ttu-id="eded8-569">ViEndOfPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="eded8-569">ViEndOfPreviousGlob</span></span>

<span data-ttu-id="eded8-570">Passe à la fin du mot précédent, en utilisant uniquement un espace blanc comme délimiteur de mot.</span><span class="sxs-lookup"><span data-stu-id="eded8-570">Moves to the end of the previous word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="eded8-571">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="eded8-571">Function is unbound.</span></span>

### <a name="vigotobrace"></a><span data-ttu-id="eded8-572">ViGotoBrace</span><span class="sxs-lookup"><span data-stu-id="eded8-572">ViGotoBrace</span></span>

<span data-ttu-id="eded8-573">Semblable à GotoBrace, mais est basé sur un caractère et non sur un jeton.</span><span class="sxs-lookup"><span data-stu-id="eded8-573">Similar to GotoBrace, but is character based instead of token based.</span></span>

- <span data-ttu-id="eded8-574">Mode de commande VI : `<%>`</span><span class="sxs-lookup"><span data-stu-id="eded8-574">Vi command mode: `<%>`</span></span>

### <a name="vinextglob"></a><span data-ttu-id="eded8-575">ViNextGlob</span><span class="sxs-lookup"><span data-stu-id="eded8-575">ViNextGlob</span></span>

<span data-ttu-id="eded8-576">Passe au mot suivant, en utilisant uniquement un espace blanc comme délimiteur de mot.</span><span class="sxs-lookup"><span data-stu-id="eded8-576">Moves to the next word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="eded8-577">Mode de commande VI : `<W>`</span><span class="sxs-lookup"><span data-stu-id="eded8-577">Vi command mode: `<W>`</span></span>

### <a name="vinextword"></a><span data-ttu-id="eded8-578">ViNextWord</span><span class="sxs-lookup"><span data-stu-id="eded8-578">ViNextWord</span></span>

<span data-ttu-id="eded8-579">Déplacer le curseur vers l’avant jusqu’au début du mot suivant.</span><span class="sxs-lookup"><span data-stu-id="eded8-579">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="eded8-580">Les limites de mots sont définies par un jeu de caractères configurable.</span><span class="sxs-lookup"><span data-stu-id="eded8-580">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="eded8-581">Mode de commande VI : `<w>`</span><span class="sxs-lookup"><span data-stu-id="eded8-581">Vi command mode: `<w>`</span></span>

## <a name="history-functions"></a><span data-ttu-id="eded8-582">Fonctions d’historique</span><span class="sxs-lookup"><span data-stu-id="eded8-582">History functions</span></span>

### <a name="beginningofhistory"></a><span data-ttu-id="eded8-583">BeginningOfHistory</span><span class="sxs-lookup"><span data-stu-id="eded8-583">BeginningOfHistory</span></span>

<span data-ttu-id="eded8-584">Accéder au premier élément de l’historique.</span><span class="sxs-lookup"><span data-stu-id="eded8-584">Move to the first item in the history.</span></span>

- <span data-ttu-id="eded8-585">Emacs- `<Alt+<>`</span><span class="sxs-lookup"><span data-stu-id="eded8-585">Emacs: `<Alt+<>`</span></span>

### <a name="clearhistory"></a><span data-ttu-id="eded8-586">ClearHistory</span><span class="sxs-lookup"><span data-stu-id="eded8-586">ClearHistory</span></span>

<span data-ttu-id="eded8-587">Efface l’historique dans PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="eded8-587">Clears history in PSReadLine.</span></span> <span data-ttu-id="eded8-588">Cela n’affecte pas l’historique PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eded8-588">This does not affect PowerShell history.</span></span>

- <span data-ttu-id="eded8-589">Cmd `<Alt+F7>`</span><span class="sxs-lookup"><span data-stu-id="eded8-589">Cmd: `<Alt+F7>`</span></span>

### <a name="endofhistory"></a><span data-ttu-id="eded8-590">EndOfHistory</span><span class="sxs-lookup"><span data-stu-id="eded8-590">EndOfHistory</span></span>

<span data-ttu-id="eded8-591">Accéder au dernier élément (l’entrée en cours) dans l’historique.</span><span class="sxs-lookup"><span data-stu-id="eded8-591">Move to the last item (the current input) in the history.</span></span>

- <span data-ttu-id="eded8-592">Emacs- `<Alt+>>`</span><span class="sxs-lookup"><span data-stu-id="eded8-592">Emacs: `<Alt+>>`</span></span>

### <a name="forwardsearchhistory"></a><span data-ttu-id="eded8-593">ForwardSearchHistory</span><span class="sxs-lookup"><span data-stu-id="eded8-593">ForwardSearchHistory</span></span>

<span data-ttu-id="eded8-594">Effectuer une recherche incrémentielle par progression dans l’historique.</span><span class="sxs-lookup"><span data-stu-id="eded8-594">Perform an incremental forward search through history.</span></span>

- <span data-ttu-id="eded8-595">Cmd `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="eded8-595">Cmd: `<Ctrl+s>`</span></span>
- <span data-ttu-id="eded8-596">Emacs- `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="eded8-596">Emacs: `<Ctrl+s>`</span></span>

### <a name="historysearchbackward"></a><span data-ttu-id="eded8-597">HistorySearchBackward</span><span class="sxs-lookup"><span data-stu-id="eded8-597">HistorySearchBackward</span></span>

<span data-ttu-id="eded8-598">Remplacez l’entrée actuelle par l’élément « Previous » de l’historique PSReadLine qui correspond aux caractères entre le début et l’entrée et le curseur.</span><span class="sxs-lookup"><span data-stu-id="eded8-598">Replace the current input with the 'previous' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="eded8-599">Cmd `<F8>`</span><span class="sxs-lookup"><span data-stu-id="eded8-599">Cmd: `<F8>`</span></span>

### <a name="historysearchforward"></a><span data-ttu-id="eded8-600">HistorySearchForward</span><span class="sxs-lookup"><span data-stu-id="eded8-600">HistorySearchForward</span></span>

<span data-ttu-id="eded8-601">Remplacez l’entrée actuelle par l’élément « Next » de l’historique PSReadLine qui correspond aux caractères entre le début et l’entrée et le curseur.</span><span class="sxs-lookup"><span data-stu-id="eded8-601">Replace the current input with the 'next' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="eded8-602">Cmd `<Shift+F8>`</span><span class="sxs-lookup"><span data-stu-id="eded8-602">Cmd: `<Shift+F8>`</span></span>

### <a name="nexthistory"></a><span data-ttu-id="eded8-603">NextHistory</span><span class="sxs-lookup"><span data-stu-id="eded8-603">NextHistory</span></span>

<span data-ttu-id="eded8-604">Remplacez l’entrée actuelle par l’élément « Next » de l’historique PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="eded8-604">Replace the current input with the 'next' item from PSReadLine history.</span></span>

- <span data-ttu-id="eded8-605">Cmd `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="eded8-605">Cmd: `<DownArrow>`</span></span>
- <span data-ttu-id="eded8-606">Emacs- `<DownArrow>` , `<Ctrl+n>`</span><span class="sxs-lookup"><span data-stu-id="eded8-606">Emacs: `<DownArrow>`, `<Ctrl+n>`</span></span>
- <span data-ttu-id="eded8-607">Mode d’insertion VI : `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="eded8-607">Vi insert mode: `<DownArrow>`</span></span>
- <span data-ttu-id="eded8-608">Mode de commande VI : `<DownArrow>` , `<j>` , `<+>`</span><span class="sxs-lookup"><span data-stu-id="eded8-608">Vi command mode: `<DownArrow>`, `<j>`, `<+>`</span></span>

### <a name="previoushistory"></a><span data-ttu-id="eded8-609">PreviousHistory</span><span class="sxs-lookup"><span data-stu-id="eded8-609">PreviousHistory</span></span>

<span data-ttu-id="eded8-610">Remplacez l’entrée actuelle par l’élément « Previous » de l’historique PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="eded8-610">Replace the current input with the 'previous' item from PSReadLine history.</span></span>

- <span data-ttu-id="eded8-611">Cmd `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="eded8-611">Cmd: `<UpArrow>`</span></span>
- <span data-ttu-id="eded8-612">Emacs- `<UpArrow>` , `<Ctrl+p>`</span><span class="sxs-lookup"><span data-stu-id="eded8-612">Emacs: `<UpArrow>`, `<Ctrl+p>`</span></span>
- <span data-ttu-id="eded8-613">Mode d’insertion VI : `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="eded8-613">Vi insert mode: `<UpArrow>`</span></span>
- <span data-ttu-id="eded8-614">Mode de commande VI : `<UpArrow>` , `<k>` , `<->`</span><span class="sxs-lookup"><span data-stu-id="eded8-614">Vi command mode: `<UpArrow>`, `<k>`, `<->`</span></span>

### <a name="reversesearchhistory"></a><span data-ttu-id="eded8-615">ReverseSearchHistory</span><span class="sxs-lookup"><span data-stu-id="eded8-615">ReverseSearchHistory</span></span>

<span data-ttu-id="eded8-616">Effectuer une recherche incrémentielle incrémentielle dans l’historique.</span><span class="sxs-lookup"><span data-stu-id="eded8-616">Perform an incremental backward search through history.</span></span>

- <span data-ttu-id="eded8-617">Cmd `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="eded8-617">Cmd: `<Ctrl+r>`</span></span>
- <span data-ttu-id="eded8-618">Emacs- `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="eded8-618">Emacs: `<Ctrl+r>`</span></span>

### <a name="visearchhistorybackward"></a><span data-ttu-id="eded8-619">ViSearchHistoryBackward</span><span class="sxs-lookup"><span data-stu-id="eded8-619">ViSearchHistoryBackward</span></span>

<span data-ttu-id="eded8-620">Demande une chaîne de recherche et lance la recherche sur AcceptLine.</span><span class="sxs-lookup"><span data-stu-id="eded8-620">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="eded8-621">Mode d’insertion VI : `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="eded8-621">Vi insert mode: `<Ctrl+r>`</span></span>
- <span data-ttu-id="eded8-622">Mode de commande VI : `</>` , `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="eded8-622">Vi command mode: `</>`, `<Ctrl+r>`</span></span>

## <a name="completion-functions"></a><span data-ttu-id="eded8-623">Fonctions d’achèvement</span><span class="sxs-lookup"><span data-stu-id="eded8-623">Completion functions</span></span>

### <a name="complete"></a><span data-ttu-id="eded8-624">Terminé</span><span class="sxs-lookup"><span data-stu-id="eded8-624">Complete</span></span>

<span data-ttu-id="eded8-625">Tentative d’exécution de l’opération sur le texte entourant le curseur.</span><span class="sxs-lookup"><span data-stu-id="eded8-625">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="eded8-626">S’il existe plusieurs saisies semi-automatiques possibles, le plus long préfixe non ambigu est utilisé pour la finalisation.</span><span class="sxs-lookup"><span data-stu-id="eded8-626">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="eded8-627">Si vous essayez de terminer la saisie semi-automatique la plus longue, une liste des saisies semi-automatiques possibles s’affiche.</span><span class="sxs-lookup"><span data-stu-id="eded8-627">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="eded8-628">Emacs- `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="eded8-628">Emacs: `<Tab>`</span></span>

### <a name="menucomplete"></a><span data-ttu-id="eded8-629">MenuComplete</span><span class="sxs-lookup"><span data-stu-id="eded8-629">MenuComplete</span></span>

<span data-ttu-id="eded8-630">Tentative d’exécution de l’opération sur le texte entourant le curseur.</span><span class="sxs-lookup"><span data-stu-id="eded8-630">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="eded8-631">S’il existe plusieurs saisies semi-automatiques possibles, le plus long préfixe non ambigu est utilisé pour la finalisation.</span><span class="sxs-lookup"><span data-stu-id="eded8-631">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="eded8-632">Si vous essayez de terminer la saisie semi-automatique la plus longue, une liste des saisies semi-automatiques possibles s’affiche.</span><span class="sxs-lookup"><span data-stu-id="eded8-632">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="eded8-633">Cmd : `<Ctrl+@>` , `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="eded8-633">Cmd: `<Ctrl+@>`, `<Ctrl+Spacebar>`</span></span>
- <span data-ttu-id="eded8-634">Emacs- `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="eded8-634">Emacs: `<Ctrl+Spacebar>`</span></span>

### <a name="possiblecompletions"></a><span data-ttu-id="eded8-635">PossibleCompletions</span><span class="sxs-lookup"><span data-stu-id="eded8-635">PossibleCompletions</span></span>

<span data-ttu-id="eded8-636">Affiche la liste des saisies semi-automatiques possibles.</span><span class="sxs-lookup"><span data-stu-id="eded8-636">Display the list of possible completions.</span></span>

- <span data-ttu-id="eded8-637">Emacs- `<Alt+=>`</span><span class="sxs-lookup"><span data-stu-id="eded8-637">Emacs: `<Alt+=>`</span></span>
- <span data-ttu-id="eded8-638">Mode d’insertion VI : `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="eded8-638">Vi insert mode: `<Ctrl+Spacebar>`</span></span>
- <span data-ttu-id="eded8-639">Mode de commande VI : `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="eded8-639">Vi command mode: `<Ctrl+Spacebar>`</span></span>

### <a name="tabcompletenext"></a><span data-ttu-id="eded8-640">TabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="eded8-640">TabCompleteNext</span></span>

<span data-ttu-id="eded8-641">Tente de terminer le texte entourant le curseur avec la prochaine saisie semi-automatique disponible.</span><span class="sxs-lookup"><span data-stu-id="eded8-641">Attempt to complete the text surrounding the cursor with the next available completion.</span></span>

- <span data-ttu-id="eded8-642">Cmd `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="eded8-642">Cmd: `<Tab>`</span></span>
- <span data-ttu-id="eded8-643">Mode de commande VI : `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="eded8-643">Vi command mode: `<Tab>`</span></span>

### <a name="tabcompleteprevious"></a><span data-ttu-id="eded8-644">TabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="eded8-644">TabCompletePrevious</span></span>

<span data-ttu-id="eded8-645">Tente de terminer le texte entourant le curseur avec l’achèvement disponible précédent.</span><span class="sxs-lookup"><span data-stu-id="eded8-645">Attempt to complete the text surrounding the cursor with the previous available completion.</span></span>

- <span data-ttu-id="eded8-646">Cmd `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="eded8-646">Cmd: `<Shift+Tab>`</span></span>
- <span data-ttu-id="eded8-647">Mode de commande VI : `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="eded8-647">Vi command mode: `<Shift+Tab>`</span></span>

### <a name="vitabcompletenext"></a><span data-ttu-id="eded8-648">ViTabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="eded8-648">ViTabCompleteNext</span></span>

<span data-ttu-id="eded8-649">Met fin au groupe d’édition actuel, si nécessaire, et appelle TabCompleteNext.</span><span class="sxs-lookup"><span data-stu-id="eded8-649">Ends the current edit group, if needed, and invokes TabCompleteNext.</span></span>

- <span data-ttu-id="eded8-650">Mode d’insertion VI : `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="eded8-650">Vi insert mode: `<Tab>`</span></span>

### <a name="vitabcompleteprevious"></a><span data-ttu-id="eded8-651">ViTabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="eded8-651">ViTabCompletePrevious</span></span>

<span data-ttu-id="eded8-652">Met fin au groupe d’édition actuel, si nécessaire, et appelle TabCompletePrevious.</span><span class="sxs-lookup"><span data-stu-id="eded8-652">Ends the current edit group, if needed, and invokes TabCompletePrevious.</span></span>

- <span data-ttu-id="eded8-653">Mode d’insertion VI : `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="eded8-653">Vi insert mode: `<Shift+Tab>`</span></span>

## <a name="prediction-functions"></a><span data-ttu-id="eded8-654">Fonctions de prédiction</span><span class="sxs-lookup"><span data-stu-id="eded8-654">Prediction functions</span></span>

### <a name="acceptnextsuggestionword"></a><span data-ttu-id="eded8-655">AcceptNextSuggestionWord</span><span class="sxs-lookup"><span data-stu-id="eded8-655">AcceptNextSuggestionWord</span></span>

<span data-ttu-id="eded8-656">Si vous utilisez `InlineView` comme style de vue pour la prédiction, acceptez le mot suivant de la suggestion en ligne.</span><span class="sxs-lookup"><span data-stu-id="eded8-656">When using `InlineView` as the view style for prediction, accept the next word of the inline suggestion.</span></span>

- <span data-ttu-id="eded8-657">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="eded8-657">Function is unbound.</span></span>

### <a name="acceptsuggestion"></a><span data-ttu-id="eded8-658">AcceptSuggestion</span><span class="sxs-lookup"><span data-stu-id="eded8-658">AcceptSuggestion</span></span>

<span data-ttu-id="eded8-659">Si vous utilisez `InlineView` comme style de vue pour la prédiction, acceptez la suggestion en ligne actuelle.</span><span class="sxs-lookup"><span data-stu-id="eded8-659">When using `InlineView` as the view style for prediction, accept the current inline suggestion.</span></span>

- <span data-ttu-id="eded8-660">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="eded8-660">Function is unbound.</span></span>

### <a name="nextsuggestion"></a><span data-ttu-id="eded8-661">NextSuggestion</span><span class="sxs-lookup"><span data-stu-id="eded8-661">NextSuggestion</span></span>

<span data-ttu-id="eded8-662">Lorsque `ListView` vous utilisez comme style de vue pour la prédiction, accédez à la suggestion suivante dans la liste.</span><span class="sxs-lookup"><span data-stu-id="eded8-662">When using `ListView` as the view style for prediction, navigate to the next suggestion in the list.</span></span>

- <span data-ttu-id="eded8-663">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="eded8-663">Function is unbound.</span></span>

### <a name="previoussuggestion"></a><span data-ttu-id="eded8-664">PreviousSuggestion</span><span class="sxs-lookup"><span data-stu-id="eded8-664">PreviousSuggestion</span></span>

<span data-ttu-id="eded8-665">Lorsque `ListView` vous utilisez comme style de vue pour la prédiction, accédez à la suggestion précédente dans la liste.</span><span class="sxs-lookup"><span data-stu-id="eded8-665">When using `ListView` as the view style for prediction, navigate to the previous suggestion in the list.</span></span>

- <span data-ttu-id="eded8-666">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="eded8-666">Function is unbound.</span></span>

### <a name="switchpredictionview"></a><span data-ttu-id="eded8-667">SwitchPredictionView</span><span class="sxs-lookup"><span data-stu-id="eded8-667">SwitchPredictionView</span></span>

<span data-ttu-id="eded8-668">Changez le style d’affichage pour la prédiction entre `InlineView` et `ListView` .</span><span class="sxs-lookup"><span data-stu-id="eded8-668">Switch the view style for prediction between `InlineView` and `ListView`.</span></span>

- <span data-ttu-id="eded8-669">Cmd `<F2>`</span><span class="sxs-lookup"><span data-stu-id="eded8-669">Cmd: `<F2>`</span></span>

## <a name="miscellaneous-functions"></a><span data-ttu-id="eded8-670">Fonctions diverses</span><span class="sxs-lookup"><span data-stu-id="eded8-670">Miscellaneous functions</span></span>

### <a name="capturescreen"></a><span data-ttu-id="eded8-671">CaptureScreen</span><span class="sxs-lookup"><span data-stu-id="eded8-671">CaptureScreen</span></span>

<span data-ttu-id="eded8-672">Démarrer la capture d’écran interactive-flèches haut et bas sélectionnez lignes, entrez copie le texte sélectionné dans le presse-papiers en tant que texte et html.</span><span class="sxs-lookup"><span data-stu-id="eded8-672">Start interactive screen capture - up/down arrows select lines, enter copies selected text to clipboard as text and html.</span></span>

- <span data-ttu-id="eded8-673">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="eded8-673">Function is unbound.</span></span>

### <a name="clearscreen"></a><span data-ttu-id="eded8-674">ClearScreen</span><span class="sxs-lookup"><span data-stu-id="eded8-674">ClearScreen</span></span>

<span data-ttu-id="eded8-675">Effacez l’écran et dessinez la ligne active en haut de l’écran.</span><span class="sxs-lookup"><span data-stu-id="eded8-675">Clear the screen and draw the current line at the top of the screen.</span></span>

- <span data-ttu-id="eded8-676">Cmd `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="eded8-676">Cmd: `<Ctrl+l>`</span></span>
- <span data-ttu-id="eded8-677">Emacs- `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="eded8-677">Emacs: `<Ctrl+l>`</span></span>
- <span data-ttu-id="eded8-678">Mode d’insertion VI : `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="eded8-678">Vi insert mode: `<Ctrl+l>`</span></span>
- <span data-ttu-id="eded8-679">Mode de commande VI : `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="eded8-679">Vi command mode: `<Ctrl+l>`</span></span>

### <a name="digitargument"></a><span data-ttu-id="eded8-680">DigitArgument</span><span class="sxs-lookup"><span data-stu-id="eded8-680">DigitArgument</span></span>

<span data-ttu-id="eded8-681">Démarrez un nouvel argument digit à passer à d’autres fonctions.</span><span class="sxs-lookup"><span data-stu-id="eded8-681">Start a new digit argument to pass to other functions.</span></span>

- <span data-ttu-id="eded8-682">Cmd : `<Alt+0>` ,,,,, `<Alt+1>` `<Alt+2>` `<Alt+3>` `<Alt+4>` `<Alt+5>` , `<Alt+6>` , `<Alt+7>` , `<Alt+8>` , `<Alt+9>` , `<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="eded8-682">Cmd: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="eded8-683">Emacs-,,,,,,,,, `<Alt+0>` `<Alt+1>` `<Alt+2>` `<Alt+3>` `<Alt+4>` `<Alt+5>` `<Alt+6>` `<Alt+7>` `<Alt+8>` , `<Alt+9>` , `<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="eded8-683">Emacs: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="eded8-684">Mode de commande VI : `<0>` , `<1>` ,, `<2>` `<3>` , `<4>` , `<5>` , `<6>` , `<7>` , `<8>` , `<9>`</span><span class="sxs-lookup"><span data-stu-id="eded8-684">Vi command mode: `<0>`, `<1>`, `<2>`, `<3>`, `<4>`, `<5>`, `<6>`, `<7>`, `<8>`, `<9>`</span></span>

### <a name="invokeprompt"></a><span data-ttu-id="eded8-685">InvokePrompt</span><span class="sxs-lookup"><span data-stu-id="eded8-685">InvokePrompt</span></span>

<span data-ttu-id="eded8-686">Efface l’invite en cours et appelle la fonction prompt pour réafficher l’invite.</span><span class="sxs-lookup"><span data-stu-id="eded8-686">Erases the current prompt and calls the prompt function to redisplay the prompt.</span></span> <span data-ttu-id="eded8-687">Utile pour les gestionnaires de clés personnalisés qui changent d’État, par exemple modifier le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="eded8-687">Useful for custom key handlers that change state, e.g. change the current directory.</span></span>

- <span data-ttu-id="eded8-688">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="eded8-688">Function is unbound.</span></span>

### <a name="scrolldisplaydown"></a><span data-ttu-id="eded8-689">ScrollDisplayDown</span><span class="sxs-lookup"><span data-stu-id="eded8-689">ScrollDisplayDown</span></span>

<span data-ttu-id="eded8-690">Faites défiler l’écran vers le volet d’affichage.</span><span class="sxs-lookup"><span data-stu-id="eded8-690">Scroll the display down one screen.</span></span>

- <span data-ttu-id="eded8-691">Cmd `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="eded8-691">Cmd: `<PageDown>`</span></span>
- <span data-ttu-id="eded8-692">Emacs- `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="eded8-692">Emacs: `<PageDown>`</span></span>

### <a name="scrolldisplaydownline"></a><span data-ttu-id="eded8-693">ScrollDisplayDownLine</span><span class="sxs-lookup"><span data-stu-id="eded8-693">ScrollDisplayDownLine</span></span>

<span data-ttu-id="eded8-694">Faites défiler l’affichage d’une ligne vers le dessous.</span><span class="sxs-lookup"><span data-stu-id="eded8-694">Scroll the display down one line.</span></span>

- <span data-ttu-id="eded8-695">Cmd `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="eded8-695">Cmd: `<Ctrl+PageDown>`</span></span>
- <span data-ttu-id="eded8-696">Emacs- `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="eded8-696">Emacs: `<Ctrl+PageDown>`</span></span>

### <a name="scrolldisplaytocursor"></a><span data-ttu-id="eded8-697">ScrollDisplayToCursor</span><span class="sxs-lookup"><span data-stu-id="eded8-697">ScrollDisplayToCursor</span></span>

<span data-ttu-id="eded8-698">Faites défiler l’affichage jusqu’au curseur.</span><span class="sxs-lookup"><span data-stu-id="eded8-698">Scroll the display to the cursor.</span></span>

- <span data-ttu-id="eded8-699">Emacs- `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="eded8-699">Emacs: `<Ctrl+End>`</span></span>

### <a name="scrolldisplaytop"></a><span data-ttu-id="eded8-700">ScrollDisplayTop</span><span class="sxs-lookup"><span data-stu-id="eded8-700">ScrollDisplayTop</span></span>

<span data-ttu-id="eded8-701">Faites défiler l’affichage vers le haut.</span><span class="sxs-lookup"><span data-stu-id="eded8-701">Scroll the display to the top.</span></span>

- <span data-ttu-id="eded8-702">Emacs- `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="eded8-702">Emacs: `<Ctrl+Home>`</span></span>

### <a name="scrolldisplayup"></a><span data-ttu-id="eded8-703">ScrollDisplayUp</span><span class="sxs-lookup"><span data-stu-id="eded8-703">ScrollDisplayUp</span></span>

<span data-ttu-id="eded8-704">Faites défiler l’écran afficher vers le haut.</span><span class="sxs-lookup"><span data-stu-id="eded8-704">Scroll the display up one screen.</span></span>

- <span data-ttu-id="eded8-705">Cmd `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="eded8-705">Cmd: `<PageUp>`</span></span>
- <span data-ttu-id="eded8-706">Emacs- `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="eded8-706">Emacs: `<PageUp>`</span></span>

### <a name="scrolldisplayupline"></a><span data-ttu-id="eded8-707">ScrollDisplayUpLine</span><span class="sxs-lookup"><span data-stu-id="eded8-707">ScrollDisplayUpLine</span></span>

<span data-ttu-id="eded8-708">Faites défiler l’affichage d’une ligne vers le haut.</span><span class="sxs-lookup"><span data-stu-id="eded8-708">Scroll the display up one line.</span></span>

- <span data-ttu-id="eded8-709">Cmd `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="eded8-709">Cmd: `<Ctrl+PageUp>`</span></span>
- <span data-ttu-id="eded8-710">Emacs- `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="eded8-710">Emacs: `<Ctrl+PageUp>`</span></span>

### <a name="selfinsert"></a><span data-ttu-id="eded8-711">SelfInsert</span><span class="sxs-lookup"><span data-stu-id="eded8-711">SelfInsert</span></span>

<span data-ttu-id="eded8-712">Insérez la clé.</span><span class="sxs-lookup"><span data-stu-id="eded8-712">Insert the key.</span></span>

- <span data-ttu-id="eded8-713">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="eded8-713">Function is unbound.</span></span>

### <a name="showcommandhelp"></a><span data-ttu-id="eded8-714">ShowCommandHelp</span><span class="sxs-lookup"><span data-stu-id="eded8-714">ShowCommandHelp</span></span>

<span data-ttu-id="eded8-715">Fournit une vue d’ensemble de l’aide sur les applets de commande.</span><span class="sxs-lookup"><span data-stu-id="eded8-715">Provides a view of full cmdlet help.</span></span> <span data-ttu-id="eded8-716">Lorsque le curseur se trouve à la fin d’un paramètre complètement développé, le fait d’appuyer sur la `<F1>` touche positionne l’affichage de l’aide à l’emplacement de ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="eded8-716">When the cursor is at the end of a fully-expanded parameter, hitting the `<F1>` key positions the display of help at the location of that parameter.</span></span>

<span data-ttu-id="eded8-717">L’aide est affichée sur une mémoire tampon d’écran de remplacement à l’aide d’un radiomessagerie de **Microsoft. PowerShell. radiomessagerie**.</span><span class="sxs-lookup"><span data-stu-id="eded8-717">The help is displayed on an alternate screen buffer using a Pager from **Microsoft.PowerShell.Pager**.</span></span> <span data-ttu-id="eded8-718">Lorsque vous quittez le pagineur, vous revenez à la position initiale du curseur sur l’écran d’origine.</span><span class="sxs-lookup"><span data-stu-id="eded8-718">When you exit the pager you are returned to the original cursor position on the original screen.</span></span> <span data-ttu-id="eded8-719">Ce récepteur de radiomessagerie fonctionne uniquement dans les applications terminal modernes telles que [Windows Terminal](https://www.microsoft.com/en-us/p/windows-terminal/9n0dx20hk701).</span><span class="sxs-lookup"><span data-stu-id="eded8-719">This pager only works in modern terminal applications such as [Windows Terminal](https://www.microsoft.com/en-us/p/windows-terminal/9n0dx20hk701).</span></span>

- <span data-ttu-id="eded8-720">Cmd `<F1>`</span><span class="sxs-lookup"><span data-stu-id="eded8-720">Cmd: `<F1>`</span></span>
- <span data-ttu-id="eded8-721">Emacs- `<F1>`</span><span class="sxs-lookup"><span data-stu-id="eded8-721">Emacs: `<F1>`</span></span>
- <span data-ttu-id="eded8-722">Mode d’insertion VI : `<F1>`</span><span class="sxs-lookup"><span data-stu-id="eded8-722">Vi insert mode: `<F1>`</span></span>
- <span data-ttu-id="eded8-723">Mode de commande VI : `<F1>`</span><span class="sxs-lookup"><span data-stu-id="eded8-723">Vi command mode: `<F1>`</span></span>

### <a name="showkeybindings"></a><span data-ttu-id="eded8-724">ShowKeyBindings</span><span class="sxs-lookup"><span data-stu-id="eded8-724">ShowKeyBindings</span></span>

<span data-ttu-id="eded8-725">Affiche toutes les clés liées.</span><span class="sxs-lookup"><span data-stu-id="eded8-725">Show all bound keys.</span></span>

- <span data-ttu-id="eded8-726">Cmd `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="eded8-726">Cmd: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="eded8-727">Emacs- `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="eded8-727">Emacs: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="eded8-728">Mode d’insertion VI : `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="eded8-728">Vi insert mode: `<Ctrl+Alt+?>`</span></span>

### <a name="showparameterhelp"></a><span data-ttu-id="eded8-729">ShowParameterHelp</span><span class="sxs-lookup"><span data-stu-id="eded8-729">ShowParameterHelp</span></span>

<span data-ttu-id="eded8-730">Fournit une aide dynamique pour les paramètres en l’affiche sous la ligne de commande actuelle, comme `MenuComplete` .</span><span class="sxs-lookup"><span data-stu-id="eded8-730">Provides dynamic help for parameters by showing it below the current command line like `MenuComplete`.</span></span> <span data-ttu-id="eded8-731">Lorsque vous appuyez sur la touche, le curseur doit se trouver à la fin du nom de paramètre entièrement développé `<Alt+h>` .</span><span class="sxs-lookup"><span data-stu-id="eded8-731">The cursor must be at the end of the fully-expanded parameter name when you press the `<Alt+h>` key.</span></span>

- <span data-ttu-id="eded8-732">Cmd `<Alt+h>`</span><span class="sxs-lookup"><span data-stu-id="eded8-732">Cmd: `<Alt+h>`</span></span>
- <span data-ttu-id="eded8-733">Emacs- `<Alt+h>`</span><span class="sxs-lookup"><span data-stu-id="eded8-733">Emacs: `<Alt+h>`</span></span>
- <span data-ttu-id="eded8-734">Mode d’insertion VI : `<Alt+h>`</span><span class="sxs-lookup"><span data-stu-id="eded8-734">Vi insert mode: `<Alt+h>`</span></span>
- <span data-ttu-id="eded8-735">Mode de commande VI : `<Alt+h>`</span><span class="sxs-lookup"><span data-stu-id="eded8-735">Vi command mode: `<Alt+h>`</span></span>

### <a name="vicommandmode"></a><span data-ttu-id="eded8-736">ViCommandMode</span><span class="sxs-lookup"><span data-stu-id="eded8-736">ViCommandMode</span></span>

<span data-ttu-id="eded8-737">Basculez le mode d’opération actuel de Vi-Insert à VI-Command.</span><span class="sxs-lookup"><span data-stu-id="eded8-737">Switch the current operating mode from Vi-Insert to Vi-Command.</span></span>

- <span data-ttu-id="eded8-738">Mode d’insertion VI : `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="eded8-738">Vi insert mode: `<Escape>`</span></span>

### <a name="vidigitargumentinchord"></a><span data-ttu-id="eded8-739">ViDigitArgumentInChord</span><span class="sxs-lookup"><span data-stu-id="eded8-739">ViDigitArgumentInChord</span></span>

<span data-ttu-id="eded8-740">Démarrez un nouvel argument digit à passer à d’autres fonctions dans l’un des cordes de VI.</span><span class="sxs-lookup"><span data-stu-id="eded8-740">Start a new digit argument to pass to other functions while in one of vi's chords.</span></span>

- <span data-ttu-id="eded8-741">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="eded8-741">Function is unbound.</span></span>

### <a name="vieditvisually"></a><span data-ttu-id="eded8-742">ViEditVisually</span><span class="sxs-lookup"><span data-stu-id="eded8-742">ViEditVisually</span></span>

<span data-ttu-id="eded8-743">Modifiez la ligne de commande dans un éditeur de texte spécifié par $env : EDITOR ou $env : VISUAL.</span><span class="sxs-lookup"><span data-stu-id="eded8-743">Edit the command line in a text editor specified by $env:EDITOR or $env:VISUAL.</span></span>

- <span data-ttu-id="eded8-744">Emacs- `<Ctrl+x,Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="eded8-744">Emacs: `<Ctrl+x,Ctrl+e>`</span></span>
- <span data-ttu-id="eded8-745">Mode de commande VI : `<v>`</span><span class="sxs-lookup"><span data-stu-id="eded8-745">Vi command mode: `<v>`</span></span>

### <a name="viexit"></a><span data-ttu-id="eded8-746">ViExit</span><span class="sxs-lookup"><span data-stu-id="eded8-746">ViExit</span></span>

<span data-ttu-id="eded8-747">Quitte l’interpréteur de commandes.</span><span class="sxs-lookup"><span data-stu-id="eded8-747">Exits the shell.</span></span>

- <span data-ttu-id="eded8-748">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="eded8-748">Function is unbound.</span></span>

### <a name="viinsertmode"></a><span data-ttu-id="eded8-749">ViInsertMode</span><span class="sxs-lookup"><span data-stu-id="eded8-749">ViInsertMode</span></span>

<span data-ttu-id="eded8-750">Basculez en mode insertion.</span><span class="sxs-lookup"><span data-stu-id="eded8-750">Switch to Insert mode.</span></span>

- <span data-ttu-id="eded8-751">Mode de commande VI : `<i>`</span><span class="sxs-lookup"><span data-stu-id="eded8-751">Vi command mode: `<i>`</span></span>

### <a name="whatiskey"></a><span data-ttu-id="eded8-752">WhatIsKey</span><span class="sxs-lookup"><span data-stu-id="eded8-752">WhatIsKey</span></span>

<span data-ttu-id="eded8-753">Lisez une clé et dites-moi à quoi la clé est liée.</span><span class="sxs-lookup"><span data-stu-id="eded8-753">Read a key and tell me what the key is bound to.</span></span>

- <span data-ttu-id="eded8-754">Cmd `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="eded8-754">Cmd: `<Alt+?>`</span></span>
- <span data-ttu-id="eded8-755">Emacs- `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="eded8-755">Emacs: `<Alt+?>`</span></span>

## <a name="selection-functions"></a><span data-ttu-id="eded8-756">Fonctions de sélection</span><span class="sxs-lookup"><span data-stu-id="eded8-756">Selection functions</span></span>

### <a name="exchangepointandmark"></a><span data-ttu-id="eded8-757">ExchangePointAndMark</span><span class="sxs-lookup"><span data-stu-id="eded8-757">ExchangePointAndMark</span></span>

<span data-ttu-id="eded8-758">Le curseur est placé à l’emplacement de la marque et la marque est déplacée vers l’emplacement du curseur.</span><span class="sxs-lookup"><span data-stu-id="eded8-758">The cursor is placed at the location of the mark and the mark is moved to the location of the cursor.</span></span>

- <span data-ttu-id="eded8-759">Emacs- `<Ctrl+x,Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="eded8-759">Emacs: `<Ctrl+x,Ctrl+x>`</span></span>

### <a name="selectall"></a><span data-ttu-id="eded8-760">SelectAll</span><span class="sxs-lookup"><span data-stu-id="eded8-760">SelectAll</span></span>

<span data-ttu-id="eded8-761">Sélectionnez la ligne entière.</span><span class="sxs-lookup"><span data-stu-id="eded8-761">Select the entire line.</span></span>

- <span data-ttu-id="eded8-762">Cmd `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="eded8-762">Cmd: `<Ctrl+a>`</span></span>

### <a name="selectbackwardchar"></a><span data-ttu-id="eded8-763">SelectBackwardChar</span><span class="sxs-lookup"><span data-stu-id="eded8-763">SelectBackwardChar</span></span>

<span data-ttu-id="eded8-764">Ajustez la sélection actuelle pour inclure le caractère précédent.</span><span class="sxs-lookup"><span data-stu-id="eded8-764">Adjust the current selection to include the previous character.</span></span>

- <span data-ttu-id="eded8-765">Cmd `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="eded8-765">Cmd: `<Shift+LeftArrow>`</span></span>
- <span data-ttu-id="eded8-766">Emacs- `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="eded8-766">Emacs: `<Shift+LeftArrow>`</span></span>

### <a name="selectbackwardsline"></a><span data-ttu-id="eded8-767">SelectBackwardsLine</span><span class="sxs-lookup"><span data-stu-id="eded8-767">SelectBackwardsLine</span></span>

<span data-ttu-id="eded8-768">Ajustez la sélection actuelle à inclure à partir du curseur jusqu’au début de la ligne.</span><span class="sxs-lookup"><span data-stu-id="eded8-768">Adjust the current selection to include from the cursor to the start of the line.</span></span>

- <span data-ttu-id="eded8-769">Cmd `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="eded8-769">Cmd: `<Shift+Home>`</span></span>
- <span data-ttu-id="eded8-770">Emacs- `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="eded8-770">Emacs: `<Shift+Home>`</span></span>

### <a name="selectbackwardword"></a><span data-ttu-id="eded8-771">SelectBackwardWord</span><span class="sxs-lookup"><span data-stu-id="eded8-771">SelectBackwardWord</span></span>

<span data-ttu-id="eded8-772">Ajustez la sélection actuelle pour inclure le mot précédent.</span><span class="sxs-lookup"><span data-stu-id="eded8-772">Adjust the current selection to include the previous word.</span></span>

- <span data-ttu-id="eded8-773">Cmd `<Shift+Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="eded8-773">Cmd: `<Shift+Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="eded8-774">Emacs- `<Alt+B>`</span><span class="sxs-lookup"><span data-stu-id="eded8-774">Emacs: `<Alt+B>`</span></span>

### <a name="selectcommandargument"></a><span data-ttu-id="eded8-775">SelectCommandArgument</span><span class="sxs-lookup"><span data-stu-id="eded8-775">SelectCommandArgument</span></span>

<span data-ttu-id="eded8-776">Effectuez une sélection visuelle des arguments de commande.</span><span class="sxs-lookup"><span data-stu-id="eded8-776">Make visual selection of the command arguments.</span></span> <span data-ttu-id="eded8-777">La sélection des arguments est limitée au sein d’un bloc de script.</span><span class="sxs-lookup"><span data-stu-id="eded8-777">Selection of arguments is scoped within a script block.</span></span> <span data-ttu-id="eded8-778">En fonction de la position du curseur, il effectue une recherche à partir du bloc de script le plus profond dans le bloc de script le plus élevé et s’arrête lorsqu’il trouve des arguments dans une portée de bloc de script.</span><span class="sxs-lookup"><span data-stu-id="eded8-778">Based on the cursor position, it searches from the innermost script block to the outmost script block, and stops when it finds any arguments in a script block scope.</span></span>

<span data-ttu-id="eded8-779">Cette fonction honore DigitArgument.</span><span class="sxs-lookup"><span data-stu-id="eded8-779">This function honors DigitArgument.</span></span> <span data-ttu-id="eded8-780">Elle traite les valeurs d’argument positives ou négatives comme des décalages vers l’avant ou vers l’arrière à partir de l’argument actuellement sélectionné, ou à partir de la position actuelle du curseur quand aucun argument n’est sélectionné.</span><span class="sxs-lookup"><span data-stu-id="eded8-780">It treats the positive or negative argument values as the forward or backward offsets from the currently selected argument, or from the current cursor position when no argument is selected.</span></span>

- <span data-ttu-id="eded8-781">Cmd `<Alt+a>`</span><span class="sxs-lookup"><span data-stu-id="eded8-781">Cmd: `<Alt+a>`</span></span>
- <span data-ttu-id="eded8-782">Emacs- `<Alt+a>`</span><span class="sxs-lookup"><span data-stu-id="eded8-782">Emacs: `<Alt+a>`</span></span>

### <a name="selectforwardchar"></a><span data-ttu-id="eded8-783">SelectForwardChar</span><span class="sxs-lookup"><span data-stu-id="eded8-783">SelectForwardChar</span></span>

<span data-ttu-id="eded8-784">Ajustez la sélection actuelle pour inclure le caractère suivant.</span><span class="sxs-lookup"><span data-stu-id="eded8-784">Adjust the current selection to include the next character.</span></span>

- <span data-ttu-id="eded8-785">Cmd `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="eded8-785">Cmd: `<Shift+RightArrow>`</span></span>
- <span data-ttu-id="eded8-786">Emacs- `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="eded8-786">Emacs: `<Shift+RightArrow>`</span></span>

### <a name="selectforwardword"></a><span data-ttu-id="eded8-787">SelectForwardWord</span><span class="sxs-lookup"><span data-stu-id="eded8-787">SelectForwardWord</span></span>

<span data-ttu-id="eded8-788">Ajustez la sélection actuelle pour inclure le mot suivant à l’aide de ForwardWord.</span><span class="sxs-lookup"><span data-stu-id="eded8-788">Adjust the current selection to include the next word using ForwardWord.</span></span>

- <span data-ttu-id="eded8-789">Emacs- `<Alt+F>`</span><span class="sxs-lookup"><span data-stu-id="eded8-789">Emacs: `<Alt+F>`</span></span>

### <a name="selectline"></a><span data-ttu-id="eded8-790">SelectLine</span><span class="sxs-lookup"><span data-stu-id="eded8-790">SelectLine</span></span>

<span data-ttu-id="eded8-791">Ajustez la sélection actuelle à inclure à partir du curseur jusqu’à la fin de la ligne.</span><span class="sxs-lookup"><span data-stu-id="eded8-791">Adjust the current selection to include from the cursor to the end of the line.</span></span>

- <span data-ttu-id="eded8-792">Cmd `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="eded8-792">Cmd: `<Shift+End>`</span></span>
- <span data-ttu-id="eded8-793">Emacs- `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="eded8-793">Emacs: `<Shift+End>`</span></span>

### <a name="selectnextword"></a><span data-ttu-id="eded8-794">SelectNextWord</span><span class="sxs-lookup"><span data-stu-id="eded8-794">SelectNextWord</span></span>

<span data-ttu-id="eded8-795">Ajustez la sélection actuelle pour inclure le mot suivant.</span><span class="sxs-lookup"><span data-stu-id="eded8-795">Adjust the current selection to include the next word.</span></span>

- <span data-ttu-id="eded8-796">Cmd `<Shift+Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="eded8-796">Cmd: `<Shift+Ctrl+RightArrow>`</span></span>

### <a name="selectshellbackwardword"></a><span data-ttu-id="eded8-797">SelectShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="eded8-797">SelectShellBackwardWord</span></span>

<span data-ttu-id="eded8-798">Ajustez la sélection actuelle pour inclure le mot précédent à l’aide de ShellBackwardWord.</span><span class="sxs-lookup"><span data-stu-id="eded8-798">Adjust the current selection to include the previous word using ShellBackwardWord.</span></span>

- <span data-ttu-id="eded8-799">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="eded8-799">Function is unbound.</span></span>

### <a name="selectshellforwardword"></a><span data-ttu-id="eded8-800">SelectShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="eded8-800">SelectShellForwardWord</span></span>

<span data-ttu-id="eded8-801">Ajustez la sélection actuelle pour inclure le mot suivant à l’aide de ShellForwardWord.</span><span class="sxs-lookup"><span data-stu-id="eded8-801">Adjust the current selection to include the next word using ShellForwardWord.</span></span>

- <span data-ttu-id="eded8-802">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="eded8-802">Function is unbound.</span></span>

### <a name="selectshellnextword"></a><span data-ttu-id="eded8-803">SelectShellNextWord</span><span class="sxs-lookup"><span data-stu-id="eded8-803">SelectShellNextWord</span></span>

<span data-ttu-id="eded8-804">Ajustez la sélection actuelle pour inclure le mot suivant à l’aide de ShellNextWord.</span><span class="sxs-lookup"><span data-stu-id="eded8-804">Adjust the current selection to include the next word using ShellNextWord.</span></span>

- <span data-ttu-id="eded8-805">La fonction est indépendante.</span><span class="sxs-lookup"><span data-stu-id="eded8-805">Function is unbound.</span></span>

### <a name="setmark"></a><span data-ttu-id="eded8-806">SetMark</span><span class="sxs-lookup"><span data-stu-id="eded8-806">SetMark</span></span>

<span data-ttu-id="eded8-807">Marquez l’emplacement actuel du curseur pour une utilisation dans une commande d’édition suivante.</span><span class="sxs-lookup"><span data-stu-id="eded8-807">Mark the current location of the cursor for use in a subsequent editing command.</span></span>

- <span data-ttu-id="eded8-808">Emacs- `<Ctrl+@>`</span><span class="sxs-lookup"><span data-stu-id="eded8-808">Emacs: `<Ctrl+@>`</span></span>

## <a name="predictive-intellisense-functions"></a><span data-ttu-id="eded8-809">Fonctions IntelliSense prédictives</span><span class="sxs-lookup"><span data-stu-id="eded8-809">Predictive IntelliSense functions</span></span>

> [!NOTE]
> <span data-ttu-id="eded8-810">La fonctionnalité IntelliSense prédictive doit être activée pour utiliser ces fonctions.</span><span class="sxs-lookup"><span data-stu-id="eded8-810">Predictive IntelliSense needs to be enabled to use these functions.</span></span>

### <a name="acceptnextwordsuggestion"></a><span data-ttu-id="eded8-811">AcceptNextWordSuggestion</span><span class="sxs-lookup"><span data-stu-id="eded8-811">AcceptNextWordSuggestion</span></span>

<span data-ttu-id="eded8-812">Accepte le mot suivant de la suggestion en ligne de la fonctionnalité IntelliSense prédictive.</span><span class="sxs-lookup"><span data-stu-id="eded8-812">Accepts the next word of the inline suggestion from Predictive IntelliSense.</span></span>
<span data-ttu-id="eded8-813">Cette fonction peut être liée à l’aide de <kbd>CTRL</kbd> + <kbd>F</kbd> en exécutant la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="eded8-813">This function can be bound with <kbd>Ctrl</kbd>+<kbd>F</kbd> by running the following command.</span></span>

```powershell
Set-PSReadLineKeyHandler -Chord "Ctrl+f" -Function ForwardWord
```

### <a name="acceptsuggestion"></a><span data-ttu-id="eded8-814">AcceptSuggestion</span><span class="sxs-lookup"><span data-stu-id="eded8-814">AcceptSuggestion</span></span>

<span data-ttu-id="eded8-815">Accepte la suggestion en ligne actuelle de la fonctionnalité IntelliSense prédictive en appuyant sur <kbd>flèche droite</kbd> lorsque le curseur se trouve à la fin de la ligne active.</span><span class="sxs-lookup"><span data-stu-id="eded8-815">Accepts the current inline suggestion from Predictive IntelliSense by pressing <kbd>RightArrow</kbd> when the cursor is at the end of the current line.</span></span>

## <a name="search-functions"></a><span data-ttu-id="eded8-816">Fonctions de recherche</span><span class="sxs-lookup"><span data-stu-id="eded8-816">Search functions</span></span>

### <a name="charactersearch"></a><span data-ttu-id="eded8-817">CharacterSearch</span><span class="sxs-lookup"><span data-stu-id="eded8-817">CharacterSearch</span></span>

<span data-ttu-id="eded8-818">Lisez un caractère et recherchez l’occurrence suivante de ce caractère.</span><span class="sxs-lookup"><span data-stu-id="eded8-818">Read a character and search forward for the next occurrence of that character.</span></span>
<span data-ttu-id="eded8-819">Si un argument est spécifié, effectuez une recherche vers l’avant (ou vers l’arrière si négatif) pour la nième occurrence.</span><span class="sxs-lookup"><span data-stu-id="eded8-819">If an argument is specified, search forward (or backward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="eded8-820">Cmd `<F3>`</span><span class="sxs-lookup"><span data-stu-id="eded8-820">Cmd: `<F3>`</span></span>
- <span data-ttu-id="eded8-821">Emacs- `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="eded8-821">Emacs: `<Ctrl+]>`</span></span>
- <span data-ttu-id="eded8-822">Mode d’insertion VI : `<F3>`</span><span class="sxs-lookup"><span data-stu-id="eded8-822">Vi insert mode: `<F3>`</span></span>
- <span data-ttu-id="eded8-823">Mode de commande VI : `<F3>`</span><span class="sxs-lookup"><span data-stu-id="eded8-823">Vi command mode: `<F3>`</span></span>

### <a name="charactersearchbackward"></a><span data-ttu-id="eded8-824">CharacterSearchBackward</span><span class="sxs-lookup"><span data-stu-id="eded8-824">CharacterSearchBackward</span></span>

<span data-ttu-id="eded8-825">Lisez un caractère et recherchez l’occurrence suivante de ce caractère.</span><span class="sxs-lookup"><span data-stu-id="eded8-825">Read a character and search backward for the next occurrence of that character.</span></span> <span data-ttu-id="eded8-826">Si un argument est spécifié, effectuez une recherche vers l’arrière (ou vers l’avant si négatif) pour la nième occurrence.</span><span class="sxs-lookup"><span data-stu-id="eded8-826">If an argument is specified, search backward (or forward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="eded8-827">Cmd `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="eded8-827">Cmd: `<Shift+F3>`</span></span>
- <span data-ttu-id="eded8-828">Emacs- `<Ctrl+Alt+]>`</span><span class="sxs-lookup"><span data-stu-id="eded8-828">Emacs: `<Ctrl+Alt+]>`</span></span>
- <span data-ttu-id="eded8-829">Mode d’insertion VI : `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="eded8-829">Vi insert mode: `<Shift+F3>`</span></span>
- <span data-ttu-id="eded8-830">Mode de commande VI : `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="eded8-830">Vi command mode: `<Shift+F3>`</span></span>

### <a name="repeatlastcharsearch"></a><span data-ttu-id="eded8-831">RepeatLastCharSearch</span><span class="sxs-lookup"><span data-stu-id="eded8-831">RepeatLastCharSearch</span></span>

<span data-ttu-id="eded8-832">Répète la dernière recherche de caractères enregistrée.</span><span class="sxs-lookup"><span data-stu-id="eded8-832">Repeat the last recorded character search.</span></span>

- <span data-ttu-id="eded8-833">Mode de commande VI : `<;>`</span><span class="sxs-lookup"><span data-stu-id="eded8-833">Vi command mode: `<;>`</span></span>

### <a name="repeatlastcharsearchbackwards"></a><span data-ttu-id="eded8-834">RepeatLastCharSearchBackwards</span><span class="sxs-lookup"><span data-stu-id="eded8-834">RepeatLastCharSearchBackwards</span></span>

<span data-ttu-id="eded8-835">Répète la dernière recherche de caractères enregistrée, mais dans la direction opposée.</span><span class="sxs-lookup"><span data-stu-id="eded8-835">Repeat the last recorded character search, but in the opposite direction.</span></span>

- <span data-ttu-id="eded8-836">Mode de commande VI : `<,>`</span><span class="sxs-lookup"><span data-stu-id="eded8-836">Vi command mode: `<,>`</span></span>

### <a name="repeatsearch"></a><span data-ttu-id="eded8-837">RepeatSearch</span><span class="sxs-lookup"><span data-stu-id="eded8-837">RepeatSearch</span></span>

<span data-ttu-id="eded8-838">Répétez la dernière recherche dans la même direction que précédemment.</span><span class="sxs-lookup"><span data-stu-id="eded8-838">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="eded8-839">Mode de commande VI : `<n>`</span><span class="sxs-lookup"><span data-stu-id="eded8-839">Vi command mode: `<n>`</span></span>

### <a name="repeatsearchbackward"></a><span data-ttu-id="eded8-840">RepeatSearchBackward</span><span class="sxs-lookup"><span data-stu-id="eded8-840">RepeatSearchBackward</span></span>

<span data-ttu-id="eded8-841">Répétez la dernière recherche dans la même direction que précédemment.</span><span class="sxs-lookup"><span data-stu-id="eded8-841">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="eded8-842">Mode de commande VI : `<N>`</span><span class="sxs-lookup"><span data-stu-id="eded8-842">Vi command mode: `<N>`</span></span>

### <a name="searchchar"></a><span data-ttu-id="eded8-843">SearchChar</span><span class="sxs-lookup"><span data-stu-id="eded8-843">SearchChar</span></span>

<span data-ttu-id="eded8-844">Lisez le caractère suivant, puis recherchez-le, à l’avenir, puis annulez un caractère.</span><span class="sxs-lookup"><span data-stu-id="eded8-844">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="eded8-845">Il s’agit de la fonctionnalité’t'.</span><span class="sxs-lookup"><span data-stu-id="eded8-845">This is for 't' functionality.</span></span>

- <span data-ttu-id="eded8-846">Mode de commande VI : `<f>`</span><span class="sxs-lookup"><span data-stu-id="eded8-846">Vi command mode: `<f>`</span></span>

### <a name="searchcharbackward"></a><span data-ttu-id="eded8-847">SearchCharBackward</span><span class="sxs-lookup"><span data-stu-id="eded8-847">SearchCharBackward</span></span>

<span data-ttu-id="eded8-848">Lisez le caractère suivant, puis recherchez-le, en accédant à l’arrière, puis en annulant un caractère.</span><span class="sxs-lookup"><span data-stu-id="eded8-848">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="eded8-849">Il s’agit de la fonctionnalité’t'.</span><span class="sxs-lookup"><span data-stu-id="eded8-849">This is for 'T' functionality.</span></span>

- <span data-ttu-id="eded8-850">Mode de commande VI : `<F>`</span><span class="sxs-lookup"><span data-stu-id="eded8-850">Vi command mode: `<F>`</span></span>

### <a name="searchcharbackwardwithbackoff"></a><span data-ttu-id="eded8-851">SearchCharBackwardWithBackoff</span><span class="sxs-lookup"><span data-stu-id="eded8-851">SearchCharBackwardWithBackoff</span></span>

<span data-ttu-id="eded8-852">Lisez le caractère suivant, puis recherchez-le, en accédant à l’arrière, puis en annulant un caractère.</span><span class="sxs-lookup"><span data-stu-id="eded8-852">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="eded8-853">Il s’agit de la fonctionnalité’t'.</span><span class="sxs-lookup"><span data-stu-id="eded8-853">This is for 'T' functionality.</span></span>

- <span data-ttu-id="eded8-854">Mode de commande VI : `<T>`</span><span class="sxs-lookup"><span data-stu-id="eded8-854">Vi command mode: `<T>`</span></span>

### <a name="searchcharwithbackoff"></a><span data-ttu-id="eded8-855">SearchCharWithBackoff</span><span class="sxs-lookup"><span data-stu-id="eded8-855">SearchCharWithBackoff</span></span>

<span data-ttu-id="eded8-856">Lisez le caractère suivant, puis recherchez-le, à l’avenir, puis annulez un caractère.</span><span class="sxs-lookup"><span data-stu-id="eded8-856">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="eded8-857">Il s’agit de la fonctionnalité’t'.</span><span class="sxs-lookup"><span data-stu-id="eded8-857">This is for 't' functionality.</span></span>

- <span data-ttu-id="eded8-858">Mode de commande VI : `<t>`</span><span class="sxs-lookup"><span data-stu-id="eded8-858">Vi command mode: `<t>`</span></span>

### <a name="searchforward"></a><span data-ttu-id="eded8-859">SearchForward</span><span class="sxs-lookup"><span data-stu-id="eded8-859">SearchForward</span></span>

<span data-ttu-id="eded8-860">Demande une chaîne de recherche et lance la recherche sur AcceptLine.</span><span class="sxs-lookup"><span data-stu-id="eded8-860">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="eded8-861">Mode d’insertion VI : `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="eded8-861">Vi insert mode: `<Ctrl+s>`</span></span>
- <span data-ttu-id="eded8-862">Mode de commande VI : `<?>` , `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="eded8-862">Vi command mode: `<?>`, `<Ctrl+s>`</span></span>

## <a name="custom-key-bindings"></a><span data-ttu-id="eded8-863">Combinaisons de touches personnalisées</span><span class="sxs-lookup"><span data-stu-id="eded8-863">Custom Key Bindings</span></span>

<span data-ttu-id="eded8-864">PSReadLine prend en charge les combinaisons de touches personnalisées à l’aide de l’applet de commande `Set-PSReadLineKeyHandler` .</span><span class="sxs-lookup"><span data-stu-id="eded8-864">PSReadLine supports custom key bindings using the cmdlet `Set-PSReadLineKeyHandler`.</span></span> <span data-ttu-id="eded8-865">La plupart des combinaisons de touches personnalisées appellent l’une des fonctions ci-dessus, par exemple</span><span class="sxs-lookup"><span data-stu-id="eded8-865">Most custom key bindings call one of the above functions, for example</span></span>

```powershell
Set-PSReadLineKeyHandler -Key UpArrow -Function HistorySearchBackward
```

<span data-ttu-id="eded8-866">Vous pouvez lier un ScriptBlock à une clé.</span><span class="sxs-lookup"><span data-stu-id="eded8-866">You can bind a ScriptBlock to a key.</span></span> <span data-ttu-id="eded8-867">Le ScriptBlock peut faire à peu près tout ce que vous voulez.</span><span class="sxs-lookup"><span data-stu-id="eded8-867">The ScriptBlock can do pretty much anything you want.</span></span> <span data-ttu-id="eded8-868">Voici quelques exemples utiles :</span><span class="sxs-lookup"><span data-stu-id="eded8-868">Some useful examples include</span></span>

- <span data-ttu-id="eded8-869">modifier la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="eded8-869">edit the command line</span></span>
- <span data-ttu-id="eded8-870">ouverture d’une nouvelle fenêtre (par exemple, aide)</span><span class="sxs-lookup"><span data-stu-id="eded8-870">opening a new window (e.g. help)</span></span>
- <span data-ttu-id="eded8-871">modifier les répertoires sans modifier la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="eded8-871">change directories without changing the command line</span></span>

<span data-ttu-id="eded8-872">Le ScriptBlock reçoit deux arguments :</span><span class="sxs-lookup"><span data-stu-id="eded8-872">The ScriptBlock receives two arguments:</span></span>

- <span data-ttu-id="eded8-873">`$key` -Objet **[ConsoleKeyInfo]** qui est la clé qui a déclenché la liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="eded8-873">`$key` - A **[ConsoleKeyInfo]** object that is the key that triggered the custom binding.</span></span> <span data-ttu-id="eded8-874">Si vous liez le même ScriptBlock à plusieurs clés et que vous devez effectuer des actions différentes en fonction de la clé, vous pouvez vérifier $key.</span><span class="sxs-lookup"><span data-stu-id="eded8-874">If you bind the same ScriptBlock to multiple keys and need to perform different actions depending on the key, you can check $key.</span></span> <span data-ttu-id="eded8-875">De nombreuses liaisons personnalisées ignorent cet argument.</span><span class="sxs-lookup"><span data-stu-id="eded8-875">Many custom bindings ignore this argument.</span></span>

- <span data-ttu-id="eded8-876">`$arg` : Argument arbitraire.</span><span class="sxs-lookup"><span data-stu-id="eded8-876">`$arg` - An arbitrary argument.</span></span> <span data-ttu-id="eded8-877">Le plus souvent, il s’agit d’un argument entier que l’utilisateur passe à partir des combinaisons de touches DigitArgument.</span><span class="sxs-lookup"><span data-stu-id="eded8-877">Most often, this would be an integer argument that the user passes from the key bindings DigitArgument.</span></span> <span data-ttu-id="eded8-878">Si votre liaison n’accepte pas d’arguments, il est raisonnable d’ignorer cet argument.</span><span class="sxs-lookup"><span data-stu-id="eded8-878">If your binding doesn't accept arguments, it's reasonable to ignore this argument.</span></span>

<span data-ttu-id="eded8-879">Jetons un coup d’œil à un exemple qui ajoute une ligne de commande à l’historique sans l’exécuter.</span><span class="sxs-lookup"><span data-stu-id="eded8-879">Let's take a look at an example that adds a command line to history without executing it.</span></span> <span data-ttu-id="eded8-880">Cela est utile lorsque vous vous rendez compte que vous avez oublié d’effectuer une opération, mais que vous ne voulez pas entrer à nouveau la ligne de commande que vous avez déjà entrée.</span><span class="sxs-lookup"><span data-stu-id="eded8-880">This is useful when you realize you forgot to do something, but don't want to re-enter the command line you've already entered.</span></span>

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

<span data-ttu-id="eded8-881">Vous pouvez voir beaucoup plus d’exemples dans le fichier `SamplePSReadLineProfile.ps1` qui est installé dans le dossier du module PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="eded8-881">You can see many more examples in the file `SamplePSReadLineProfile.ps1` which is installed in the PSReadLine module folder.</span></span>

<span data-ttu-id="eded8-882">La plupart des combinaisons de touches utilisent des fonctions d’assistance pour la modification de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="eded8-882">Most key bindings use some helper functions for editing the command line.</span></span>
<span data-ttu-id="eded8-883">Ces API sont documentées dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="eded8-883">Those APIs are documented in the next section.</span></span>

## <a name="custom-key-binding-support-apis"></a><span data-ttu-id="eded8-884">API de prise en charge de la liaison de clé personnalisée</span><span class="sxs-lookup"><span data-stu-id="eded8-884">Custom Key Binding Support APIs</span></span>

<span data-ttu-id="eded8-885">Les fonctions suivantes sont publiques dans Microsoft. PowerShell. PSConsoleReadLine, mais ne peuvent pas être directement liées à une clé.</span><span class="sxs-lookup"><span data-stu-id="eded8-885">The following functions are public in Microsoft.PowerShell.PSConsoleReadLine, but cannot be directly bound to a key.</span></span> <span data-ttu-id="eded8-886">La plupart sont utiles dans les combinaisons de touches personnalisées.</span><span class="sxs-lookup"><span data-stu-id="eded8-886">Most are useful in custom key bindings.</span></span>

```csharp
void AddToHistory(string command)
```

<span data-ttu-id="eded8-887">Ajoutez une ligne de commande à l’historique sans l’exécuter.</span><span class="sxs-lookup"><span data-stu-id="eded8-887">Add a command line to history without executing it.</span></span>

```csharp
void ClearKillRing()
```

<span data-ttu-id="eded8-888">Effacez le point d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="eded8-888">Clear the kill-ring.</span></span>  <span data-ttu-id="eded8-889">Cela est principalement utilisé pour les tests.</span><span class="sxs-lookup"><span data-stu-id="eded8-889">This is mostly used for testing.</span></span>

```csharp
void Delete(int start, int length)
```

<span data-ttu-id="eded8-890">Supprimer les caractères de longueur du début.</span><span class="sxs-lookup"><span data-stu-id="eded8-890">Delete length characters from start.</span></span>  <span data-ttu-id="eded8-891">Cette opération prend en charge les opérations d’annulation et de rétablissement.</span><span class="sxs-lookup"><span data-stu-id="eded8-891">This operation supports undo/redo.</span></span>

```csharp
void Ding()
```

<span data-ttu-id="eded8-892">Effectuez l’action Ding en fonction des préférences de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="eded8-892">Perform the Ding action based on the users preference.</span></span>

```csharp
void GetBufferState([ref] string input, [ref] int cursor)
void GetBufferState([ref] Ast ast, [ref] Token[] tokens,
  [ref] ParseError[] parseErrors, [ref] int cursor)
```

<span data-ttu-id="eded8-893">Ces deux fonctions récupèrent des informations utiles sur l’état actuel de la mémoire tampon d’entrée.</span><span class="sxs-lookup"><span data-stu-id="eded8-893">These two functions retrieve useful information about the current state of the input buffer.</span></span>  <span data-ttu-id="eded8-894">La première est plus couramment utilisée dans les cas simples.</span><span class="sxs-lookup"><span data-stu-id="eded8-894">The first is more commonly used for simple cases.</span></span>  <span data-ttu-id="eded8-895">Le second est utilisé si votre liaison fait une opération plus avancée avec l’AST.</span><span class="sxs-lookup"><span data-stu-id="eded8-895">The second is used if your binding is doing something more advanced with the Ast.</span></span>

```csharp
IEnumerable[Microsoft.PowerShell.KeyHandler]
  GetKeyHandlers(bool includeBound, bool includeUnbound)

IEnumerable[Microsoft.PowerShell.KeyHandler]
  GetKeyHandlers(string[] Chord)
```

<span data-ttu-id="eded8-896">Ces deux fonctions sont utilisées par `Get-PSReadLineKeyHandler` .</span><span class="sxs-lookup"><span data-stu-id="eded8-896">These two functions are used by `Get-PSReadLineKeyHandler`.</span></span> <span data-ttu-id="eded8-897">La première est utilisée pour récupérer toutes les combinaisons de touches.</span><span class="sxs-lookup"><span data-stu-id="eded8-897">The first is used to get all key bindings.</span></span> <span data-ttu-id="eded8-898">Le second est utilisé pour recevoir des combinaisons de touches spécifiques.</span><span class="sxs-lookup"><span data-stu-id="eded8-898">The second is used to get specific key bindings.</span></span>

```csharp
Microsoft.PowerShell.PSConsoleReadLineOptions GetOptions()
```

<span data-ttu-id="eded8-899">Cette fonction est utilisée par Get-PSReadLineOption et n’est probablement pas trop utile dans une liaison de clé personnalisée.</span><span class="sxs-lookup"><span data-stu-id="eded8-899">This function is used by Get-PSReadLineOption and probably isn't too useful in a custom key binding.</span></span>

```csharp
void GetSelectionState([ref] int start, [ref] int length)
```

<span data-ttu-id="eded8-900">Si aucune sélection n’est effectuée sur la ligne de commande,-1 est retourné à la fois en début et en longueur.</span><span class="sxs-lookup"><span data-stu-id="eded8-900">If there is no selection on the command line, -1 will be returned in both start and length.</span></span> <span data-ttu-id="eded8-901">Si une sélection est effectuée sur la ligne de commande, le début et la longueur de la sélection sont retournés.</span><span class="sxs-lookup"><span data-stu-id="eded8-901">If there is a selection on the command line, the start and length of the selection are returned.</span></span>

```csharp
void Insert(char c)
void Insert(string s)
```

<span data-ttu-id="eded8-902">Insérez un caractère ou une chaîne au niveau du curseur.</span><span class="sxs-lookup"><span data-stu-id="eded8-902">Insert a character or string at the cursor.</span></span>  <span data-ttu-id="eded8-903">Cette opération prend en charge les opérations d’annulation et de rétablissement.</span><span class="sxs-lookup"><span data-stu-id="eded8-903">This operation supports undo/redo.</span></span>

```csharp
string ReadLine(runspace remoteRunspace,
  System.Management.Automation.EngineIntrinsics engineIntrinsics)
```

<span data-ttu-id="eded8-904">Il s’agit du point d’entrée principal de PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="eded8-904">This is the main entry point to PSReadLine.</span></span> <span data-ttu-id="eded8-905">Comme il ne prend pas en charge la récursivité, il n’est pas utile dans une liaison de clé personnalisée.</span><span class="sxs-lookup"><span data-stu-id="eded8-905">It does not support recursion, so is not useful in a custom key binding.</span></span>

```csharp
void RemoveKeyHandler(string[] key)
```

<span data-ttu-id="eded8-906">Cette fonction est utilisée par Remove-PSReadLineKeyHandler et n’est probablement pas trop utile dans une liaison de clé personnalisée.</span><span class="sxs-lookup"><span data-stu-id="eded8-906">This function is used by Remove-PSReadLineKeyHandler and probably isn't too useful in a custom key binding.</span></span>

```csharp
void Replace(int start, int length, string replacement)
```

<span data-ttu-id="eded8-907">Remplacez une partie de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="eded8-907">Replace some of the input.</span></span> <span data-ttu-id="eded8-908">Cette opération prend en charge les opérations d’annulation et de rétablissement.</span><span class="sxs-lookup"><span data-stu-id="eded8-908">This operation supports undo/redo.</span></span> <span data-ttu-id="eded8-909">C’est préférable à Delete, suivi de Insert, car il est traité comme une action unique pour Undo.</span><span class="sxs-lookup"><span data-stu-id="eded8-909">This is preferred over Delete followed by Insert because it is treated as a single action for undo.</span></span>

```csharp
void SetCursorPosition(int cursor)
```

<span data-ttu-id="eded8-910">Déplacer le curseur vers l’offset donné.</span><span class="sxs-lookup"><span data-stu-id="eded8-910">Move the cursor to the given offset.</span></span> <span data-ttu-id="eded8-911">Le déplacement du curseur n’est pas suivi pour l’annulation.</span><span class="sxs-lookup"><span data-stu-id="eded8-911">Cursor movement is not tracked for undo.</span></span>

```csharp
void SetOptions(Microsoft.PowerShell.SetPSReadLineOption options)
```

<span data-ttu-id="eded8-912">Cette fonction est une méthode d’assistance utilisée par l’applet de commande Set-PSReadLineOption, mais peut être utile pour une combinaison de touches personnalisée qui souhaite modifier temporairement un paramètre.</span><span class="sxs-lookup"><span data-stu-id="eded8-912">This function is a helper method used by the cmdlet Set-PSReadLineOption, but might be useful to a custom key binding that wants to temporarily change a setting.</span></span>

```csharp
bool TryGetArgAsInt(System.Object arg, [ref] int numericArg,
  int defaultNumericArg)
```

<span data-ttu-id="eded8-913">Cette méthode d’assistance est utilisée pour les liaisons personnalisées qui respectent DigitArgument.</span><span class="sxs-lookup"><span data-stu-id="eded8-913">This helper method is used for custom bindings that honor DigitArgument.</span></span> <span data-ttu-id="eded8-914">Un appel classique ressemble à ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="eded8-914">A typical call looks like</span></span>

```powershell
[int]$numericArg = 0
[Microsoft.PowerShell.PSConsoleReadLine]::TryGetArgAsInt($arg,
  [ref]$numericArg, 1)
```

## <a name="notes"></a><span data-ttu-id="eded8-915">Notes</span><span class="sxs-lookup"><span data-stu-id="eded8-915">Notes</span></span>

### <a name="command-history"></a><span data-ttu-id="eded8-916">Historique des commandes</span><span class="sxs-lookup"><span data-stu-id="eded8-916">Command History</span></span>

<span data-ttu-id="eded8-917">PSReadLine gère un fichier d’historique contenant toutes les commandes et données que vous avez entrées à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="eded8-917">PSReadLine maintains a history file containing all the commands and data you have entered from the command line.</span></span> <span data-ttu-id="eded8-918">Cela peut contenir des données sensibles, y compris des mots de passe.</span><span class="sxs-lookup"><span data-stu-id="eded8-918">This may contain sensitive data including passwords.</span></span> <span data-ttu-id="eded8-919">Par exemple, si vous utilisez l’applet de commande, `ConvertTo-SecureString` le mot de passe est enregistré dans le fichier d’historique sous forme de texte brut.</span><span class="sxs-lookup"><span data-stu-id="eded8-919">For example, if you use the `ConvertTo-SecureString` cmdlet the password is logged in the history file as plain text.</span></span> <span data-ttu-id="eded8-920">Les fichiers d’historique sont un fichier nommé `$($host.Name)_history.txt` .</span><span class="sxs-lookup"><span data-stu-id="eded8-920">The history files is a file named `$($host.Name)_history.txt`.</span></span> <span data-ttu-id="eded8-921">Sur les systèmes Windows, le fichier d’historique est stocké à l’adresse `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine` .</span><span class="sxs-lookup"><span data-stu-id="eded8-921">On Windows systems the history file is stored at `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine`.</span></span> <span data-ttu-id="eded8-922">Sur les systèmes non-Windows, les fichiers d’historique sont stockés dans `$env:XDG_DATA_HOME/powershell/PSReadLine` ou `$env:HOME/.local/share/powershell/PSReadLine` .</span><span class="sxs-lookup"><span data-stu-id="eded8-922">On non-Windows systems, the history files is stored at `$env:XDG_DATA_HOME/powershell/PSReadLine` or `$env:HOME/.local/share/powershell/PSReadLine`.</span></span>

### <a name="feedback--contributing-to-psreadline"></a><span data-ttu-id="eded8-923">Commentaires & contribution à PSReadLine</span><span class="sxs-lookup"><span data-stu-id="eded8-923">Feedback & Contributing To PSReadLine</span></span>

[<span data-ttu-id="eded8-924">PSReadLine sur GitHub</span><span class="sxs-lookup"><span data-stu-id="eded8-924">PSReadLine on GitHub</span></span>](https://github.com/PowerShell/PSReadLine)

<span data-ttu-id="eded8-925">N’hésitez pas à envoyer une demande de tirage ou à envoyer des commentaires sur la page GitHub.</span><span class="sxs-lookup"><span data-stu-id="eded8-925">Feel free to submit a pull request or submit feedback on the GitHub page.</span></span>

## <a name="see-also"></a><span data-ttu-id="eded8-926">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eded8-926">See Also</span></span>

<span data-ttu-id="eded8-927">PSReadLine est fortement influencé par la bibliothèque GNU [ReadLine](https://tiswww.case.edu/php/chet/readline/rltop.html) .</span><span class="sxs-lookup"><span data-stu-id="eded8-927">PSReadLine is heavily influenced by the GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) library.</span></span>
