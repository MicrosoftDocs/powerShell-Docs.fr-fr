---
title: Utilisation de Visual Studio Code pour le débogage et l’édition à distance
description: Utilisation de Visual Studio Code pour le débogage et l’édition à distance
ms.date: 08/06/2018
ms.openlocfilehash: fbc1ee3556e822b4afb2b37111d0688dc89fdab3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086666"
---
# <a name="using-visual-studio-code-for-remote-editing-and-debugging"></a><span data-ttu-id="68f9b-103">Utilisation de Visual Studio Code pour le débogage et l’édition à distance</span><span class="sxs-lookup"><span data-stu-id="68f9b-103">Using Visual Studio Code for remote editing and debugging</span></span>

<span data-ttu-id="68f9b-104">Ceux d’entre vous qui sont familiarisés avec l’environnement ISE se rappelleront peut-être que vous pouvez exécuter `psedit file.ps1` à partir de la console intégrée pour ouvrir des fichiers, locaux ou distants, directement dans ISE.</span><span class="sxs-lookup"><span data-stu-id="68f9b-104">For those of you that were familiar with the ISE, you may recall that you could run `psedit file.ps1` from the integrated console to open files - local or remote - right in the ISE.</span></span>

<span data-ttu-id="68f9b-105">En fait, cette fonctionnalité est également disponible dans l’extension PowerShell pour VSCode.</span><span class="sxs-lookup"><span data-stu-id="68f9b-105">As it turns out, this feature is also available in the PowerShell extension for VSCode.</span></span> <span data-ttu-id="68f9b-106">Ce guide vous explique comment procéder.</span><span class="sxs-lookup"><span data-stu-id="68f9b-106">This guide will show you how to do it.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="68f9b-107">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="68f9b-107">Prerequisites</span></span>

<span data-ttu-id="68f9b-108">Ce guide suppose que vous disposez des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="68f9b-108">This guide assumes that you have:</span></span>

- <span data-ttu-id="68f9b-109">une ressource distante (par exemple une machine virtuelle, un conteneur) à laquelle vous avez accès ;</span><span class="sxs-lookup"><span data-stu-id="68f9b-109">a remote resource (ex: a VM, a container) that you have access to</span></span>
- <span data-ttu-id="68f9b-110">PowerShell en cours d’exécution sur cette ressource et l’ordinateur hôte</span><span class="sxs-lookup"><span data-stu-id="68f9b-110">PowerShell running on it and the host machine</span></span>
- <span data-ttu-id="68f9b-111">VSCode et l’extension PowerShell pour VSCode</span><span class="sxs-lookup"><span data-stu-id="68f9b-111">VSCode and the PowerShell extension for VSCode</span></span>

<span data-ttu-id="68f9b-112">Cette fonctionnalité fonctionne sur Windows PowerShell et PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="68f9b-112">This feature works on Windows PowerShell and PowerShell Core.</span></span>

