---
title: Utilisation de Visual Studio Code pour le développement PowerShell
description: Utilisation de Visual Studio Code pour le développement PowerShell
ms.date: 11/07/2019
ms.openlocfilehash: 8a4ceb3da669716915449af2d211aaf2ae61bb4f
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94390308"
---
# <a name="using-visual-studio-code-for-powershell-development"></a><span data-ttu-id="9ef5c-103">Utilisation de Visual Studio Code pour le développement PowerShell</span><span class="sxs-lookup"><span data-stu-id="9ef5c-103">Using Visual Studio Code for PowerShell Development</span></span>

<span data-ttu-id="9ef5c-104">[Visual Studio Code][vscode] est un éditeur de scripts multiplateforme de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-104">[Visual Studio Code][vscode] is a cross-platform script editor by Microsoft.</span></span> <span data-ttu-id="9ef5c-105">Avec [l’extension PowerShell][psext], il fournit une expérience d’édition de script riche et interactive, ce qui facilite l’écriture de scripts PowerShell fiables.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-105">Together with the [PowerShell extension][psext], it provides a rich and interactive script editing experience, making it easier to write reliable PowerShell scripts.</span></span> <span data-ttu-id="9ef5c-106">Visual Studio Code avec l’extension PowerShell est l’éditeur recommandé pour l’écriture de scripts PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-106">Visual Studio Code with the PowerShell extension is the recommended editor for writing PowerShell scripts.</span></span>

<span data-ttu-id="9ef5c-107">Il prend en charge les versions suivantes de PowerShell :</span><span class="sxs-lookup"><span data-stu-id="9ef5c-107">It supports the following PowerShell versions:</span></span>

- <span data-ttu-id="9ef5c-108">PowerShell 7 et versions ultérieures (Windows, macOS et Linux)</span><span class="sxs-lookup"><span data-stu-id="9ef5c-108">PowerShell 7 and up (Windows, macOS, and Linux)</span></span>
- <span data-ttu-id="9ef5c-109">PowerShell Core 6 (Windows, macOS et Linux)</span><span class="sxs-lookup"><span data-stu-id="9ef5c-109">PowerShell Core 6 (Windows, macOS, and Linux)</span></span>
- <span data-ttu-id="9ef5c-110">Windows PowerShell 5.1 (Windows uniquement)</span><span class="sxs-lookup"><span data-stu-id="9ef5c-110">Windows PowerShell 5.1 (Windows-only)</span></span>

> [!NOTE]
> <span data-ttu-id="9ef5c-111">Visual Studio Code est différent de [Visual Studio][].</span><span class="sxs-lookup"><span data-stu-id="9ef5c-111">Visual Studio Code is not the same as [Visual Studio][].</span></span>

## <a name="getting-started"></a><span data-ttu-id="9ef5c-112">Prise en main</span><span class="sxs-lookup"><span data-stu-id="9ef5c-112">Getting started</span></span>

<span data-ttu-id="9ef5c-113">Avant de commencer, vérifiez que PowerShell est présent sur votre système.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-113">Before you begin, make sure PowerShell exists on your system.</span></span> <span data-ttu-id="9ef5c-114">Pour les charges de travail modernes sur Windows, macOS et Linux, voir les liens suivants :</span><span class="sxs-lookup"><span data-stu-id="9ef5c-114">For modern workloads on Windows, macOS, and Linux, see the following links:</span></span>

- <span data-ttu-id="9ef5c-115">[Installation de PowerShell sur Linux][install-pscore-linux]</span><span class="sxs-lookup"><span data-stu-id="9ef5c-115">[Installing PowerShell on Linux][install-pscore-linux]</span></span>
- <span data-ttu-id="9ef5c-116">[Installation de PowerShell sur macOS][install-pscore-macos]</span><span class="sxs-lookup"><span data-stu-id="9ef5c-116">[Installing PowerShell on macOS][install-pscore-macos]</span></span>
- <span data-ttu-id="9ef5c-117">[Installation de PowerShell sur Windows][install-pscore-windows]</span><span class="sxs-lookup"><span data-stu-id="9ef5c-117">[Installing PowerShell on Windows][install-pscore-windows]</span></span>

<span data-ttu-id="9ef5c-118">Pour les charges de travail Windows PowerShell classiques, consultez [Installation de Windows PowerShell][install-winps].</span><span class="sxs-lookup"><span data-stu-id="9ef5c-118">For traditional Windows PowerShell workloads, see [Installing Windows PowerShell][install-winps].</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9ef5c-119">L’environnement [ISE Windows PowerShell][ise] est toujours disponible pour Windows.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-119">The [Windows PowerShell ISE][ise] is still available for Windows.</span></span> <span data-ttu-id="9ef5c-120">Toutefois, il ne fait plus partie du développement de fonctionnalités actif.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-120">However, it is no longer in active feature development.</span></span> <span data-ttu-id="9ef5c-121">L’environnement ISE ne fonctionne pas avec PowerShell 6 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-121">The ISE does not work with PowerShell 6 and higher.</span></span> <span data-ttu-id="9ef5c-122">En tant que composant de Windows, il continue d’être officiellement pris en charge pour la sécurité et les correctifs de maintenance de haute priorité.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-122">As a component of Windows, it continues to be officially supported for security and high-priority servicing fixes.</span></span>
> <span data-ttu-id="9ef5c-123">Nous n’avons aucun projet de supprimer l’environnement ISE de Windows.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-123">We have no plans to remove the ISE from Windows.</span></span>

## <a name="editing-with-visual-studio-code"></a><span data-ttu-id="9ef5c-124">Édition avec Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="9ef5c-124">Editing with Visual Studio Code</span></span>

