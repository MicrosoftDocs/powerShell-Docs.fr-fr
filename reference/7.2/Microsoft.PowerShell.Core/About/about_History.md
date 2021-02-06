---
description: Décrit comment récupérer et exécuter des commandes dans l’historique des commandes.
Locale: en-US
ms.date: 05/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_history?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_History
ms.openlocfilehash: 44e03bd37b0b2c5928fb3aa850f3f5b554ccf123
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597354"
---
# <a name="about-history"></a><span data-ttu-id="b6c87-103">À propos de l’historique</span><span class="sxs-lookup"><span data-stu-id="b6c87-103">About History</span></span>

## <a name="short-description"></a><span data-ttu-id="b6c87-104">Description courte</span><span class="sxs-lookup"><span data-stu-id="b6c87-104">Short Description</span></span>
<span data-ttu-id="b6c87-105">Décrit comment récupérer et exécuter des commandes dans l’historique des commandes.</span><span class="sxs-lookup"><span data-stu-id="b6c87-105">Describes how to get and run commands in the command history.</span></span>

## <a name="long-description"></a><span data-ttu-id="b6c87-106">Description longue</span><span class="sxs-lookup"><span data-stu-id="b6c87-106">Long Description</span></span>

<span data-ttu-id="b6c87-107">Lorsque vous entrez une commande à l’invite de commandes, PowerShell enregistre la commande dans l’historique des commandes.</span><span class="sxs-lookup"><span data-stu-id="b6c87-107">When you enter a command at the command prompt, PowerShell saves the command in the command history.</span></span> <span data-ttu-id="b6c87-108">Vous pouvez utiliser les commandes de l’historique comme enregistrement de votre travail.</span><span class="sxs-lookup"><span data-stu-id="b6c87-108">You can use the commands in the history as a record of your work.</span></span> <span data-ttu-id="b6c87-109">Vous pouvez rappeler et exécuter les commandes à partir de l’historique des commandes.</span><span class="sxs-lookup"><span data-stu-id="b6c87-109">And, you can recall and run the commands from the command history.</span></span>

<span data-ttu-id="b6c87-110">PowerShell a deux fournisseurs d’historique différents : l’historique intégré et l’historique géré par le module **PSReadLine** .</span><span class="sxs-lookup"><span data-stu-id="b6c87-110">PowerShell has two different history providers: the built-in history and the history managed by the **PSReadLine** module.</span></span> <span data-ttu-id="b6c87-111">Les historiques sont gérés séparément, mais les deux historiques sont disponibles dans les sessions où **PSReadLine** est chargé.</span><span class="sxs-lookup"><span data-stu-id="b6c87-111">The histories are managed separately, but both histories are available in sessions where **PSReadLine** is loaded.</span></span>

## <a name="using-the-psreadline-history"></a><span data-ttu-id="b6c87-112">Utilisation de l’historique PSReadLine</span><span class="sxs-lookup"><span data-stu-id="b6c87-112">Using the PSReadLine history</span></span>

<span data-ttu-id="b6c87-113">L’historique PSReadLine effectue le suivi des commandes utilisées dans toutes les sessions PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b6c87-113">The PSReadLine history tracks the commands used in all PowerShell sessions.</span></span>
<span data-ttu-id="b6c87-114">L’historique est écrit dans un fichier central par hôte.</span><span class="sxs-lookup"><span data-stu-id="b6c87-114">The history is written to a central file per host.</span></span> <span data-ttu-id="b6c87-115">Ce fichier d’historique est disponible pour toutes les sessions et contient tous les historiques précédents.</span><span class="sxs-lookup"><span data-stu-id="b6c87-115">That history file is available to all sessions and contains all past history.</span></span> <span data-ttu-id="b6c87-116">L’historique n’est pas supprimé à la fin de la session.</span><span class="sxs-lookup"><span data-stu-id="b6c87-116">The history is not deleted when the session ends.</span></span> <span data-ttu-id="b6c87-117">En outre, cet historique ne peut pas être géré par les `*-History` applets de commande.</span><span class="sxs-lookup"><span data-stu-id="b6c87-117">Also, that history cannot be managed by the `*-History` cmdlets.</span></span> <span data-ttu-id="b6c87-118">Pour plus d’informations, consultez [about_PSReadLine](../../PSReadLine/About/about_PSReadLine.md).</span><span class="sxs-lookup"><span data-stu-id="b6c87-118">For more information, see [about_PSReadLine](../../PSReadLine/About/about_PSReadLine.md).</span></span>

