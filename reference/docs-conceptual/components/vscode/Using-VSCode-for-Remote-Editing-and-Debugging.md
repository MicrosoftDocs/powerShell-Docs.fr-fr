---
title: Utilisation de Visual Studio Code pour le débogage et l’édition à distance
description: Utilisation de Visual Studio Code pour le débogage et l’édition à distance
ms.date: 06/13/2019
ms.openlocfilehash: 5ce7f575d90ff47fd6b8a0a2b567e972ec3a9fef
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "78279128"
---
# <a name="using-visual-studio-code-for-remote-editing-and-debugging"></a><span data-ttu-id="cf705-103">Utilisation de Visual Studio Code pour le débogage et l’édition à distance</span><span class="sxs-lookup"><span data-stu-id="cf705-103">Using Visual Studio Code for remote editing and debugging</span></span>

<span data-ttu-id="cf705-104">Ceux d’entre vous qui sont familiarisés avec l’environnement ISE se rappelleront peut-être que vous pouvez exécuter `psedit file.ps1` à partir de la console intégrée pour ouvrir des fichiers, locaux ou distants, directement dans ISE.</span><span class="sxs-lookup"><span data-stu-id="cf705-104">For those of you that are familiar with the ISE, you may recall that you could run `psedit file.ps1` from the integrated console to open files - local or remote - right in the ISE.</span></span>

<span data-ttu-id="cf705-105">Cette fonctionnalité est également disponible dans l’extension PowerShell pour VSCode.</span><span class="sxs-lookup"><span data-stu-id="cf705-105">This feature is also available in the PowerShell extension for VSCode.</span></span> <span data-ttu-id="cf705-106">Ce guide vous explique comment procéder.</span><span class="sxs-lookup"><span data-stu-id="cf705-106">This guide shows you how to do it.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="cf705-107">Conditions préalables requises</span><span class="sxs-lookup"><span data-stu-id="cf705-107">Prerequisites</span></span>

<span data-ttu-id="cf705-108">Ce guide suppose que vous disposez des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="cf705-108">This guide assumes that you have:</span></span>

- <span data-ttu-id="cf705-109">une ressource distante (par exemple une machine virtuelle, un conteneur) à laquelle vous avez accès ;</span><span class="sxs-lookup"><span data-stu-id="cf705-109">A remote resource (ex: a VM, a container) that you have access to</span></span>
- <span data-ttu-id="cf705-110">PowerShell en cours d’exécution sur cette ressource et l’ordinateur hôte</span><span class="sxs-lookup"><span data-stu-id="cf705-110">PowerShell running on it and the host machine</span></span>
- <span data-ttu-id="cf705-111">VSCode et l’extension PowerShell pour VSCode</span><span class="sxs-lookup"><span data-stu-id="cf705-111">VSCode and the PowerShell extension for VSCode</span></span>

<span data-ttu-id="cf705-112">Cette fonctionnalité fonctionne sur Windows PowerShell et PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="cf705-112">This feature works on Windows PowerShell and PowerShell Core.</span></span>