1. <span data-ttu-id="9ef5c-125">Installer Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-125">Install Visual Studio Code.</span></span> <span data-ttu-id="9ef5c-126">Pour plus d’informations, voir la vue d’ensemble [Configurer Visual Studio Code][vsc-setup].</span><span class="sxs-lookup"><span data-stu-id="9ef5c-126">For more information, see the overview [Setting up Visual Studio Code][vsc-setup].</span></span>

   <span data-ttu-id="9ef5c-127">Les instructions d’installation sont propres à chaque plateforme :</span><span class="sxs-lookup"><span data-stu-id="9ef5c-127">There are installation instructions for each platform:</span></span>

   - <span data-ttu-id="9ef5c-128">**Windows** : suivez les instructions d’installation sur la page [Exécution de Visual Studio Code sur Windows][vsc-setup-win].</span><span class="sxs-lookup"><span data-stu-id="9ef5c-128">**Windows**: follow the installation instructions on the [Running Visual Studio Code on Windows][vsc-setup-win] page.</span></span>
   - <span data-ttu-id="9ef5c-129">**macOS** : suivez les instructions d’installation sur la page [Exécution de Visual Studio Code sur macOS][vsc-setup-macOS].</span><span class="sxs-lookup"><span data-stu-id="9ef5c-129">**macOS**: follow the installation instructions on the [Running Visual Studio Code on macOS][vsc-setup-macOS] page.</span></span>
   - <span data-ttu-id="9ef5c-130">**Linux** : suivez les instructions d’installation sur la page [Exécution de Visual Studio Code sur Linux][vsc-setup-linux].</span><span class="sxs-lookup"><span data-stu-id="9ef5c-130">**Linux**: follow the installation instructions on the [Running Visual Studio Code on Linux][vsc-setup-linux] page.</span></span>

1. <span data-ttu-id="9ef5c-131">Installez l’extension PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-131">Install the PowerShell Extension.</span></span>

   1. <span data-ttu-id="9ef5c-132">Lancez l’application Visual Studio Code en tapant `code` dans une console, ou `code-insiders` si vous avez installé Visual Studio Code Insiders.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-132">Launch the Visual Studio Code app by typing `code` in a console or `code-insiders` if you installed Visual Studio Code Insiders.</span></span>
   1. <span data-ttu-id="9ef5c-133">Lancez **Quick Open** sur Windows ou Linux en appuyant sur <kbd>Ctrl</kbd>+<kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-133">Launch **Quick Open** on Windows or Linux by pressing <kbd>Ctrl</kbd>+<kbd>P</kbd>.</span></span> <span data-ttu-id="9ef5c-134">Sur macOS, appuyez sur <kbd>Cmd</kbd>+<kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-134">On macOS, press <kbd>Cmd</kbd>+<kbd>P</kbd>.</span></span>
   1. <span data-ttu-id="9ef5c-135">Dans Quick Open, tapez `ext install powershell`, puis appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-135">In Quick Open, type `ext install powershell` and press **Enter**.</span></span>
   1. <span data-ttu-id="9ef5c-136">La vue **Extensions** s’ouvre dans la barre latérale.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-136">The **Extensions** view opens on the Side Bar.</span></span> <span data-ttu-id="9ef5c-137">Sélectionnez l’extension de PowerShell de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-137">Select the PowerShell extension from Microsoft.</span></span>
      <span data-ttu-id="9ef5c-138">Un écran Visual Studio Code semblable à l’image suivante apparaît :</span><span class="sxs-lookup"><span data-stu-id="9ef5c-138">You should see a Visual Studio Code screen similar to the following image:</span></span>

      ![Visual Studio Code - vue de l’extension PowerShell](media/using-vscode/vscode.png)

   1. <span data-ttu-id="9ef5c-140">Cliquez sur le bouton **Installer** sur l’extension PowerShell de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-140">Click the **Install** button on the PowerShell extension from Microsoft.</span></span>
   1. <span data-ttu-id="9ef5c-141">Après l’installation, si vous voyez le bouton **Installer** se changer en **Recharger**, cliquez sur **Recharger**.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-141">After the install, if you see the **Install** button turn into **Reload**, Click on **Reload**.</span></span>
   1. <span data-ttu-id="9ef5c-142">Une fois Visual Studio Code rechargé, vous pouvez passer à l’édition.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-142">After Visual Studio Code has reloaded, you're ready for editing.</span></span>

<span data-ttu-id="9ef5c-143">Par exemple, pour créer un fichier, cliquez sur **Fichier > Nouveau**.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-143">For example, to create a new file, click **File > New**.</span></span> <span data-ttu-id="9ef5c-144">Pour l’enregistrer, cliquez sur **Fichier > Enregistrer**, puis indiquez un nom de fichier, comme `HelloWorld.ps1`.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-144">To save it, click **File > Save** and then provide a file name, such as `HelloWorld.ps1`.</span></span> <span data-ttu-id="9ef5c-145">Pour fermer le fichier, cliquez sur `X` à côté du nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-145">To close the file, click the `X` next to the file name.</span></span> <span data-ttu-id="9ef5c-146">Pour quitter Visual Studio Code, cliquez sur **Fichier > Quitter**.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-146">To exit Visual Studio Code, **File > Exit**.</span></span>

### <a name="installing-the-powershell-extension-on-restricted-systems"></a><span data-ttu-id="9ef5c-147">Installation de l’extension PowerShell sur des systèmes restreints</span><span class="sxs-lookup"><span data-stu-id="9ef5c-147">Installing the PowerShell Extension on Restricted Systems</span></span>