## <a name="using-the-built-in-session-history"></a><span data-ttu-id="b6c87-119">Utilisation de l’historique de session intégré</span><span class="sxs-lookup"><span data-stu-id="b6c87-119">Using the built-in session history</span></span>

<span data-ttu-id="b6c87-120">L’historique intégré effectue uniquement le suivi des commandes utilisées dans la session active.</span><span class="sxs-lookup"><span data-stu-id="b6c87-120">The built-in history only tracks the commands used in the current session.</span></span> <span data-ttu-id="b6c87-121">L’historique n’est pas disponible pour les autres sessions et est supprimé à la fin de la session.</span><span class="sxs-lookup"><span data-stu-id="b6c87-121">The history is not available to other sessions and is deleted when the session ends.</span></span>

### <a name="history-cmdlets"></a><span data-ttu-id="b6c87-122">Applets de commande d’historique</span><span class="sxs-lookup"><span data-stu-id="b6c87-122">History Cmdlets</span></span>

<span data-ttu-id="b6c87-123">PowerShell possède un ensemble d’applets de commande qui gèrent l’historique des commandes.</span><span class="sxs-lookup"><span data-stu-id="b6c87-123">PowerShell has a set of cmdlets that manage the command history.</span></span>

| <span data-ttu-id="b6c87-124">Applet de commande</span><span class="sxs-lookup"><span data-stu-id="b6c87-124">Cmdlet</span></span>           | <span data-ttu-id="b6c87-125">Alias</span><span class="sxs-lookup"><span data-stu-id="b6c87-125">Alias</span></span>  | <span data-ttu-id="b6c87-126">Description</span><span class="sxs-lookup"><span data-stu-id="b6c87-126">Description</span></span>                                |
| ---------------- | ------ | ------------------------------------------ |
| `Get-History`    | `h`    | <span data-ttu-id="b6c87-127">Obtient l’historique de la commande.</span><span class="sxs-lookup"><span data-stu-id="b6c87-127">Gets the command history.</span></span>                  |
| `Invoke-History` | `r`    | <span data-ttu-id="b6c87-128">Exécute une commande de l'historique.</span><span class="sxs-lookup"><span data-stu-id="b6c87-128">Runs a command in the command history.</span></span>     |
| `Add-History`    |        | <span data-ttu-id="b6c87-129">Ajoute une commande à l’historique de commande.</span><span class="sxs-lookup"><span data-stu-id="b6c87-129">Adds a command to the command history.</span></span>     |
| `Clear-History`  | `clhy` | <span data-ttu-id="b6c87-130">Supprime les commandes de l’historique de commande.</span><span class="sxs-lookup"><span data-stu-id="b6c87-130">Deletes commands from the command history.</span></span> |

### <a name="keyboard-shortcuts-for-managing-history"></a><span data-ttu-id="b6c87-131">Raccourcis clavier pour la gestion de l’historique</span><span class="sxs-lookup"><span data-stu-id="b6c87-131">Keyboard Shortcuts for Managing History</span></span>

<span data-ttu-id="b6c87-132">Dans la console PowerShell, vous pouvez utiliser les raccourcis suivants pour gérer l’historique des commandes.</span><span class="sxs-lookup"><span data-stu-id="b6c87-132">In the PowerShell console, you can use the following shortcuts to manage the command history.</span></span>