<span data-ttu-id="68f9b-113">Cette fonctionnalité fonctionne également lorsque vous vous connectez à un ordinateur distant via WinRM, PowerShell Direct ou SSH.</span><span class="sxs-lookup"><span data-stu-id="68f9b-113">This feature also works when connecting to a remote machine via WinRM, PowerShell Direct, or SSH.</span></span> <span data-ttu-id="68f9b-114">Si vous souhaitez utiliser SSH, mais sur Windows, consultez la [version Win32 de SSH](https://github.com/PowerShell/Win32-OpenSSH).</span><span class="sxs-lookup"><span data-stu-id="68f9b-114">If you want to use SSH, but are using Windows, check out the [Win32 version of SSH](https://github.com/PowerShell/Win32-OpenSSH)!</span></span>

## <a name="lets-go"></a><span data-ttu-id="68f9b-115">C’est parti</span><span class="sxs-lookup"><span data-stu-id="68f9b-115">Let's go</span></span>

<span data-ttu-id="68f9b-116">Dans cette section, je vais effectuer des modifications et un débogage à distance à partir de mon MacBook Pro sur une machine virtuelle Ubuntu s’exécutant dans Azure.</span><span class="sxs-lookup"><span data-stu-id="68f9b-116">In this section, I'll walk through remote editing and debugging from my MacBook Pro, to an Ubuntu VM running in Azure.</span></span> <span data-ttu-id="68f9b-117">Je n’utiliserai peut-être pas Windows, mais **le processus est identique**.</span><span class="sxs-lookup"><span data-stu-id="68f9b-117">I might not be using Windows, but **the process is identical**.</span></span>

### <a name="local-file-editing-with-open-editorfile"></a><span data-ttu-id="68f9b-118">Modification d’un fichier local avec Open-EditorFile</span><span class="sxs-lookup"><span data-stu-id="68f9b-118">Local file editing with Open-EditorFile</span></span>

<span data-ttu-id="68f9b-119">Après avoir lancé l’extension PowerShell pour VSCode et ouvert la console PowerShell intégrée, nous pouvons taper `Open-EditorFile foo.ps1` ou `psedit foo.ps1` pour ouvrir le fichier local foo.ps1 directement dans l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="68f9b-119">With the PowerShell extension for VSCode started and the PowerShell Integrated Console opened, we can type `Open-EditorFile foo.ps1` or `psedit foo.ps1` to open the local foo.ps1 file right in the editor.</span></span>

![Open-EditorFile foo.ps1 fonctionne localement](https://user-images.githubusercontent.com/2644648/34895897-7c2c46ac-f79c-11e7-9410-a252aff52f13.png)

>[!NOTE]
> <span data-ttu-id="68f9b-121">foo.ps1 se doit déjà exister.</span><span class="sxs-lookup"><span data-stu-id="68f9b-121">foo.ps1 must already exist.</span></span>

<span data-ttu-id="68f9b-122">À partir de là, nous pouvons :</span><span class="sxs-lookup"><span data-stu-id="68f9b-122">From there, we can:</span></span>

<span data-ttu-id="68f9b-123">ajouter des points d’arrêt à la gouttière ![ajout de point d’arrêt à la gouttière](https://user-images.githubusercontent.com/2644648/34895893-7bdc38e2-f79c-11e7-8026-8ad53f9a1bad.png)</span><span class="sxs-lookup"><span data-stu-id="68f9b-123">add breakpoints to the gutter ![adding breakpoint to gutter](https://user-images.githubusercontent.com/2644648/34895893-7bdc38e2-f79c-11e7-8026-8ad53f9a1bad.png)</span></span>

<span data-ttu-id="68f9b-124">et appuyer sur F5 pour déboguer le script PowerShell.</span><span class="sxs-lookup"><span data-stu-id="68f9b-124">and hit F5 to debug the PowerShell script.</span></span>
<span data-ttu-id="68f9b-125">![débogage du script local PowerShell](https://user-images.githubusercontent.com/2644648/34895894-7bedb874-f79c-11e7-9180-7e0dc2d02af8.png)</span><span class="sxs-lookup"><span data-stu-id="68f9b-125">![debugging the PowerShell local script](https://user-images.githubusercontent.com/2644648/34895894-7bedb874-f79c-11e7-9180-7e0dc2d02af8.png)</span></span>

<span data-ttu-id="68f9b-126">Pendant le débogage, vous pouvez interagir avec la console de débogage, consultez les variables dans l’étendue à gauche, et exécutez tous les autres outils de débogage standard.</span><span class="sxs-lookup"><span data-stu-id="68f9b-126">While debugging, you can interact with the debug console, check out the variables in the scope on the left, and all the other standard debugging tools.</span></span>

### <a name="remote-file-editing-with-open-editorfile"></a><span data-ttu-id="68f9b-127">Modification de fichiers à distance avec Open-EditorFile</span><span class="sxs-lookup"><span data-stu-id="68f9b-127">Remote file editing with Open-EditorFile</span></span>

<span data-ttu-id="68f9b-128">Examinons maintenant la modification et le débogage de fichiers à distance.</span><span class="sxs-lookup"><span data-stu-id="68f9b-128">Now let's get into remote file editing and debugging.</span></span> <span data-ttu-id="68f9b-129">Les étapes sont presque identiques et nous n’avons qu’une seule tâche préalable à effectuer : ouvrir notre session PowerShell sur le serveur distant.</span><span class="sxs-lookup"><span data-stu-id="68f9b-129">The steps are nearly the same, there's just one thing we need to do first - enter our PowerShell session to the remote server.</span></span>

<span data-ttu-id="68f9b-130">Nous utiliserons pour cela une applet de commande.</span><span class="sxs-lookup"><span data-stu-id="68f9b-130">There's a cmdlet for to do so.</span></span> <span data-ttu-id="68f9b-131">Elle s’appelle `Enter-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="68f9b-131">It's called `Enter-PSSession`.</span></span>

<span data-ttu-id="68f9b-132">Voici le fonctionnement détaillé de cette applet de commande :</span><span class="sxs-lookup"><span data-stu-id="68f9b-132">The watered down explanation of the cmdlet is:</span></span>

- <span data-ttu-id="68f9b-133">`Enter-PSSession -ComputerName foo` démarre une session via WinRM</span><span class="sxs-lookup"><span data-stu-id="68f9b-133">`Enter-PSSession -ComputerName foo` starts a session via WinRM</span></span>
- <span data-ttu-id="68f9b-134">`Enter-PSSession -ContainerId foo` et `Enter-PSSession -VmId foo` démarrent une session via PowerShell Direct</span><span class="sxs-lookup"><span data-stu-id="68f9b-134">`Enter-PSSession -ContainerId foo` and `Enter-PSSession -VmId foo` start a session via PowerShell Direct</span></span>
- <span data-ttu-id="68f9b-135">`Enter-PSSession -HostName foo` démarre une session via SSH</span><span class="sxs-lookup"><span data-stu-id="68f9b-135">`Enter-PSSession -HostName foo` starts a session via SSH</span></span>

<span data-ttu-id="68f9b-136">Pour plus d’informations sur `Enter-PSSession`, consultez la documentation disponible [ici](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="68f9b-136">For more info on `Enter-PSSession`, check out the docs [here](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-6).</span></span>

<span data-ttu-id="68f9b-137">J’utiliserai SSH pour l’accès distant puisque je passerai de macOS vers une machine virtuelle Ubuntu dans Azure.</span><span class="sxs-lookup"><span data-stu-id="68f9b-137">I'll be using SSH for remoting since I'm going from macOS to an Ubuntu VM in Azure.</span></span>

<span data-ttu-id="68f9b-138">Tout d’abord, dans la console intégrée, exécutons Enter-PSSession.</span><span class="sxs-lookup"><span data-stu-id="68f9b-138">First, in the Integrated Console, let's run our Enter-PSSession.</span></span> <span data-ttu-id="68f9b-139">Vous saurez que vous êtes dans la session car `[something]` s’affichera à gauche de l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="68f9b-139">You'll know that you're in the session because `[something]` will show up to the left of your prompt.</span></span>

![L’appel à Enter-PSSession](https://user-images.githubusercontent.com/2644648/34895896-7c18e0bc-f79c-11e7-9b36-6f4bd0e9b0db.png)

<span data-ttu-id="68f9b-141">De là, nous pouvons effectuer les étapes exactes comme si nous modifiions un script local.</span><span class="sxs-lookup"><span data-stu-id="68f9b-141">From there, we can do the exact steps as if we were editing a local script.</span></span>

1. <span data-ttu-id="68f9b-142">Exécutez `Open-EditorFile test.ps1` ou `psedit test.ps1` pour ouvrir le fichier `test.ps1` distant ![Open-EditorFile fichier test.ps1](https://user-images.githubusercontent.com/2644648/34895898-7c3e6a12-f79c-11e7-8bdf-549b591ecbcb.png)</span><span class="sxs-lookup"><span data-stu-id="68f9b-142">Run `Open-EditorFile test.ps1` or `psedit test.ps1` to open the remote `test.ps1` file ![Open-EditorFile the test.ps1 file](https://user-images.githubusercontent.com/2644648/34895898-7c3e6a12-f79c-11e7-8bdf-549b591ecbcb.png)</span></span>
2. <span data-ttu-id="68f9b-143">Modifier le fichier/définir des points d’arrêt</span><span class="sxs-lookup"><span data-stu-id="68f9b-143">Edit the file/set breakpoints</span></span> ![modifier et définir des points d’arrêt](https://user-images.githubusercontent.com/2644648/34895892-7bb68246-f79c-11e7-8c0a-c2121773afbb.png)
3. <span data-ttu-id="68f9b-145">Démarrer le débogage (F5) du fichier distant</span><span class="sxs-lookup"><span data-stu-id="68f9b-145">Start debugging (F5) the remote file</span></span>

![débogage du fichier distant](https://user-images.githubusercontent.com/2644648/34895895-7c040782-f79c-11e7-93ea-47724fa5c10d.png)

<span data-ttu-id="68f9b-147">Voilà, c’est tout !</span><span class="sxs-lookup"><span data-stu-id="68f9b-147">That's all there's to it!</span></span> <span data-ttu-id="68f9b-148">Nous espérons que ce guide a répondu à vos questions sur le débogage et les modifications à distance à l’aide de PowerShell dans VSCode.</span><span class="sxs-lookup"><span data-stu-id="68f9b-148">We hope that this guide helped clear up any questions about remote debugging and editing PowerShell in VSCode.</span></span>

<span data-ttu-id="68f9b-149">Si vous rencontrez des problèmes, n’hésitez pas à nous le faire savoir [sur le référentiel GitHub](http://github.com/powershell/vscode-powershell).</span><span class="sxs-lookup"><span data-stu-id="68f9b-149">If you have any problems, feel free to open issues [on the GitHub repo](http://github.com/powershell/vscode-powershell).</span></span>