<span data-ttu-id="9ef5c-148">Certains systèmes sont configurés pour exiger la validation de toutes les signatures de code.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-148">Some systems are set up to require validation of all code signatures.</span></span> <span data-ttu-id="9ef5c-149">Vous risquez de recevoir l’erreur suivante :</span><span class="sxs-lookup"><span data-stu-id="9ef5c-149">You may receive the following error:</span></span>

```
Language server startup failed.
```

<span data-ttu-id="9ef5c-150">Ce problème peut se produire lorsque la stratégie d’exécution de PowerShell est définie par la stratégie de groupe Windows.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-150">This problem can occur when PowerShell's execution policy is set by Windows Group Policy.</span></span> <span data-ttu-id="9ef5c-151">Pour approuver manuellement PowerShell Editor Services et l’extension PowerShell pour Visual Studio Code, ouvrez une invite PowerShell et exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="9ef5c-151">To manually approve PowerShell Editor Services and the PowerShell extension for Visual Studio Code, open a PowerShell prompt and run the following command:</span></span>

```powershell
Import-Module $HOME\.vscode\extensions\ms-vscode.powershell*\modules\PowerShellEditorServices\PowerShellEditorServices.psd1
```

<span data-ttu-id="9ef5c-152">Le message **Voulez-vous exécuter le logiciel provenant de cet éditeur non approuvé ?** apparaît.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-152">You're prompted with **Do you want to run software from this untrusted publisher?**</span></span> <span data-ttu-id="9ef5c-153">Tapez `A` pour exécuter le fichier.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-153">Type `A` to run the file.</span></span> <span data-ttu-id="9ef5c-154">Ouvrez ensuite Visual Studio Code et vérifiez que l’extension PowerShell fonctionne correctement.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-154">Then, open Visual Studio Code and check that the PowerShell extension is functioning properly.</span></span> <span data-ttu-id="9ef5c-155">Si vous rencontrez toujours des problèmes de mise en route, faites-le-nous savoir sur [Problèmes GitHub][].</span><span class="sxs-lookup"><span data-stu-id="9ef5c-155">If you still have problems getting started, let us know on [GitHub issues][].</span></span>

> [!NOTE]
> <span data-ttu-id="9ef5c-156">L’extension PowerShell pour Visual Studio Code ne prend pas en charge l’exécution en mode de langage avec contrainte.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-156">The PowerShell extension for Visual Studio Code does not support running in constrained language mode.</span></span> <span data-ttu-id="9ef5c-157">Pour plus d’informations, consultez le [problème GitHub n° 606][i606].</span><span class="sxs-lookup"><span data-stu-id="9ef5c-157">For more information, see [GitHub issue #606][i606].</span></span>

### <a name="choosing-a-version-of-powershell-to-use-with-the-extension"></a><span data-ttu-id="9ef5c-158">Choisir la version de PowerShell à utiliser avec l’extension</span><span class="sxs-lookup"><span data-stu-id="9ef5c-158">Choosing a version of PowerShell to use with the extension</span></span>

<span data-ttu-id="9ef5c-159">Maintenant que PowerShell Core peut s’installer côte à côte avec Windows PowerShell, il est possible d’utiliser une version spécifique de PowerShell avec l’extension PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-159">With PowerShell Core installing side-by-side with Windows PowerShell, it's now possible to use a specific version of PowerShell with the PowerShell extension.</span></span> <span data-ttu-id="9ef5c-160">Cette fonctionnalité examine quelques chemins connus sur différents systèmes d’exploitation pour détecter les installations de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-160">This feature looks at a few well-known paths on different operating systems to discover installations of PowerShell.</span></span>

<span data-ttu-id="9ef5c-161">Suivez les étapes ci-dessous pour choisir la version :</span><span class="sxs-lookup"><span data-stu-id="9ef5c-161">Use the following steps to choose the version:</span></span>

1. <span data-ttu-id="9ef5c-162">Ouvrez la **Palette de commandes** sous Windows ou Linux avec <kbd>Ctrl</kbd>+<kbd>Maj</kbd>+<kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-162">Open the **Command Palette** on Windows or Linux with <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>.</span></span> <span data-ttu-id="9ef5c-163">Sur macOS, utilisez <kbd>Cmd</kbd>+<kbd>Maj</kbd>+<kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-163">On macOS, use <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>.</span></span>
1. <span data-ttu-id="9ef5c-164">Recherchez **Session**.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-164">Search for **Session**.</span></span>
1. <span data-ttu-id="9ef5c-165">Cliquez sur **PowerShell : Afficher le menu de session**.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-165">Click on **PowerShell: Show Session Menu**.</span></span>
1. <span data-ttu-id="9ef5c-166">Choisissez la version de PowerShell que vous souhaitez utiliser dans la liste, par exemple : **PowerShell Core**.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-166">Choose the version of PowerShell you want to use from the list, for example: **PowerShell Core**.</span></span>