- <span data-ttu-id="b6c87-133"><kbd>Flèche vers le haut</kbd> : affiche la commande précédente.</span><span class="sxs-lookup"><span data-stu-id="b6c87-133"><kbd>UpArrow</kbd> - Displays the previous command.</span></span>
- <span data-ttu-id="b6c87-134"><kbd>Flèche</kbd> vers le bas-affiche la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="b6c87-134"><kbd>DownArrow</kbd> - Displays the next command.</span></span>
- <span data-ttu-id="b6c87-135"><kbd>F7</kbd> -affiche l’historique des commandes.</span><span class="sxs-lookup"><span data-stu-id="b6c87-135"><kbd>F7</kbd> - Displays the command history.</span></span>
- <span data-ttu-id="b6c87-136"><kbd>Echap</kbd> : pour masquer l’historique.</span><span class="sxs-lookup"><span data-stu-id="b6c87-136"><kbd>ESC</kbd> - To hide the history.</span></span>
- <span data-ttu-id="b6c87-137"><kbd>F8</kbd> -recherche une commande.</span><span class="sxs-lookup"><span data-stu-id="b6c87-137"><kbd>F8</kbd> - Finds a command.</span></span> <span data-ttu-id="b6c87-138">Tapez un ou plusieurs caractères, puis appuyez sur <kbd>F8</kbd>.</span><span class="sxs-lookup"><span data-stu-id="b6c87-138">Type one or more characters then press <kbd>F8</kbd>.</span></span> <span data-ttu-id="b6c87-139">Appuyez de nouveau sur <kbd>F8</kbd> pour l’instance suivante.</span><span class="sxs-lookup"><span data-stu-id="b6c87-139">Press <kbd>F8</kbd> again the next instance.</span></span>
- <span data-ttu-id="b6c87-140"><kbd>F9</kbd> -Rechercher une commande par ID d’historique.</span><span class="sxs-lookup"><span data-stu-id="b6c87-140"><kbd>F9</kbd> - Find a command by history ID.</span></span> <span data-ttu-id="b6c87-141">Tapez l’ID de l’historique, puis appuyez sur <kbd>F9</kbd>.</span><span class="sxs-lookup"><span data-stu-id="b6c87-141">Type the history ID then press <kbd>F9</kbd>.</span></span> <span data-ttu-id="b6c87-142">Appuyez sur <kbd>F7</kbd> pour Rechercher l’ID.</span><span class="sxs-lookup"><span data-stu-id="b6c87-142">Press <kbd>F7</kbd> to find the ID.</span></span>
- <span data-ttu-id="b6c87-143"><kbd>#</kbd>`<string>`</kbd><kbd>Tab</kbd> : recherchez `*<string>*` et retourne la correspondance la plus récente dans l’historique.</span><span class="sxs-lookup"><span data-stu-id="b6c87-143"><kbd>#</kbd>`<string>`</kbd><kbd>Tab</kbd> - Search the history for `*<string>*` and returns the most recent match.</span></span> <span data-ttu-id="b6c87-144">Si vous appuyez sur <kbd>Tab</kbd> à plusieurs reprises, il parcourt les éléments correspondants dans votre historique.</span><span class="sxs-lookup"><span data-stu-id="b6c87-144">If you press <kbd>Tab</kbd> repeatedly, it cycles through the matching items in your history.</span></span>

> [!NOTE]
> <span data-ttu-id="b6c87-145">Ces combinaisons de touches sont implémentées par l’application hôte de la console.</span><span class="sxs-lookup"><span data-stu-id="b6c87-145">These key bindings are implemented by the console host application.</span></span> <span data-ttu-id="b6c87-146">D’autres applications, telles que Visual Studio Code ou Windows Terminal, peuvent avoir des combinaisons de touches différentes.</span><span class="sxs-lookup"><span data-stu-id="b6c87-146">Other applications, such as Visual Studio Code or Windows Terminal, can have different key bindings.</span></span> <span data-ttu-id="b6c87-147">Les liaisons peuvent être substituées par le module PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="b6c87-147">The bindings can be overridden by the PSReadLine module.</span></span> <span data-ttu-id="b6c87-148">PSReadLine se charge automatiquement quand vous démarrez une session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b6c87-148">PSReadLine loads automatically when you start a PowerShell session.</span></span>
> <span data-ttu-id="b6c87-149">Avec PSReadLine chargé, les fonctions <kbd>F7</kbd> et <kbd>F9</kbd> ne sont liées à aucune fonction.</span><span class="sxs-lookup"><span data-stu-id="b6c87-149">With PSReadLine loaded, <kbd>F7</kbd> and <kbd>F9</kbd> are not bound to any function.</span></span> <span data-ttu-id="b6c87-150">PSReadLine ne fournit pas de fonctionnalité équivalente.</span><span class="sxs-lookup"><span data-stu-id="b6c87-150">PSReadLine does not provide equivalent functionality.</span></span> <span data-ttu-id="b6c87-151">Pour plus d’informations, consultez [about_PSReadLine](../../PSReadLine/About/about_PSReadLine.md).</span><span class="sxs-lookup"><span data-stu-id="b6c87-151">For more information, see [about_PSReadLine](../../PSReadLine/About/about_PSReadLine.md).</span></span>