<span data-ttu-id="cf705-113">Cette fonctionnalité fonctionne également lorsque vous vous connectez à un ordinateur distant via WinRM, PowerShell Direct ou SSH.</span><span class="sxs-lookup"><span data-stu-id="cf705-113">This feature also works when connecting to a remote machine via WinRM, PowerShell Direct, or SSH.</span></span> <span data-ttu-id="cf705-114">Si vous souhaitez utiliser SSH, mais sur Windows, consultez la [version Win32 de SSH](https://github.com/PowerShell/Win32-OpenSSH).</span><span class="sxs-lookup"><span data-stu-id="cf705-114">If you want to use SSH, but are using Windows, check out the [Win32 version of SSH](https://github.com/PowerShell/Win32-OpenSSH)!</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cf705-115">Les commandes `Open-EditorFile` et `psedit` fonctionnent uniquement dans la **console intégrée PowerShell** créée par l’extension PowerShell pour VSCode.</span><span class="sxs-lookup"><span data-stu-id="cf705-115">The `Open-EditorFile` and `psedit` commands only work in the **PowerShell Integrated Console** created by the PowerShell extension for VSCode.</span></span>

## <a name="usage-examples"></a><span data-ttu-id="cf705-116">Exemples d'utilisation</span><span class="sxs-lookup"><span data-stu-id="cf705-116">Usage examples</span></span>

<span data-ttu-id="cf705-117">Ces exemples montrent des modifications et un débogage à distance à partir d’un MacBook Pro sur une machine virtuelle Ubuntu s’exécutant dans Azure.</span><span class="sxs-lookup"><span data-stu-id="cf705-117">These examples show remote editing and debugging from a MacBook Pro to an Ubuntu VM running in Azure.</span></span> <span data-ttu-id="cf705-118">Le processus est identique sur Windows.</span><span class="sxs-lookup"><span data-stu-id="cf705-118">The process is identical on Windows.</span></span>

### <a name="local-file-editing-with-open-editorfile"></a><span data-ttu-id="cf705-119">Modification d’un fichier local avec Open-EditorFile</span><span class="sxs-lookup"><span data-stu-id="cf705-119">Local file editing with Open-EditorFile</span></span>

<span data-ttu-id="cf705-120">Après avoir lancé l’extension PowerShell pour VSCode et ouvert la console PowerShell intégrée, nous pouvons taper `Open-EditorFile foo.ps1` ou `psedit foo.ps1` pour ouvrir le fichier local foo.ps1 directement dans l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="cf705-120">With the PowerShell extension for VSCode started and the PowerShell Integrated Console opened, we can type `Open-EditorFile foo.ps1` or `psedit foo.ps1` to open the local foo.ps1 file right in the editor.</span></span>

![Open-EditorFile foo.ps1 fonctionne localement](media/Using-VSCode-for-Remote-Editing-and-Debugging/1-open-local-file.png)

>[!NOTE]
> <span data-ttu-id="cf705-122">Le fichier `foo.ps1` doit déjà exister.</span><span class="sxs-lookup"><span data-stu-id="cf705-122">The file `foo.ps1` must already exist.</span></span>

<span data-ttu-id="cf705-123">À partir de là, nous pouvons :</span><span class="sxs-lookup"><span data-stu-id="cf705-123">From there, we can:</span></span>

- <span data-ttu-id="cf705-124">ajouter des points d’arrêt à la marge</span><span class="sxs-lookup"><span data-stu-id="cf705-124">Add breakpoints to the gutter</span></span>

  ![ajout de points d’arrêt à la marge](media/Using-VSCode-for-Remote-Editing-and-Debugging/2-adding-breakpoint-gutter.png)

- <span data-ttu-id="cf705-126">Appuyez sur F5 pour déboguer le script PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cf705-126">Hit F5 to debug the PowerShell script.</span></span>

  ![débogage du script local PowerShell](media/Using-VSCode-for-Remote-Editing-and-Debugging/3-local-debug.png)

<span data-ttu-id="cf705-128">Pendant le débogage, vous pouvez interagir avec la console de débogage, consultez les variables dans l’étendue à gauche, et exécutez tous les autres outils de débogage standard.</span><span class="sxs-lookup"><span data-stu-id="cf705-128">While debugging, you can interact with the debug console, check out the variables in the scope on the left, and all the other standard debugging tools.</span></span>

### <a name="remote-file-editing-with-open-editorfile"></a><span data-ttu-id="cf705-129">Modification de fichiers à distance avec Open-EditorFile</span><span class="sxs-lookup"><span data-stu-id="cf705-129">Remote file editing with Open-EditorFile</span></span>

<span data-ttu-id="cf705-130">Examinons maintenant la modification et le débogage de fichiers à distance.</span><span class="sxs-lookup"><span data-stu-id="cf705-130">Now let's get into remote file editing and debugging.</span></span> <span data-ttu-id="cf705-131">Les étapes sont presque identiques et nous n’avons qu’une seule tâche préalable à effectuer : ouvrir notre session PowerShell sur le serveur distant.</span><span class="sxs-lookup"><span data-stu-id="cf705-131">The steps are nearly the same, there's just one thing we need to do first - enter our PowerShell session to the remote server.</span></span>

<span data-ttu-id="cf705-132">Nous utiliserons pour cela une applet de commande.</span><span class="sxs-lookup"><span data-stu-id="cf705-132">There's a cmdlet for to do so.</span></span> <span data-ttu-id="cf705-133">Elle s’appelle `Enter-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="cf705-133">It's called `Enter-PSSession`.</span></span>

<span data-ttu-id="cf705-134">Voici le fonctionnement détaillé de cette applet de commande :</span><span class="sxs-lookup"><span data-stu-id="cf705-134">The watered down explanation of the cmdlet is:</span></span>

- <span data-ttu-id="cf705-135">`Enter-PSSession -ComputerName foo` démarre une session via WinRM</span><span class="sxs-lookup"><span data-stu-id="cf705-135">`Enter-PSSession -ComputerName foo` starts a session via WinRM</span></span>
- <span data-ttu-id="cf705-136">`Enter-PSSession -ContainerId foo` et `Enter-PSSession -VmId foo` démarrent une session via PowerShell Direct</span><span class="sxs-lookup"><span data-stu-id="cf705-136">`Enter-PSSession -ContainerId foo` and `Enter-PSSession -VmId foo` start a session via PowerShell Direct</span></span>
- <span data-ttu-id="cf705-137">`Enter-PSSession -HostName foo` démarre une session via SSH</span><span class="sxs-lookup"><span data-stu-id="cf705-137">`Enter-PSSession -HostName foo` starts a session via SSH</span></span>

<span data-ttu-id="cf705-138">Pour plus d’informations, consultez la documentation [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession).</span><span class="sxs-lookup"><span data-stu-id="cf705-138">For more information, see the documentation for [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession).</span></span>

<span data-ttu-id="cf705-139">Comme nous passons de macOS à une machine virtuelle Ubuntu dans Azure, nous utilisons SSH pour la communication à distance.</span><span class="sxs-lookup"><span data-stu-id="cf705-139">Since we are going from macOS to an Ubuntu VM in Azure, we are using SSH for remoting.</span></span>

<span data-ttu-id="cf705-140">Tout d’abord, dans la console intégrée, exécutez `Enter-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="cf705-140">First, in the Integrated Console, run `Enter-PSSession`.</span></span> <span data-ttu-id="cf705-141">Vous êtes connecté à la session à distance lorsque `[<hostname>]` s’affiche à gauche de votre invite.</span><span class="sxs-lookup"><span data-stu-id="cf705-141">You're connected to the remote session when `[<hostname>]` shows up to the left of your prompt.</span></span>

![L’appel à Enter-PSSession](media/Using-VSCode-for-Remote-Editing-and-Debugging/4-enter-pssession.png)

<span data-ttu-id="cf705-143">Maintenant, nous pouvons effectuer les mêmes étapes que si nous modifiions un script local.</span><span class="sxs-lookup"><span data-stu-id="cf705-143">Now, we can do the same steps as if we are editing a local script.</span></span>

1. <span data-ttu-id="cf705-144">Exécutez `Open-EditorFile test.ps1` ou `psedit test.ps1` pour ouvrir le fichier `test.ps1` distant</span><span class="sxs-lookup"><span data-stu-id="cf705-144">Run `Open-EditorFile test.ps1` or `psedit test.ps1` to open the remote `test.ps1` file</span></span>

  ![Fichier Open-EditorFile the test.ps1](media/Using-VSCode-for-Remote-Editing-and-Debugging/5-open-remote-file.png)

1. <span data-ttu-id="cf705-146">Modifier le fichier/définir des points d’arrêt</span><span class="sxs-lookup"><span data-stu-id="cf705-146">Edit the file/set breakpoints</span></span>

   ![modifier et définir des points d’arrêt](media/Using-VSCode-for-Remote-Editing-and-Debugging/6-set-breakpoints.png)

1. <span data-ttu-id="cf705-148">Démarrer le débogage (F5) du fichier distant</span><span class="sxs-lookup"><span data-stu-id="cf705-148">Start debugging (F5) the remote file</span></span>

   ![débogage du fichier distant](media/Using-VSCode-for-Remote-Editing-and-Debugging/7-start-debugging.png)

<span data-ttu-id="cf705-150">Si vous rencontrez des problèmes, vous pouvez ouvrir des tickets dans le [référentiel GitHub](https://github.com/powershell/vscode-powershell).</span><span class="sxs-lookup"><span data-stu-id="cf705-150">If you have any problems, you can open issues in the [GitHub repo](https://github.com/powershell/vscode-powershell).</span></span>