<span data-ttu-id="9ef5c-167">Si vous avez installé PowerShell à un emplacement non standard, il risque de ne pas apparaître d’emblée dans le menu de session.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-167">If you installed PowerShell to a non-typical location, it might not show up initially in the Session Menu.</span></span> <span data-ttu-id="9ef5c-168">Pour étendre le menu de session, [ajoutez vos propres chemins personnalisés](#adding-your-own-powershell-paths-to-the-session-menu) en suivant la procédure décrite ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-168">You can extend the session menu by [adding your own custom paths](#adding-your-own-powershell-paths-to-the-session-menu) as described below.</span></span>

> [!NOTE]
> <span data-ttu-id="9ef5c-169">Le menu de session PowerShell est également accessible à partir du numéro de version vert dans le coin inférieur droit de la barre d’état.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-169">The PowerShell session menu can also be accessed from the green version number in the bottom right corner of status bar.</span></span> <span data-ttu-id="9ef5c-170">Cliquez dessus pour accéder au menu de session.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-170">Clicking this version number opens the session menu.</span></span>

## <a name="configuration-settings-for-visual-studio-code"></a><span data-ttu-id="9ef5c-171">Paramètres de configuration de Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="9ef5c-171">Configuration settings for Visual Studio Code</span></span>

<span data-ttu-id="9ef5c-172">Tout d’abord, si vous n’êtes pas familiarisé avec la modification des paramètres dans Visual Studio Code, nous vous recommandons de lire la [documentation des paramètres de Visual Studio Code][vsc-settings].</span><span class="sxs-lookup"><span data-stu-id="9ef5c-172">First, if you're not familiar with how to change settings in Visual Studio Code, we recommend reading [Visual Studio Code's settings][vsc-settings] documentation.</span></span>

<span data-ttu-id="9ef5c-173">Après avoir lu la documentation, vous pouvez ajouter des paramètres de configuration dans `settings.json`.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-173">After reading the documentation, you can add configuration settings in `settings.json`.</span></span>