### <a name="maximumhistorycount"></a><span data-ttu-id="b6c87-152">MaximumHistoryCount</span><span class="sxs-lookup"><span data-stu-id="b6c87-152">MaximumHistoryCount</span></span>

<span data-ttu-id="b6c87-153">La `$MaximumHistoryCount` variable de préférence détermine le nombre maximal de commandes que PowerShell enregistre dans l’historique des commandes.</span><span class="sxs-lookup"><span data-stu-id="b6c87-153">The `$MaximumHistoryCount` preference variable determines the maximum number of commands that PowerShell saves in the command history.</span></span> <span data-ttu-id="b6c87-154">La valeur par défaut est</span><span class="sxs-lookup"><span data-stu-id="b6c87-154">The default value is</span></span>
4096.

<span data-ttu-id="b6c87-155">Par exemple, la commande suivante réduit les `$MaximumHistoryCount` commandes à 100 :</span><span class="sxs-lookup"><span data-stu-id="b6c87-155">For example, the following command lowers the `$MaximumHistoryCount` to 100 commands:</span></span>

```powershell
$MaximumHistoryCount = 100
```

<span data-ttu-id="b6c87-156">Pour appliquer le paramètre, redémarrez PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b6c87-156">To apply the setting, restart PowerShell.</span></span>

<span data-ttu-id="b6c87-157">Pour enregistrer la nouvelle valeur de la variable pour toutes vos sessions PowerShell, ajoutez l’instruction d’assignation à un profil PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b6c87-157">To save the new variable value for all your PowerShell sessions, add the assignment statement to a PowerShell profile.</span></span> <span data-ttu-id="b6c87-158">Pour plus d'informations sur les profils, consultez [about_Profiles](about_Profiles.md).</span><span class="sxs-lookup"><span data-stu-id="b6c87-158">For more information about profiles, see [about_Profiles](about_Profiles.md).</span></span>

<span data-ttu-id="b6c87-159">Pour plus d’informations sur la `$MaximumHistoryCount` variable de préférence, consultez [about_Preference_Variables](about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="b6c87-159">For more information about the `$MaximumHistoryCount` preference variable, see [about_Preference_Variables](about_Preference_Variables.md).</span></span>

### <a name="order-of-commands-in-the-history"></a><span data-ttu-id="b6c87-160">Ordre des commandes dans l’historique</span><span class="sxs-lookup"><span data-stu-id="b6c87-160">Order of Commands in the History</span></span>

<span data-ttu-id="b6c87-161">Les commandes sont ajoutées à l’historique à la fin de l’exécution de la commande, et non lors de l’entrée de la commande.</span><span class="sxs-lookup"><span data-stu-id="b6c87-161">Commands are added to the history when the command finishes executing, not when the command is entered.</span></span> <span data-ttu-id="b6c87-162">Si les commandes prennent un certain temps, ou si les commandes s’exécutent dans une invite imbriquée, les commandes peuvent sembler être désordonnées dans l’historique.</span><span class="sxs-lookup"><span data-stu-id="b6c87-162">If commands take some time to be completed, or if the commands are executing in a nested prompt, the commands might appear to be out of order in the history.</span></span> <span data-ttu-id="b6c87-163">Les commandes qui s’exécutent dans une invite imbriquée sont exécutées uniquement lorsque vous quittez le niveau d’invite.</span><span class="sxs-lookup"><span data-stu-id="b6c87-163">Commands that are executing in a nested prompt are completed only when you exit the prompt level.</span></span>

## <a name="see-also"></a><span data-ttu-id="b6c87-164">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b6c87-164">See Also</span></span>

- [<span data-ttu-id="b6c87-165">about_Line_Editing</span><span class="sxs-lookup"><span data-stu-id="b6c87-165">about_Line_Editing</span></span>](about_Line_Editing.md)
- [<span data-ttu-id="b6c87-166">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="b6c87-166">about_Preference_Variables</span></span>](about_Preference_Variables.md)
- [<span data-ttu-id="b6c87-167">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="b6c87-167">about_Profiles</span></span>](about_Profiles.md)
- [<span data-ttu-id="b6c87-168">about_Variables</span><span class="sxs-lookup"><span data-stu-id="b6c87-168">about_Variables</span></span>](about_Variables.md)
- [<span data-ttu-id="b6c87-169">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="b6c87-169">about_PSReadLine</span></span>](../../PSReadLine/About/about_PSReadLine.md)

