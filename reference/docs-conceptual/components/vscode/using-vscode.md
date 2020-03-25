---
title: Utilisation de Visual Studio Code pour le développement PowerShell
description: Utilisation de Visual Studio Code pour le développement PowerShell
ms.date: 11/07/2019
ms.openlocfilehash: 86739970b58460bef9686a75bf0604d0605d4888
ms.sourcegitcommit: d36db3a1bc44aee6bc97422b557041c3aece4c67
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80082432"
---
# <a name="using-visual-studio-code-for-powershell-development"></a><span data-ttu-id="4a7cf-103">Utilisation de Visual Studio Code pour le développement PowerShell</span><span class="sxs-lookup"><span data-stu-id="4a7cf-103">Using Visual Studio Code for PowerShell Development</span></span>

<span data-ttu-id="4a7cf-104">[Visual Studio Code](https://code.visualstudio.com/) est un éditeur de scripts multiplateforme (Windows, macOS et Linux) de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-104">[Visual Studio Code](https://code.visualstudio.com/) is a cross-platform (Windows, macOS, and Linux) script editor by Microsoft.</span></span> <span data-ttu-id="4a7cf-105">Avec l'[extension PowerShell](https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell), il fournit une expérience d’édition de script riche et interactive, ce qui facilite l’écriture de scripts PowerShell fiables.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-105">Together with the [the PowerShell extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell), it provides a rich and interactive script editing experience, making it easier to write reliable PowerShell scripts.</span></span>

<span data-ttu-id="4a7cf-106">Visual Studio Code avec l’extension PowerShell est l’éditeur recommandé pour l’écriture de scripts PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-106">Visual Studio Code with the PowerShell extension is the recommended editor for writing PowerShell scripts.</span></span>
<span data-ttu-id="4a7cf-107">Il prend en charge les versions suivantes de PowerShell :</span><span class="sxs-lookup"><span data-stu-id="4a7cf-107">It supports the following PowerShell versions:</span></span>

- <span data-ttu-id="4a7cf-108">PowerShell 7 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="4a7cf-108">PowerShell 7 and up</span></span>
- <span data-ttu-id="4a7cf-109">PowerShell Core 6</span><span class="sxs-lookup"><span data-stu-id="4a7cf-109">PowerShell Core 6</span></span>
- <span data-ttu-id="4a7cf-110">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="4a7cf-110">Windows PowerShell 5.1</span></span>

<span data-ttu-id="4a7cf-111">Avant de commencer, vérifiez que PowerShell est présent sur votre système.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-111">Before you begin, make sure PowerShell exists on your system.</span></span> <span data-ttu-id="4a7cf-112">Pour les charges de travail modernes sur Windows, macOS et Linux, voir les liens suivants :</span><span class="sxs-lookup"><span data-stu-id="4a7cf-112">For modern workloads on Windows, macOS, and Linux, see the following links:</span></span>

- <span data-ttu-id="4a7cf-113">[Installation de PowerShell Core sur Linux][install-pscore-linux]</span><span class="sxs-lookup"><span data-stu-id="4a7cf-113">[Installing PowerShell Core on Linux][install-pscore-linux]</span></span>
- <span data-ttu-id="4a7cf-114">[Installation de PowerShell Core sur macOS][install-pscore-macos]</span><span class="sxs-lookup"><span data-stu-id="4a7cf-114">[Installing PowerShell Core on macOS][install-pscore-macos]</span></span>
- <span data-ttu-id="4a7cf-115">[Installation de PowerShell Core sur Windows][install-pscore-windows]</span><span class="sxs-lookup"><span data-stu-id="4a7cf-115">[Installing PowerShell Core on Windows][install-pscore-windows]</span></span>

<span data-ttu-id="4a7cf-116">Pour les charges de travail Windows PowerShell classiques, consultez [Installation de Windows PowerShell][install-winps].</span><span class="sxs-lookup"><span data-stu-id="4a7cf-116">For traditional Windows PowerShell workloads, see [Installing Windows PowerShell][install-winps].</span></span>

> [!NOTE]
> <span data-ttu-id="4a7cf-117">Visual Studio Code est différent de [Visual Studio](https://visualstudio.microsoft.com/).</span><span class="sxs-lookup"><span data-stu-id="4a7cf-117">Visual Studio Code is not the same as [Visual Studio](https://visualstudio.microsoft.com/).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4a7cf-118">[Windows PowerShell ISE][ise] est également toujours disponible pour Windows, mais il n’est plus dans le développement actif de fonctionnalités et ne fonctionne ni avec PowerShell 7 et les versions ultérieures, ni avec PowerShell Core 6.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-118">The [Windows PowerShell ISE][ise] is also still available for Windows, however, it is no longer in active feature development and does not work with PowerShell 7 and up or PowerShell Core 6.</span></span>
> <span data-ttu-id="4a7cf-119">En tant que composant d’expédition de Windows, il continue d’être officiellement pris en charge pour la sécurité et les correctifs de maintenance de haute priorité.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-119">As a shipping component of Windows, it continues to be officially supported for security and high-priority servicing fixes.</span></span> <span data-ttu-id="4a7cf-120">Nous n’avons actuellement aucun projet de supprimer l’environnement ISE de Windows.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-120">We currently have no plans to remove the ISE from Windows.</span></span>

## <a name="editing-with-visual-studio-code"></a><span data-ttu-id="4a7cf-121">Édition avec Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="4a7cf-121">Editing with Visual Studio Code</span></span>

1. <span data-ttu-id="4a7cf-122">Installer Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-122">Install Visual Studio Code.</span></span> <span data-ttu-id="4a7cf-123">Pour plus d’informations, voir la vue d’ensemble [Configurer Visual Studio Code](https://code.visualstudio.com/Docs/setup/setup-overview).</span><span class="sxs-lookup"><span data-stu-id="4a7cf-123">For more information, see the overview [Setting up Visual Studio Code](https://code.visualstudio.com/Docs/setup/setup-overview).</span></span>

    <span data-ttu-id="4a7cf-124">Les instructions d’installation sont propres à chaque plateforme :</span><span class="sxs-lookup"><span data-stu-id="4a7cf-124">There are installation instructions for each platform:</span></span>

    - <span data-ttu-id="4a7cf-125">**Windows** : suivez les instructions d’installation sur la page [Exécution de Visual Studio Code sur Windows](https://code.visualstudio.com/docs/setup/windows).</span><span class="sxs-lookup"><span data-stu-id="4a7cf-125">**Windows**: follow the installation instructions on the [Running Visual Studio Code on Windows](https://code.visualstudio.com/docs/setup/windows) page.</span></span>
    - <span data-ttu-id="4a7cf-126">**macOS** : suivez les instructions d’installation sur la page [Exécution de Visual Studio Code sur macOS](https://code.visualstudio.com/docs/setup/mac).</span><span class="sxs-lookup"><span data-stu-id="4a7cf-126">**macOS**: follow the installation instructions on the [Running Visual Studio Code on macOS](https://code.visualstudio.com/docs/setup/mac) page.</span></span>
    - <span data-ttu-id="4a7cf-127">**Linux** : suivez les instructions d’installation sur la page [Exécution de Visual Studio Code sur Linux](https://code.visualstudio.com/docs/setup/linux).</span><span class="sxs-lookup"><span data-stu-id="4a7cf-127">**Linux**: follow the installation instructions on the [Running Visual Studio Code on Linux](https://code.visualstudio.com/docs/setup/linux) page.</span></span>

1. <span data-ttu-id="4a7cf-128">Installez l’extension PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-128">Install the PowerShell Extension.</span></span>

   1. <span data-ttu-id="4a7cf-129">Lancez l’application Visual Studio Code en tapant `code` dans une console, ou `code-insiders` si vous avez installé Visual Studio Code Insiders.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-129">Launch the Visual Studio Code app by typing `code` in a console or `code-insiders` if you installed Visual Studio Code Insiders.</span></span>
   1. <span data-ttu-id="4a7cf-130">Lancez **Quick Open** sur Windows ou Linux en appuyant sur <kbd>Ctrl</kbd>+<kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-130">Launch **Quick Open** on Windows or Linux by pressing <kbd>Ctrl</kbd>+<kbd>P</kbd>.</span></span> <span data-ttu-id="4a7cf-131">Sur macOS, appuyez sur <kbd>Cmd</kbd>+<kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-131">On macOS, press <kbd>Cmd</kbd>+<kbd>P</kbd>.</span></span>
   1. <span data-ttu-id="4a7cf-132">Dans Quick Open, tapez `ext install powershell`, puis appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-132">In Quick Open, type `ext install powershell` and press **Enter**.</span></span>
   1. <span data-ttu-id="4a7cf-133">La vue **Extensions** s’ouvre dans la barre latérale.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-133">The **Extensions** view opens on the Side Bar.</span></span> <span data-ttu-id="4a7cf-134">Sélectionnez l’extension de PowerShell de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-134">Select the PowerShell extension from Microsoft.</span></span>
      <span data-ttu-id="4a7cf-135">Un écran Visual Studio Code semblable à l’image suivante apparaît :</span><span class="sxs-lookup"><span data-stu-id="4a7cf-135">You should see a Visual Studio Code screen similar to the following image:</span></span>

      ![Visual Studio Code](media/using-vscode/vscode.png)

   1. <span data-ttu-id="4a7cf-137">Cliquez sur le bouton **Installer** sur l’extension PowerShell de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-137">Click the **Install** button on the PowerShell extension from Microsoft.</span></span>
   1. <span data-ttu-id="4a7cf-138">Après l’installation, si vous voyez le bouton **Installer** se changer en **Recharger**, cliquez sur **Recharger**.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-138">After the install, if you see the **Install** button turn into **Reload**, Click on **Reload**.</span></span>
   1. <span data-ttu-id="4a7cf-139">Une fois Visual Studio Code rechargé, vous pouvez passer à l’édition.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-139">After Visual Studio Code has reloaded, you're ready for editing.</span></span>

<span data-ttu-id="4a7cf-140">Par exemple, pour créer un fichier, cliquez sur **Fichier > Nouveau**.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-140">For example, to create a new file, click **File > New**.</span></span> <span data-ttu-id="4a7cf-141">Pour l’enregistrer, cliquez sur **Fichier > Enregistrer**, puis indiquez un nom de fichier, comme `HelloWorld.ps1`.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-141">To save it, click **File > Save** and then provide a file name, such as `HelloWorld.ps1`.</span></span> <span data-ttu-id="4a7cf-142">Pour fermer le fichier, cliquez sur `X` à côté du nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-142">To close the file, click the `X` next to the file name.</span></span> <span data-ttu-id="4a7cf-143">Pour quitter Visual Studio Code, cliquez sur **Fichier > Quitter**.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-143">To exit Visual Studio Code, **File > Exit**.</span></span>

### <a name="installing-the-powershell-extension-on-restricted-systems"></a><span data-ttu-id="4a7cf-144">Installation de l’extension PowerShell sur des systèmes restreints</span><span class="sxs-lookup"><span data-stu-id="4a7cf-144">Installing the PowerShell Extension on Restricted Systems</span></span>

<span data-ttu-id="4a7cf-145">Certains systèmes sont configurés de façon à imposer la vérification de toutes les signatures de code et l’approbation manuelle de PowerShell Editor Services pour qu’il puisse s’exécuter sur le système.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-145">Some systems are set up in a way that requires all code signatures to be checked and requires PowerShell Editor Services to be manually approved to run on the system.</span></span> <span data-ttu-id="4a7cf-146">Une mise à jour de la stratégie de groupe qui modifie la stratégie d’exécution est une cause probable si vous avez installé l’extension PowerShell, mais recevez une erreur de ce type :</span><span class="sxs-lookup"><span data-stu-id="4a7cf-146">A Group Policy update that changes execution policy is a likely cause if you've installed the PowerShell extension but are receiving an error such as:</span></span>

```
Language server startup failed.
```

<span data-ttu-id="4a7cf-147">Pour approuver manuellement PowerShell Editor Services et l’extension PowerShell pour Visual Studio Code, ouvrez une invite PowerShell et exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="4a7cf-147">To manually approve PowerShell Editor Services and the PowerShell extension for Visual Studio Code, open a PowerShell prompt and run the following command:</span></span>

```powershell
Import-Module $HOME\.vscode\extensions\ms-vscode.powershell*\modules\PowerShellEditorServices\PowerShellEditorServices.psd1
```

<span data-ttu-id="4a7cf-148">Le message **Voulez-vous exécuter le logiciel provenant de cet éditeur non approuvé ?** apparaît.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-148">You're prompted with **Do you want to run software from this untrusted publisher?**</span></span>
<span data-ttu-id="4a7cf-149">Tapez `A` pour exécuter le fichier.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-149">Type `A` to run the file.</span></span> <span data-ttu-id="4a7cf-150">Ouvrez ensuite Visual Studio Code et vérifiez que l’extension PowerShell fonctionne correctement.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-150">Then, open Visual Studio Code and check that the PowerShell extension is functioning properly.</span></span> <span data-ttu-id="4a7cf-151">Si vous rencontrez toujours des problèmes de mise en route, faites-le-nous savoir sur [GitHub](https://github.com/PowerShell/vscode-powershell/issues).</span><span class="sxs-lookup"><span data-stu-id="4a7cf-151">If you still have issues getting started, let us know on [GitHub](https://github.com/PowerShell/vscode-powershell/issues).</span></span>

> [!NOTE]
> <span data-ttu-id="4a7cf-152">L’extension PowerShell pour Visual Studio Code ne prend pas en charge l’exécution en mode de langage avec contrainte.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-152">The PowerShell extension for Visual Studio Code does not support running in constrained language mode.</span></span> <span data-ttu-id="4a7cf-153">Pour plus d’informations, consultez le [Problème de suivi de cette prise en charge par GitHub](https://github.com/PowerShell/vscode-powershell/issues/606).</span><span class="sxs-lookup"><span data-stu-id="4a7cf-153">Please see the [GitHub issue tracking that support](https://github.com/PowerShell/vscode-powershell/issues/606) for more information.</span></span>

### <a name="using-an-older-version-of-the-powershell-extension-for-windows-powershell-v3-and-v4"></a><span data-ttu-id="4a7cf-154">Utilisation d’une version antérieure de l’extension PowerShell pour Windows PowerShell v3 et v4</span><span class="sxs-lookup"><span data-stu-id="4a7cf-154">Using an older version of the PowerShell Extension for Windows PowerShell v3 and v4</span></span>

<span data-ttu-id="4a7cf-155">Bien que l’extension PowerShell actuelle [ne prenne plus en charge v3 et v4](https://github.com/PowerShell/vscode-powershell/issues/1310), vous pouvez toujours utiliser la dernière version de l’extension qui a été exécutée.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-155">Although the current PowerShell extension [stopped supporting v3 and v4](https://github.com/PowerShell/vscode-powershell/issues/1310), you can still use the last version of the extension that did.</span></span>

> [!NOTE]
> <span data-ttu-id="4a7cf-156">Il n’y aura aucun correctif supplémentaire pour cette version antérieure de l’extension.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-156">There will be no additional fixes to this older version of the extension.</span></span> <span data-ttu-id="4a7cf-157">Bien que fournie « TELLE QUELLE », elle est à votre disposition si vous utilisez encore Windows PowerShell v3 et Windows PowerShell v4.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-157">It's provided "AS IS" but is available for you if you are still using Windows PowerShell v3 and Windows PowerShell v4.</span></span>

<span data-ttu-id="4a7cf-158">Tout d’abord, ouvrez le volet Extension et recherchez `PowerShell`.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-158">First, open the Extension pane and search for `PowerShell`.</span></span> <span data-ttu-id="4a7cf-159">Cliquez ensuite sur l’engrenage, puis sélectionnez **Installer une autre version...** .</span><span class="sxs-lookup"><span data-stu-id="4a7cf-159">Then click the gear and select **Install another version...**.</span></span>

![Installer une autre version...](media/using-vscode/install-another-version.png)

<span data-ttu-id="4a7cf-161">Sélectionnez ensuite la version **`2020.1.0`** .</span><span class="sxs-lookup"><span data-stu-id="4a7cf-161">Then select the **`2020.1.0`** version.</span></span> <span data-ttu-id="4a7cf-162">Cette version de l’extension était la dernière version à prendre en charge v3 et v4.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-162">This version of the extension was the last version to support v3 and v4.</span></span>

<span data-ttu-id="4a7cf-163">Ajoutez également le paramètre suivant afin que la version de votre extension ne soit pas mise à jour automatiquement :</span><span class="sxs-lookup"><span data-stu-id="4a7cf-163">Also, add the following setting so that your extension version doesn't update automatically:</span></span>

```json
{
    "extensions.autoUpdate": false
}
```

<span data-ttu-id="4a7cf-164">Même si cela fonctionnera dans un avenir proche, Visual Studio Code pourrait implémenter une modification qui arrêterait cette version de l’extension.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-164">Although this will work in the forseeable future, Visual Studio Code could implement a change that breaks this version of the extension.</span></span>
<span data-ttu-id="4a7cf-165">Pour cette raison et à cause de l’absence de support, nous vous recommandons plutôt de procéder comme suit :</span><span class="sxs-lookup"><span data-stu-id="4a7cf-165">Because of this, and lack of support, we highly recommend either:</span></span>

- <span data-ttu-id="4a7cf-166">Téléchargez PowerShell 7 : il s’agit d’une installation côte à côte avec Windows PowerShell qui fonctionne de manière optimale avec l’extension PowerShell</span><span class="sxs-lookup"><span data-stu-id="4a7cf-166">Downloading PowerShell 7 - which is a side-by-side install to Windows PowerShell and works the best with the PowerShell extension</span></span>
- <span data-ttu-id="4a7cf-167">Mise à niveau vers Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="4a7cf-167">Upgrading to Windows PowerShell 5.1</span></span>

<span data-ttu-id="4a7cf-168">La section [Édition avec Visual Studio Code](#editing-with-visual-studio-code) de cet article contient des liens vers l’emplacement d’installation.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-168">The [Editing with Visual Studio Code](#editing-with-visual-studio-code) section in this article links to where to install these.</span></span>

### <a name="choosing-a-version-of-powershell-to-use-with-the-extension"></a><span data-ttu-id="4a7cf-169">Choisir la version de PowerShell à utiliser avec l’extension</span><span class="sxs-lookup"><span data-stu-id="4a7cf-169">Choosing a version of PowerShell to use with the extension</span></span>

<span data-ttu-id="4a7cf-170">Maintenant que PowerShell Core peut s’installer côte à côte avec Windows PowerShell, il est possible d’utiliser une version donnée de PowerShell avec l’extension PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-170">With PowerShell Core installing side-by-side with Windows PowerShell, it's now possible to use a particular version of PowerShell with the PowerShell extension.</span></span> <span data-ttu-id="4a7cf-171">Suivez les étapes ci-dessous pour choisir la version :</span><span class="sxs-lookup"><span data-stu-id="4a7cf-171">Use the following steps to choose the version:</span></span>

1. <span data-ttu-id="4a7cf-172">Ouvrez la **Palette de commandes** sous Windows ou Linux avec <kbd>Ctrl</kbd>+<kbd>Maj</kbd>+<kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-172">Open the **Command Palette** on Windows or Linux with <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>.</span></span> <span data-ttu-id="4a7cf-173">Sur macOS, utilisez <kbd>Cmd</kbd>+<kbd>Maj</kbd>+<kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-173">On macOS, use <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>.</span></span>
1. <span data-ttu-id="4a7cf-174">Recherchez **Session**.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-174">Search for **Session**.</span></span>
1. <span data-ttu-id="4a7cf-175">Cliquez sur **PowerShell : Afficher le menu de session**.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-175">Click on **PowerShell: Show Session Menu**.</span></span>
1. <span data-ttu-id="4a7cf-176">Choisissez la version de PowerShell que vous souhaitez utiliser dans la liste, par exemple : **PowerShell Core**.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-176">Choose the version of PowerShell you want to use from the list, for example: **PowerShell Core**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4a7cf-177">Cette fonctionnalité examine quelques chemins connus sur différents systèmes d’exploitation pour détecter les emplacements d’installation de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-177">This feature looks at a few well-known paths on different operating systems to discover install locations of PowerShell.</span></span> <span data-ttu-id="4a7cf-178">Si vous avez installé PowerShell à un emplacement non standard, il risque de ne pas apparaître d’emblée dans le menu de session.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-178">If you installed PowerShell to a non-typical location, it might not show up initially in the Session Menu.</span></span> <span data-ttu-id="4a7cf-179">Pour étendre le menu de session, [ajoutez vos propres chemins personnalisés](#adding-your-own-powershell-paths-to-the-session-menu) en suivant la procédure décrite ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-179">You can extend the session menu by [adding your own custom paths](#adding-your-own-powershell-paths-to-the-session-menu) as described below.</span></span>

>[!NOTE]
> <span data-ttu-id="4a7cf-180">Il existe un autre moyen d’accéder au menu de session.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-180">There's another way to get to the session menu.</span></span> <span data-ttu-id="4a7cf-181">Quand un fichier PowerShell est ouvert dans l’éditeur, un numéro de version apparaît en vert en bas à droite.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-181">When a PowerShell file is open in your editor, you see a green version number in the bottom right.</span></span> <span data-ttu-id="4a7cf-182">Cliquez dessus pour accéder au menu de session.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-182">Clicking this version number will bring you to the session menu.</span></span>

### <a name="adding-your-own-powershell-paths-to-the-session-menu"></a><span data-ttu-id="4a7cf-183">Ajouter ses propres chemins PowerShell au menu de session</span><span class="sxs-lookup"><span data-stu-id="4a7cf-183">Adding your own PowerShell paths to the session menu</span></span>

<span data-ttu-id="4a7cf-184">Il est possible d’ajouter d’autres chemins d’exécutables PowerShell au menu de session via le [paramètre Visual Studio Code](https://code.visualstudio.com/docs/getstarted/settings) : `powershell.powerShellAdditionalExePaths`.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-184">You can add other PowerShell executable paths to the session menu through the [Visual Studio Code setting](https://code.visualstudio.com/docs/getstarted/settings): `powershell.powerShellAdditionalExePaths`.</span></span>

<span data-ttu-id="4a7cf-185">Ajoutez un élément à la liste `powershell.powerShellAdditionalExePaths` ou créez la liste si elle n’existe pas dans `settings.json` :</span><span class="sxs-lookup"><span data-stu-id="4a7cf-185">Add an item to the list `powershell.powerShellAdditionalExePaths` or create the list if it doesn't exist in your `settings.json`:</span></span>

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

<span data-ttu-id="4a7cf-186">Chaque élément doit comporter :</span><span class="sxs-lookup"><span data-stu-id="4a7cf-186">Each item must have:</span></span>

- <span data-ttu-id="4a7cf-187">`exePath`: chemin de l’exécutable `pwsh` ou `powershell`.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-187">`exePath`: The path to the `pwsh` or `powershell` executable.</span></span>
- <span data-ttu-id="4a7cf-188">`versionName`: texte qui s’affichera dans le menu de session.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-188">`versionName`: The text that will show up in the session menu.</span></span>

<span data-ttu-id="4a7cf-189">Vous pouvez définir la version de PowerShell par défaut avec le paramètre `powershell.powerShellDefaultVersion` en le définissant sur le texte qui s’affiche dans le menu de session (soit `versionName` dans le dernier paramètre) :</span><span class="sxs-lookup"><span data-stu-id="4a7cf-189">You can set the default PowerShell version to use the `powershell.powerShellDefaultVersion` setting by setting this to the text displayed in the session menu (also known as the `versionName` in the last setting):</span></span>

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

<span data-ttu-id="4a7cf-190">Après avoir configuré ce paramètre, redémarrez Visual Studio Code ou rechargez la fenêtre Visual Studio Code active avec la **Palette de commandes**, puis tapez **Développeur : Recharger la fenêtre**.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-190">After you've configured this setting, restart Visual Studio Code or to reload the current Visual Studio Code window from the **Command Palette**, type **Developer: Reload Window**.</span></span>

<span data-ttu-id="4a7cf-191">Si vous ouvrez le menu de session, vous trouvez à présent les versions supplémentaires de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-191">If you open the session menu, you now see your additional PowerShell versions!</span></span>

> [!NOTE]
> <span data-ttu-id="4a7cf-192">Si vous générez PowerShell à partir de la source, c’est un excellent moyen de tester votre build locale de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-192">If you build PowerShell from source, this is a great way to test out your local build of PowerShell.</span></span>

### <a name="configuration-settings-for-visual-studio-code"></a><span data-ttu-id="4a7cf-193">Paramètres de configuration de Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="4a7cf-193">Configuration settings for Visual Studio Code</span></span>

<span data-ttu-id="4a7cf-194">Tout d’abord, si vous n’êtes pas familiarisé avec la modification des paramètres dans Visual Studio Code, nous vous recommandons de consulter la [documentation des paramètres de Visual Studio Code](https://code.visualstudio.com/docs/getstarted/settings).</span><span class="sxs-lookup"><span data-stu-id="4a7cf-194">First, if you're not familiar with how to change settings in Visual Studio Code, we recommend looking at [Visual Studio Code's settings documentation](https://code.visualstudio.com/docs/getstarted/settings).</span></span>

<span data-ttu-id="4a7cf-195">En suivant la procédure décrite dans le paragraphe précédent, vous pouvez ajouter des paramètres de configuration dans `settings.json`.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-195">By using the steps in the previous paragraph, you can add configuration settings in `settings.json`.</span></span>

```json
{
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "files.trimTrailingWhitespace": true,
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

<span data-ttu-id="4a7cf-196">Si vous ne souhaitez pas que ces paramètres affectent tous les types de fichiers, Visual Studio Code permet également des configurations par langage.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-196">If you don't want these settings to affect all files types, Visual Studio Code also allows per-language configurations.</span></span> <span data-ttu-id="4a7cf-197">Vous pouvez créer un paramètre propre au langage en plaçant des paramètres dans un champ `[<language-name>]`.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-197">Create a language-specific setting by putting settings in a `[<language-name>]` field.</span></span> <span data-ttu-id="4a7cf-198">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="4a7cf-198">For example:</span></span>

```json
{
    "[powershell]": {
        "files.encoding": "utf8bom",
        "files.autoGuessEncoding": true
    }
}
```

> [!TIP]
> <span data-ttu-id="4a7cf-199">Pour plus d’informations sur l’encodage de fichier dans Visual Studio Code, consultez [Présentation de l’encodage de fichier](understanding-file-encoding.md).</span><span class="sxs-lookup"><span data-stu-id="4a7cf-199">For more information about file encoding in Visual Studio Code, see [Understanding file encoding](understanding-file-encoding.md).</span></span>
>
> <span data-ttu-id="4a7cf-200">Consultez également [Comment répliquer l’expérience ISE dans Visual Studio Code](How-To-Replicate-the-ISE-Experience-In-VSCode.md) pour obtenir d’autres conseils de configuration de Visual Studio Code pour l’édition avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-200">Also check out the [How to replicate the ISE experience in Visual Studio Code](How-To-Replicate-the-ISE-Experience-In-VSCode.md) for other tips on how to configure Visual Studio Code for PowerShell editing.</span></span>

## <a name="debugging-with-visual-studio-code"></a><span data-ttu-id="4a7cf-201">Débogage avec Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="4a7cf-201">Debugging with Visual Studio Code</span></span>

### <a name="no-workspace-debugging"></a><span data-ttu-id="4a7cf-202">Débogage sans espace de travail</span><span class="sxs-lookup"><span data-stu-id="4a7cf-202">No-workspace debugging</span></span>

<span data-ttu-id="4a7cf-203">À partir de Visual Studio Code version 1.9, il est possible de déboguer des scripts PowerShell sans ouvrir le dossier qui les contient.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-203">As of Visual Studio Code version 1.9 you can debug PowerShell scripts without opening the folder that contains the PowerShell script.</span></span> <span data-ttu-id="4a7cf-204">Ouvrez un fichier de script PowerShell avec **Fichier > Ouvrir un fichier…** , définissez un point d’arrêt sur une ligne (appuyez sur <kbd>F9</kbd>), puis appuyez sur <kbd>F5</kbd> pour démarrer le débogage.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-204">Open the PowerShell script file with **File > Open File...**, set a breakpoint on a line, press <kbd>F9</kbd>, and then press <kbd>F5</kbd> to start debugging.</span></span> <span data-ttu-id="4a7cf-205">Le volet Actions de débogage apparaît ; il permet de s’arrêter dans le débogueur, d’effectuer un pas à pas détaillé, de reprendre et d’arrêter le débogage.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-205">You should see the Debug actions pane appear which allows you to break into the debugger, step, resume, and stop debugging.</span></span>

### <a name="workspace-debugging"></a><span data-ttu-id="4a7cf-206">Débogage d’espace de travail</span><span class="sxs-lookup"><span data-stu-id="4a7cf-206">Workspace debugging</span></span>

<span data-ttu-id="4a7cf-207">Le débogage d’espace de travail fait référence au débogage dans le contexte d’un dossier ouvert dans Visual Studio Code dans le menu **Fichier**  avec **Ouvrir le dossier…** . Le dossier que vous ouvrez est généralement votre dossier de projet PowerShell et/ou la racine de votre dépôt Git.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-207">Workspace debugging refers to debugging in the context of a folder that you've opened in Visual Studio Code from the **File** menu using **Open Folder...**. The folder you open is typically your PowerShell project folder and/or the root of your Git repository.</span></span>

<span data-ttu-id="4a7cf-208">Même dans ce mode, vous pouvez lancer le débogage du script PowerShell actuellement sélectionné en appuyant sur <kbd>F5</kbd>.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-208">Even in this mode, you can start debugging the currently selected PowerShell script by pressing <kbd>F5</kbd>.</span></span> <span data-ttu-id="4a7cf-209">Cependant, le débogage d’espace de travail vous permet de définir plusieurs configurations de débogage autres que simplement déboguer le fichier actuellement ouvert.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-209">However, workspace debugging allows you to define multiple debug configurations other than just debugging the currently open file.</span></span> <span data-ttu-id="4a7cf-210">Nous y arriverons dans un instant.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-210">We'll get to those in a moment.</span></span>

<span data-ttu-id="4a7cf-211">Suivez ces étapes pour créer votre fichier de configuration de débogage :</span><span class="sxs-lookup"><span data-stu-id="4a7cf-211">Follow these steps to create your debug configuration file:</span></span>

  1. <span data-ttu-id="4a7cf-212">Ouvrez la vue **Déboguer** sur Windows ou Linux en appuyant sur <kbd>Ctrl</kbd>+<kbd>Maj</kbd>+<kbd>D</kbd>.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-212">Open the **Debug** view on Windows or Linux by pressing <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>.</span></span> <span data-ttu-id="4a7cf-213">Sur macOS, appuyez sur <kbd>Cmd</kbd>+<kbd>Maj</kbd>+<kbd>D</kbd>.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-213">On macOS, press <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>.</span></span>
  1. <span data-ttu-id="4a7cf-214">Cliquez sur le lien « Créer un fichier launch. JSON ».</span><span class="sxs-lookup"><span data-stu-id="4a7cf-214">Click the "create a launch.json file" link.</span></span>
  1. <span data-ttu-id="4a7cf-215">Visual Studio Code vous invite à **Sélectionner un environnement**.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-215">Visual Studio Code prompts you to **Select Environment**.</span></span> <span data-ttu-id="4a7cf-216">Choisissez **PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-216">Choose **PowerShell**.</span></span>
  1. <span data-ttu-id="4a7cf-217">Enfin, choisissez le type de débogage que vous souhaitez utiliser :</span><span class="sxs-lookup"><span data-stu-id="4a7cf-217">Lastly, choose the type of debugging you'd like to use:</span></span>

- <span data-ttu-id="4a7cf-218">**Lancer le fichier actuel** : lancer et déboguer le fichier dans la fenêtre de l’éditeur actuellement active</span><span class="sxs-lookup"><span data-stu-id="4a7cf-218">**Launch Current File** - Launch and debug the file in the currently active editor window</span></span>
- <span data-ttu-id="4a7cf-219">**Lancer le script** : lancer et déboguer le fichier ou la commande spécifiés</span><span class="sxs-lookup"><span data-stu-id="4a7cf-219">**Launch Script** - Launch and debug the specified file or command</span></span>
- <span data-ttu-id="4a7cf-220">**Session interactive** : déboguer les commandes exécutées à partir de la console intégrée</span><span class="sxs-lookup"><span data-stu-id="4a7cf-220">**Interactive Session** - Debug commands executed from the Integrated Console</span></span>
- <span data-ttu-id="4a7cf-221">**Attacher** : attacher le débogueur à un processus hôte PowerShell en cours d’exécution</span><span class="sxs-lookup"><span data-stu-id="4a7cf-221">**Attach** - Attach the debugger to a running PowerShell Host Process</span></span>

<span data-ttu-id="4a7cf-222">Visual Studio Code crée alors un répertoire et un fichier `.vscode\launch.json` à la racine du dossier de votre espace de travail.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-222">The result is that Visual Studio Code creates a directory and a file `.vscode\launch.json` in the root of your workspace folder.</span></span> <span data-ttu-id="4a7cf-223">C’est là que votre configuration de débogage est stockée.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-223">This location is where your debug configuration is stored.</span></span> <span data-ttu-id="4a7cf-224">Si vos fichiers se trouvent dans un référentiel Git, il est généralement préférable de valider le fichier `launch.json`.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-224">If your files are in a Git repository, you typically want to commit the `launch.json` file.</span></span> <span data-ttu-id="4a7cf-225">Le fichier `launch.json` présente le contenu suivant :</span><span class="sxs-lookup"><span data-stu-id="4a7cf-225">The contents of the `launch.json` file are:</span></span>

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

<span data-ttu-id="4a7cf-226">Ce fichier représente les scénarios de débogage courants.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-226">This file represents the common debug scenarios.</span></span> <span data-ttu-id="4a7cf-227">Quand vous ouvrez ce fichier dans l’éditeur, un bouton **Ajouter une configuration…** apparaît.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-227">When you open this file in the editor, you see an **Add Configuration...** button.</span></span> <span data-ttu-id="4a7cf-228">Vous pouvez cliquer sur ce bouton pour ajouter d’autres configurations de débogage PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-228">You can click this button to add more PowerShell debug configurations.</span></span> <span data-ttu-id="4a7cf-229">Il est utile d’ajouter la configuration **PowerShell : Lancer un script**.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-229">One useful configuration to add is **PowerShell: Launch Script**.</span></span> <span data-ttu-id="4a7cf-230">Avec cette configuration, vous pouvez spécifier un fichier avec des arguments facultatifs qui doit se lancer quand vous appuyez sur <kbd>F5</kbd>, quel que soit le fichier actuellement actif dans l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-230">With this configuration, you can specify a file with optional arguments that should be launched whenever you press <kbd>F5</kbd> no matter which file is currently active in the editor.</span></span>

<span data-ttu-id="4a7cf-231">Une fois la configuration de débogage établie, vous pouvez sélectionner la configuration que vous souhaitez utiliser lors d’une session de débogage.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-231">After the debug configuration is established, you can select which configuration you want to use during a debug session.</span></span> <span data-ttu-id="4a7cf-232">Sélectionnez une configuration dans la liste déroulante de la configuration de débogage, dans la barre d’outils de la vue **Déboguer**.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-232">Select a configuration from the debug configuration drop-down in the **Debug** view's toolbar.</span></span>

<span data-ttu-id="4a7cf-233">Quelques blogs peuvent être utiles pour bien démarrer avec l’extension PowerShell pour Visual Studio Code :</span><span class="sxs-lookup"><span data-stu-id="4a7cf-233">There are a few blogs that may be helpful to get you started using PowerShell extension for Visual Studio Code:</span></span>

- <span data-ttu-id="4a7cf-234">[Extension PowerShell][ps-extension]</span><span class="sxs-lookup"><span data-stu-id="4a7cf-234">[PowerShell Extension][ps-extension]</span></span>
- <span data-ttu-id="4a7cf-235">[Écrire et déboguer des scripts PowerShell dans Visual Studio Code][debug]</span><span class="sxs-lookup"><span data-stu-id="4a7cf-235">[Write and debug PowerShell scripts in Visual Studio Code][debug]</span></span>
- <span data-ttu-id="4a7cf-236">[Aide sur le débogage avec Visual Studio Code][vscode-guide]</span><span class="sxs-lookup"><span data-stu-id="4a7cf-236">[Debugging Visual Studio Code Guidance][vscode-guide]</span></span>
- <span data-ttu-id="4a7cf-237">[Débogage de PowerShell dans Visual Studio Code][ps-vscode]</span><span class="sxs-lookup"><span data-stu-id="4a7cf-237">[Debugging PowerShell in Visual Studio Code][ps-vscode]</span></span>
- <span data-ttu-id="4a7cf-238">[Guide pratique pour le développement avec PowerShell dans Visual Studio Code][getting-started]</span><span class="sxs-lookup"><span data-stu-id="4a7cf-238">[Get started with PowerShell development in Visual Studio Code][getting-started]</span></span>
- <span data-ttu-id="4a7cf-239">[Fonctionnalités d’édition de Visual Studio Code pour le développement avec PowerShell – Partie 1][editing-part1]</span><span class="sxs-lookup"><span data-stu-id="4a7cf-239">[Visual Studio Code editing features for PowerShell development – Part 1][editing-part1]</span></span>
- <span data-ttu-id="4a7cf-240">[Fonctionnalités d’édition de Visual Studio Code pour le développement avec PowerShell – Partie 2][editing-part2]</span><span class="sxs-lookup"><span data-stu-id="4a7cf-240">[Visual Studio Code editing features for PowerShell development – Part 2][editing-part2]</span></span>
- <span data-ttu-id="4a7cf-241">[Débogage des scripts PowerShell dans Visual Studio Code – Partie 1][debugging-part1]</span><span class="sxs-lookup"><span data-stu-id="4a7cf-241">[Debugging PowerShell script in Visual Studio Code – Part 1][debugging-part1]</span></span>
- <span data-ttu-id="4a7cf-242">[Débogage des scripts PowerShell dans Visual Studio Code – Partie 2][debugging-part2]</span><span class="sxs-lookup"><span data-stu-id="4a7cf-242">[Debugging PowerShell script in Visual Studio Code – Part 2][debugging-part2]</span></span>

[ise]: ../ise/Introducing-the-Windows-PowerShell-ISE.md
[install-pscore-linux]:  ../../install/Installing-PowerShell-Core-on-Linux.md
[install-pscore-macos]:  ../../install/Installing-PowerShell-Core-on-macOS.md
[install-pscore-windows]: ../../install/Installing-PowerShell-Core-on-Windows.md
[install-winps]: ../../install/Installing-Windows-PowerShell.md
[ps-extension]: https://blogs.msdn.microsoft.com/cdndevs/2015/12/11/visual-studio-code-powershell-extension/
[debug]: https://devblogs.microsoft.com/powershell/announcing-powershell-language-support-for-visual-studio-code-and-more/
[vscode-guide]: https://johnpapa.net/debugging-with-visual-studio-code/
[ps-vscode]: https://github.com/PowerShell/vscode-powershell/tree/master/examples
[getting-started]: https://devblogs.microsoft.com/scripting/get-started-with-powershell-development-in-visual-studio-code/
[editing-part1]: https://devblogs.microsoft.com/scripting/visual-studio-code-editing-features-for-powershell-development-part-1/
[editing-part2]: https://devblogs.microsoft.com/scripting/visual-studio-code-editing-features-for-powershell-development-part-2/
[debugging-part1]: https://devblogs.microsoft.com/scripting/debugging-powershell-script-in-visual-studio-code-part-1/
[debugging-part2]: https://devblogs.microsoft.com/scripting/debugging-powershell-script-in-visual-studio-code-part-2/

## <a name="powershell-extension-for-visual-studio-code"></a><span data-ttu-id="4a7cf-243">Extension PowerShell pour Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="4a7cf-243">PowerShell extension for Visual Studio Code</span></span>

<span data-ttu-id="4a7cf-244">Vous trouverez le code source de l’extension PowerShell sur [GitHub](https://github.com/PowerShell/vscode-powershell).</span><span class="sxs-lookup"><span data-stu-id="4a7cf-244">The PowerShell extension's source code can be found on [GitHub](https://github.com/PowerShell/vscode-powershell).</span></span>

<span data-ttu-id="4a7cf-245">Si vous êtes intéressé à contribuer, les demandes de tirage sont très appréciées.</span><span class="sxs-lookup"><span data-stu-id="4a7cf-245">If you're interested in contributing, Pull Request are greatly appreciated.</span></span> <span data-ttu-id="4a7cf-246">Pour commencer, suivez les [instructions de la documentation du développeur sur GitHub](https://github.com/PowerShell/vscode-powershell/blob/master/docs/development.md).</span><span class="sxs-lookup"><span data-stu-id="4a7cf-246">Follow along with the [developer documentation on GitHub](https://github.com/PowerShell/vscode-powershell/blob/master/docs/development.md) to get started.</span></span>

## <a name="troubleshooting-the-powershell-extension-for-visual-studio-code"></a><span data-ttu-id="4a7cf-247">Résolution des problèmes de l’extension PowerShell pour Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="4a7cf-247">Troubleshooting the PowerShell extension for Visual Studio Code</span></span>

<span data-ttu-id="4a7cf-248">Si vous rencontrez des problèmes lors de l’utilisation de Visual Studio Code pour le développement de scripts PowerShell, consultez le [guide de résolution des problèmes de sur GitHub](https://github.com/PowerShell/vscode-powershell/blob/master/docs/troubleshooting.md)</span><span class="sxs-lookup"><span data-stu-id="4a7cf-248">If you experience any issues using Visual Studio Code for PowerShell script development, please take a look at the [troubleshooting guide on GitHub](https://github.com/PowerShell/vscode-powershell/blob/master/docs/troubleshooting.md)</span></span>