```json
{
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "files.trimTrailingWhitespace": true,
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

<span data-ttu-id="9ef5c-174">Si vous ne souhaitez pas que ces paramètres affectent tous les types de fichiers, Visual Studio Code permet également des configurations par langage.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-174">If you don't want these settings to affect all files types, Visual Studio Code also allows per-language configurations.</span></span> <span data-ttu-id="9ef5c-175">Vous pouvez créer un paramètre propre au langage en plaçant des paramètres dans un champ `[<language-name>]`.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-175">Create a language-specific setting by putting settings in a `[<language-name>]` field.</span></span> <span data-ttu-id="9ef5c-176">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="9ef5c-176">For example:</span></span>

```json
{
    "[powershell]": {
        "files.encoding": "utf8bom",
        "files.autoGuessEncoding": true
    }
}
```

> [!TIP]
> <span data-ttu-id="9ef5c-177">Pour plus d’informations sur l’encodage de fichier dans Visual Studio Code, consultez [Présentation de l’encodage de fichier][file-encoding].</span><span class="sxs-lookup"><span data-stu-id="9ef5c-177">For more information about file encoding in Visual Studio Code, see [Understanding file encoding][file-encoding].</span></span>
>
> <span data-ttu-id="9ef5c-178">Consultez également [Comment répliquer l’expérience ISE dans Visual Studio Code][vsc-ise] pour obtenir d’autres conseils de configuration de Visual Studio Code pour l’édition avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-178">Also, check out [How to replicate the ISE experience in Visual Studio Code][vsc-ise] for other tips on how to configure Visual Studio Code for PowerShell editing.</span></span>

### <a name="adding-your-own-powershell-paths-to-the-session-menu"></a><span data-ttu-id="9ef5c-179">Ajouter ses propres chemins PowerShell au menu de session</span><span class="sxs-lookup"><span data-stu-id="9ef5c-179">Adding your own PowerShell paths to the session menu</span></span>

<span data-ttu-id="9ef5c-180">Il est possible d’ajouter d’autres chemins d’exécutables PowerShell au menu de session via le [paramètre Visual Studio Code](https://code.visualstudio.com/docs/getstarted/settings) : `powershell.powerShellAdditionalExePaths`.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-180">You can add other PowerShell executable paths to the session menu through the [Visual Studio Code setting](https://code.visualstudio.com/docs/getstarted/settings): `powershell.powerShellAdditionalExePaths`.</span></span>

<span data-ttu-id="9ef5c-181">Ajoutez un élément à la liste `powershell.powerShellAdditionalExePaths` ou créez la liste si elle n’existe pas dans `settings.json` :</span><span class="sxs-lookup"><span data-stu-id="9ef5c-181">Add an item to the list `powershell.powerShellAdditionalExePaths` or create the list if it doesn't exist in your `settings.json`:</span></span>

```json
{
    // other settings...

    "powershell.powerShellAdditionalExePaths": [
        {
            "exePath": "C:\\Users\\tyler\\Downloads\\PowerShell\\pwsh.exe",
            "versionName": "Downloaded PowerShell"
        }
    ],

    // other settings...
}
```

<span data-ttu-id="9ef5c-182">Chaque élément doit comporter :</span><span class="sxs-lookup"><span data-stu-id="9ef5c-182">Each item must have:</span></span>

- <span data-ttu-id="9ef5c-183">`exePath`: chemin de l’exécutable `pwsh` ou `powershell`.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-183">`exePath`: The path to the `pwsh` or `powershell` executable.</span></span>
- <span data-ttu-id="9ef5c-184">`versionName`: texte qui s’affichera dans le menu de session.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-184">`versionName`: The text that will show up in the session menu.</span></span>

<span data-ttu-id="9ef5c-185">Pour définir la version PowerShell par défaut, définissez la valeur `powershell.powerShellDefaultVersion` sur le texte affiché dans le menu de session (également connu sous le nom de `versionName`) :</span><span class="sxs-lookup"><span data-stu-id="9ef5c-185">To set the default PowerShell version, set the value `powershell.powerShellDefaultVersion` to the text displayed in the session menu (also known as the `versionName`):</span></span>

```json
{
    // other settings...

    "powershell.powerShellAdditionalExePaths": [
        {
            "exePath": "C:\\Users\\tyler\\Downloads\\PowerShell\\pwsh.exe",
            "versionName": "Downloaded PowerShell"
        }
    ],

    "powershell.powerShellDefaultVersion": "Downloaded PowerShell",

    // other settings...
}
```

<span data-ttu-id="9ef5c-186">Après avoir configuré ce paramètre, redémarrez Visual Studio Code ou rechargez la fenêtre Visual Studio Code active avec la **Palette de commandes**, puis tapez **Développeur : Recharger la fenêtre**.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-186">After you've configured this setting, restart Visual Studio Code or to reload the current Visual Studio Code window from the **Command Palette**, type **Developer: Reload Window**.</span></span>

<span data-ttu-id="9ef5c-187">Si vous ouvrez le menu de session, vous trouvez à présent les versions supplémentaires de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-187">If you open the session menu, you now see your additional PowerShell versions!</span></span>

> [!NOTE]
> <span data-ttu-id="9ef5c-188">Si vous générez PowerShell à partir de la source, c’est un excellent moyen de tester votre build locale de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-188">If you build PowerShell from source, this is a great way to test out your local build of PowerShell.</span></span>

### <a name="using-an-older-version-of-the-powershell-extension-for-windows-powershell-v3-and-v4"></a><span data-ttu-id="9ef5c-189">Utilisation d’une version antérieure de l’extension PowerShell pour Windows PowerShell v3 et v4</span><span class="sxs-lookup"><span data-stu-id="9ef5c-189">Using an older version of the PowerShell Extension for Windows PowerShell v3 and v4</span></span>

<span data-ttu-id="9ef5c-190">L’extension PowerShell actuelle ne prend pas en charge [PowerShell v3 et v4][i1310].</span><span class="sxs-lookup"><span data-stu-id="9ef5c-190">The current PowerShell extension doesn't support [PowerShell v3 and v4][i1310].</span></span> <span data-ttu-id="9ef5c-191">Toutefois, vous pouvez utiliser la dernière version de l’extension qui prend en charge PowerShell v3 et v4.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-191">However, you can use the last version of the extension that supports PowerShell v3 and v4.</span></span>

> [!CAUTION]
> <span data-ttu-id="9ef5c-192">Il n’y aura aucun correctif supplémentaire pour cette version antérieure de l’extension.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-192">There will be no additional fixes to this older version of the extension.</span></span> <span data-ttu-id="9ef5c-193">Bien que fournie « TELLE QUELLE », elle est à votre disposition si vous utilisez encore Windows PowerShell v3 et Windows PowerShell v4.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-193">It's provided "AS IS" but is available for you if you are still using Windows PowerShell v3 and Windows PowerShell v4.</span></span>

<span data-ttu-id="9ef5c-194">Tout d’abord, ouvrez le volet Extension et recherchez `PowerShell`.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-194">First, open the Extension pane and search for `PowerShell`.</span></span> <span data-ttu-id="9ef5c-195">Cliquez ensuite sur l’engrenage, puis sélectionnez **Installer une autre version...** .</span><span class="sxs-lookup"><span data-stu-id="9ef5c-195">Then click the gear and select **Install another version...**.</span></span>

![Élément de menu - Installer une autre version...](media/using-vscode/install-another-version.png)

<span data-ttu-id="9ef5c-197">Sélectionnez ensuite la version **2020.1.0**.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-197">Then select the **2020.1.0** version.</span></span> <span data-ttu-id="9ef5c-198">Cette version de l’extension était la dernière version à prendre en charge v3 et v4.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-198">This version of the extension was the last version to support v3 and v4.</span></span> <span data-ttu-id="9ef5c-199">Veillez à ajouter le paramètre suivant afin que la version de votre extension ne soit pas mise à jour automatiquement :</span><span class="sxs-lookup"><span data-stu-id="9ef5c-199">Be sure to add the following setting so that your extension version doesn't update automatically:</span></span>

```json
{
    "extensions.autoUpdate": false
}
```

<span data-ttu-id="9ef5c-200">La version **2020.1.0** fonctionnera très bientôt.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-200">Version **2020.1.0** will work for the foreseeable future.</span></span> <span data-ttu-id="9ef5c-201">Toutefois, Visual Studio Code pourrait implémenter une modification qui arrêterait cette version de l’extension.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-201">However, Visual Studio Code could implement a change that breaks this version of the extension.</span></span> <span data-ttu-id="9ef5c-202">Pour cette raison et à cause de l’absence de support, nous vous recommandons de procéder comme suit :</span><span class="sxs-lookup"><span data-stu-id="9ef5c-202">Because of this, and lack of support, we recommend:</span></span>

- <span data-ttu-id="9ef5c-203">Mise à niveau vers Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="9ef5c-203">Upgrading to Windows PowerShell 5.1</span></span>
- <span data-ttu-id="9ef5c-204">Installer PowerShell 7, une installation côte à côte avec Windows PowerShell qui fonctionne de manière optimale avec l’extension PowerShell</span><span class="sxs-lookup"><span data-stu-id="9ef5c-204">Install PowerShell 7, which is a side-by-side install to Windows PowerShell and works the best with the PowerShell extension</span></span>

## <a name="debugging-with-visual-studio-code"></a><span data-ttu-id="9ef5c-205">Débogage avec Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="9ef5c-205">Debugging with Visual Studio Code</span></span>

### <a name="no-workspace-debugging"></a><span data-ttu-id="9ef5c-206">Débogage sans espace de travail</span><span class="sxs-lookup"><span data-stu-id="9ef5c-206">No-workspace debugging</span></span>

<span data-ttu-id="9ef5c-207">Dans Visual Studio Code version 1.9 (ou ultérieure), il est possible de déboguer des scripts PowerShell sans ouvrir le dossier qui les contient.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-207">In Visual Studio Code version 1.9 (or higher), you can debug PowerShell scripts without opening the folder that contains the PowerShell script.</span></span>

1. <span data-ttu-id="9ef5c-208">Ouvrir le fichier de script PowerShell avec **Fichier > Ouvrir le fichier...**</span><span class="sxs-lookup"><span data-stu-id="9ef5c-208">Open the PowerShell script file with **File > Open File...**</span></span>
1. <span data-ttu-id="9ef5c-209">Définissez un point d’arrêt : sélectionnez une ligne, puis appuyez sur <kbd>F9</kbd></span><span class="sxs-lookup"><span data-stu-id="9ef5c-209">Set a breakpoint - select a line then press <kbd>F9</kbd></span></span>
1. <span data-ttu-id="9ef5c-210">Appuyez sur <kbd>F5</kbd> pour démarrer le débogage</span><span class="sxs-lookup"><span data-stu-id="9ef5c-210">Press <kbd>F5</kbd> to start debugging</span></span>

<span data-ttu-id="9ef5c-211">Le volet Actions de débogage apparaît ; il permet de s’arrêter dans le débogueur, d’effectuer un pas à pas détaillé, de reprendre et d’arrêter le débogage.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-211">You should see the Debug actions pane appear which allows you to break into the debugger, step, resume, and stop debugging.</span></span>

### <a name="workspace-debugging"></a><span data-ttu-id="9ef5c-212">Débogage d’espace de travail</span><span class="sxs-lookup"><span data-stu-id="9ef5c-212">Workspace debugging</span></span>

<span data-ttu-id="9ef5c-213">Le débogage d’espace de travail fait référence au débogage dans le contexte d’un dossier ouvert dans le menu **Fichier**  avec **Ouvrir le dossier…** . Le dossier que vous ouvrez est généralement votre dossier de projet PowerShell ou la racine de votre dépôt Git.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-213">Workspace debugging refers to debugging in the context of a folder that you've opened from the **File** menu using **Open Folder...**. The folder you open is typically your PowerShell project folder or the root of your Git repository.</span></span> <span data-ttu-id="9ef5c-214">Le débogage d’espace de travail vous permet de définir plusieurs configurations de débogage autres que simplement déboguer le fichier actuellement ouvert.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-214">Workspace debugging allows you to define multiple debug configurations other than just debugging the currently open file.</span></span>

<span data-ttu-id="9ef5c-215">Suivez ces étapes pour créer un fichier de configuration de débogage :</span><span class="sxs-lookup"><span data-stu-id="9ef5c-215">Follow these steps to create a debug configuration file:</span></span>

1. <span data-ttu-id="9ef5c-216">Ouvrez la vue **Déboguer** sur Windows ou Linux en appuyant sur <kbd>Ctrl</kbd>+<kbd>Maj</kbd>+<kbd>D</kbd>.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-216">Open the **Debug** view on Windows or Linux by pressing <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>.</span></span> <span data-ttu-id="9ef5c-217">Sur macOS, appuyez sur <kbd>Cmd</kbd>+<kbd>Maj</kbd>+<kbd>D</kbd>.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-217">On macOS, press <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>.</span></span>
1. <span data-ttu-id="9ef5c-218">Cliquez sur le lien **Créer un fichier launch.json**.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-218">Click the **create a launch.json file** link.</span></span>
1. <span data-ttu-id="9ef5c-219">À partir de l’invite **Sélectionner l’environnement**, choisissez **PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-219">From the **Select Environment** prompt, choose **PowerShell**.</span></span>
1. <span data-ttu-id="9ef5c-220">Choisissez le type de débogage que vous souhaitez utiliser :</span><span class="sxs-lookup"><span data-stu-id="9ef5c-220">Choose the type of debugging you'd like to use:</span></span>

   - <span data-ttu-id="9ef5c-221">**Lancer le fichier actuel** : lancer et déboguer le fichier dans la fenêtre de l’éditeur actuellement active</span><span class="sxs-lookup"><span data-stu-id="9ef5c-221">**Launch Current File** - Launch and debug the file in the currently active editor window</span></span>
   - <span data-ttu-id="9ef5c-222">**Lancer le script** : lancer et déboguer le fichier ou la commande spécifiés</span><span class="sxs-lookup"><span data-stu-id="9ef5c-222">**Launch Script** - Launch and debug the specified file or command</span></span>
   - <span data-ttu-id="9ef5c-223">**Session interactive** : déboguer les commandes exécutées à partir de la console intégrée</span><span class="sxs-lookup"><span data-stu-id="9ef5c-223">**Interactive Session** - Debug commands executed from the Integrated Console</span></span>
   - <span data-ttu-id="9ef5c-224">**Attacher** : attacher le débogueur à un processus hôte PowerShell en cours d’exécution</span><span class="sxs-lookup"><span data-stu-id="9ef5c-224">**Attach** - Attach the debugger to a running PowerShell Host Process</span></span>

<span data-ttu-id="9ef5c-225">Visual Studio Code crée un répertoire et un fichier `.vscode\launch.json` à la racine du dossier de votre espace de travail pour stocker la configuration de débogage.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-225">Visual Studio Code creates a directory and a file `.vscode\launch.json` in the root of your workspace folder to store the debug configuration.</span></span> <span data-ttu-id="9ef5c-226">Si vos fichiers se trouvent dans un référentiel Git, il est généralement préférable de valider le fichier `launch.json`.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-226">If your files are in a Git repository, you typically want to commit the `launch.json` file.</span></span> <span data-ttu-id="9ef5c-227">Le fichier `launch.json` présente le contenu suivant :</span><span class="sxs-lookup"><span data-stu-id="9ef5c-227">The contents of the `launch.json` file are:</span></span>

```json
{
  "version": "0.2.0",
  "configurations": [
      {
          "type": "PowerShell",
          "request": "launch",
          "name": "PowerShell Launch (current file)",
          "script": "${file}",
          "args": [],
          "cwd": "${file}"
      },
      {
          "type": "PowerShell",
          "request": "attach",
          "name": "PowerShell Attach to Host Process",
          "processId": "${command.PickPSHostProcess}",
          "runspaceId": 1
      },
      {
          "type": "PowerShell",
          "request": "launch",
          "name": "PowerShell Interactive Session",
          "cwd": "${workspaceRoot}"
      }
  ]
}
```

<span data-ttu-id="9ef5c-228">Ce fichier représente les scénarios de débogage courants.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-228">This file represents the common debug scenarios.</span></span> <span data-ttu-id="9ef5c-229">Quand vous ouvrez ce fichier dans l’éditeur, un bouton **Ajouter une configuration…** apparaît.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-229">When you open this file in the editor, you see an **Add Configuration...** button.</span></span> <span data-ttu-id="9ef5c-230">Vous pouvez cliquer sur ce bouton pour ajouter d’autres configurations de débogage PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-230">You can click this button to add more PowerShell debug configurations.</span></span> <span data-ttu-id="9ef5c-231">Il est utile d’ajouter la configuration **PowerShell : Lancer un script**.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-231">One useful configuration to add is **PowerShell: Launch Script**.</span></span> <span data-ttu-id="9ef5c-232">Avec cette configuration, vous pouvez spécifier un fichier avec des arguments facultatifs qui sont utilisés quand vous appuyez sur <kbd>F5</kbd>, quel que soit le fichier actif dans l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-232">With this configuration, you can specify a file containing optional arguments that are used whenever you press <kbd>F5</kbd> no matter which file is active in the editor.</span></span>

<span data-ttu-id="9ef5c-233">Une fois la configuration de débogage établie, vous pouvez sélectionner la configuration que vous souhaitez utiliser lors d’une session de débogage.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-233">After the debug configuration is established, you can select which configuration you want to use during a debug session.</span></span> <span data-ttu-id="9ef5c-234">Sélectionnez une configuration dans la liste déroulante de la configuration de débogage, dans la barre d’outils de la vue **Déboguer**.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-234">Select a configuration from the debug configuration drop-down in the **Debug** view's toolbar.</span></span>

## <a name="troubleshooting-the-powershell-extension-for-visual-studio-code"></a><span data-ttu-id="9ef5c-235">Résolution des problèmes de l’extension PowerShell pour Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="9ef5c-235">Troubleshooting the PowerShell extension for Visual Studio Code</span></span>

<span data-ttu-id="9ef5c-236">Si vous rencontrez des problèmes lors de l’utilisation de Visual Studio Code pour le développement de scripts PowerShell, consultez le [guide de résolution des problèmes][troubleshooting] sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-236">If you experience any issues using Visual Studio Code for PowerShell script development, see the [troubleshooting guide][troubleshooting] on GitHub.</span></span>

## <a name="useful-resources"></a><span data-ttu-id="9ef5c-237">Ressources utiles</span><span class="sxs-lookup"><span data-stu-id="9ef5c-237">Useful resources</span></span>

<span data-ttu-id="9ef5c-238">Quelques vidéos et billets de blogs peuvent être utiles pour bien démarrer avec l’extension PowerShell pour Visual Studio Code :</span><span class="sxs-lookup"><span data-stu-id="9ef5c-238">There are a few videos and blog posts that may be helpful to get you started using the PowerShell extension for Visual Studio Code:</span></span>

### <a name="videos"></a><span data-ttu-id="9ef5c-239">Videos</span><span class="sxs-lookup"><span data-stu-id="9ef5c-239">Videos</span></span>

- [<span data-ttu-id="9ef5c-240">Utilisation de Visual Studio Code comme éditeur PowerShell par défaut</span><span class="sxs-lookup"><span data-stu-id="9ef5c-240">Using Visual Studio Code as Your Default PowerShell Editor</span></span>](https://youtu.be/bGn45vIeAMM)
- [<span data-ttu-id="9ef5c-241">Visual Studio Code : exploration du débogage de vos scripts PowerShell</span><span class="sxs-lookup"><span data-stu-id="9ef5c-241">Visual Studio Code: deep dive into debugging your PowerShell scripts</span></span>](https://youtu.be/cSbIXmlkr8o)

### <a name="blog-posts"></a><span data-ttu-id="9ef5c-242">Billets de blog :</span><span class="sxs-lookup"><span data-stu-id="9ef5c-242">Blog posts</span></span>

- <span data-ttu-id="9ef5c-243">[Extension PowerShell][pscdn]</span><span class="sxs-lookup"><span data-stu-id="9ef5c-243">[PowerShell Extension][pscdn]</span></span>
- <span data-ttu-id="9ef5c-244">[Écrire et déboguer des scripts PowerShell dans Visual Studio Code][debug]</span><span class="sxs-lookup"><span data-stu-id="9ef5c-244">[Write and debug PowerShell scripts in Visual Studio Code][debug]</span></span>
- <span data-ttu-id="9ef5c-245">[Aide sur le débogage avec Visual Studio Code][psdbgblog]</span><span class="sxs-lookup"><span data-stu-id="9ef5c-245">[Debugging Visual Studio Code Guidance][psdbgblog]</span></span>
- <span data-ttu-id="9ef5c-246">[Débogage de PowerShell dans Visual Studio Code][psdbg-gh]</span><span class="sxs-lookup"><span data-stu-id="9ef5c-246">[Debugging PowerShell in Visual Studio Code][psdbg-gh]</span></span>
- <span data-ttu-id="9ef5c-247">[Guide pratique pour le développement avec PowerShell dans Visual Studio Code][getting-started]</span><span class="sxs-lookup"><span data-stu-id="9ef5c-247">[Get started with PowerShell development in Visual Studio Code][getting-started]</span></span>
- <span data-ttu-id="9ef5c-248">[Fonctionnalités d’édition de Visual Studio Code pour le développement avec PowerShell – Partie 1][editing-part1]</span><span class="sxs-lookup"><span data-stu-id="9ef5c-248">[Visual Studio Code editing features for PowerShell development – Part 1][editing-part1]</span></span>
- <span data-ttu-id="9ef5c-249">[Fonctionnalités d’édition de Visual Studio Code pour le développement avec PowerShell – Partie 2][editing-part2]</span><span class="sxs-lookup"><span data-stu-id="9ef5c-249">[Visual Studio Code editing features for PowerShell development – Part 2][editing-part2]</span></span>
- <span data-ttu-id="9ef5c-250">[Débogage des scripts PowerShell dans Visual Studio Code – Partie 1][debugging-part1]</span><span class="sxs-lookup"><span data-stu-id="9ef5c-250">[Debugging PowerShell script in Visual Studio Code – Part 1][debugging-part1]</span></span>
- <span data-ttu-id="9ef5c-251">[Débogage des scripts PowerShell dans Visual Studio Code – Partie 2][debugging-part2]</span><span class="sxs-lookup"><span data-stu-id="9ef5c-251">[Debugging PowerShell script in Visual Studio Code – Part 2][debugging-part2]</span></span>

## <a name="powershell-extension-project-source-code"></a><span data-ttu-id="9ef5c-252">Code source du projet d’extension PowerShell</span><span class="sxs-lookup"><span data-stu-id="9ef5c-252">PowerShell extension project source code</span></span>

<span data-ttu-id="9ef5c-253">Vous trouverez le code source de l’extension PowerShell sur [GitHub][psext-src].</span><span class="sxs-lookup"><span data-stu-id="9ef5c-253">The PowerShell extension's source code can be found on [GitHub][psext-src].</span></span>

<span data-ttu-id="9ef5c-254">Si vous êtes intéressé à contribuer, les demandes de tirage (Pull requests) sont très appréciées.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-254">If you're interested in contributing, Pull Requests are greatly appreciated.</span></span> <span data-ttu-id="9ef5c-255">Pour commencer, suivez les [instructions de la documentation du développeur][dev-docs] sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-255">Follow along with the [developer documentation][dev-docs] on GitHub to get started.</span></span>

<!-- related articles -->
[ise]:                    ../../windows-powershell/ise/Introducing-the-Windows-PowerShell-ISE.md
[install-pscore-linux]:   ../../install/Installing-PowerShell-Core-on-Linux.md
[install-pscore-macos]:   ../../install/Installing-PowerShell-Core-on-macOS.md
[install-pscore-windows]: ../../install/Installing-PowerShell-Core-on-Windows.md
[install-winps]:          ../../install/Installing-Windows-PowerShell.md
[file-encoding]:          understanding-file-encoding.md
[vsc-ise]:                How-To-Replicate-the-ISE-Experience-In-VSCode.md

<!-- blogs -->
[debug]:                  https://devblogs.microsoft.com/powershell/announcing-powershell-language-support-for-visual-studio-code-and-more/
[debugging-part1]:        https://devblogs.microsoft.com/scripting/debugging-powershell-script-in-visual-studio-code-part-1/
[debugging-part2]:        https://devblogs.microsoft.com/scripting/debugging-powershell-script-in-visual-studio-code-part-2/
[editing-part1]:          https://devblogs.microsoft.com/scripting/visual-studio-code-editing-features-for-powershell-development-part-1/
[editing-part2]:          https://devblogs.microsoft.com/scripting/visual-studio-code-editing-features-for-powershell-development-part-2/
[getting-started]:        https://devblogs.microsoft.com/scripting/get-started-with-powershell-development-in-visual-studio-code/
[psdbgblog]:              https://johnpapa.net/debugging-with-visual-studio-code/
[psdbg-gh]:               https://github.com/PowerShell/vscode-powershell/tree/master/examples
[pscdn]:                  https://docs.microsoft.com/archive/blogs/cdndevs/visual-studio-code-powershell-extension

<!-- issues -->
[Problèmes GitHub]:          https://github.com/PowerShell/vscode-powershell/issues
[GitHub issues]:          https://github.com/PowerShell/vscode-powershell/issues
[i1310]:                  https://github.com/PowerShell/vscode-powershell/issues/1310
[i606]:                   https://github.com/PowerShell/vscode-powershell/issues/606

<!-- product links -->
[Visual Studio]:          https://visualstudio.microsoft.com/
[Visual Studio]:          https://visualstudio.microsoft.com/
[vscode]:                 https://code.visualstudio.com/
[psext]:                  https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell
[vsc-settings]:           https://code.visualstudio.com/docs/getstarted/settings
[vsc-setup]:              https://code.visualstudio.com/Docs/setup/setup-overview
[vsc-setup-win]:          https://code.visualstudio.com/docs/setup/windows
[vsc-setup-macos]:        https://code.visualstudio.com/docs/setup/mac
[vsc-setup-linux]:        https://code.visualstudio.com/docs/setup/linux
[psext-src]:              https://github.com/PowerShell/vscode-powershell
[troubleshooting]:        https://github.com/PowerShell/vscode-powershell/blob/master/docs/troubleshooting.md
[dev-docs]:               https://github.com/PowerShell/vscode-powershell/blob/master/docs/development.md
