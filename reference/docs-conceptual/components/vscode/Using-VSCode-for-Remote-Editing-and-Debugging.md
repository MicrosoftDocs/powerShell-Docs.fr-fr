---
title: Utilisation de Visual Studio Code pour le débogage et l’édition à distance
description: Utilisation de Visual Studio Code pour le débogage et l’édition à distance
ms.date: 08/06/2018
ms.openlocfilehash: bab1a629a7e9dafd5957cf93025abb18b8a4f326
ms.sourcegitcommit: 548547b2d5fc73e726bb9fec6175d452a351d975
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2018
ms.locfileid: "53655608"
---
# <a name="using-visual-studio-code-for-remote-editing-and-debugging"></a><span data-ttu-id="ce01c-103">Utilisation de Visual Studio Code pour le débogage et l’édition à distance</span><span class="sxs-lookup"><span data-stu-id="ce01c-103">Using Visual Studio Code for remote editing and debugging</span></span>

<span data-ttu-id="ce01c-104">Pour ceux d'entre vous qui ont été familiarisé avec l’environnement ISE, vous vous rappelez peut-être que vous pouvez exécuter `psedit file.ps1` à partir de la console intégrée pour ouvrir des fichiers - locales ou distants - avec le bouton droit dans l’environnement ISE.</span><span class="sxs-lookup"><span data-stu-id="ce01c-104">For those of you that were familiar with the ISE, you may recall that you could run `psedit file.ps1` from the integrated console to open files - local or remote - right in the ISE.</span></span>

<span data-ttu-id="ce01c-105">En fait, cette fonctionnalité est également disponible dans l’extension PowerShell pour VSCode.</span><span class="sxs-lookup"><span data-stu-id="ce01c-105">As it turns out, this feature is also available in the PowerShell extension for VSCode.</span></span> <span data-ttu-id="ce01c-106">Ce guide vous explique comment procéder.</span><span class="sxs-lookup"><span data-stu-id="ce01c-106">This guide will show you how to do it.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ce01c-107">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="ce01c-107">Prerequisites</span></span>

<span data-ttu-id="ce01c-108">Ce guide suppose que vous avez :</span><span class="sxs-lookup"><span data-stu-id="ce01c-108">This guide assumes that you have:</span></span>

- <span data-ttu-id="ce01c-109">une ressource distante (ex : une machine virtuelle, un conteneur) que vous avez accès à</span><span class="sxs-lookup"><span data-stu-id="ce01c-109">a remote resource (ex: a VM, a container) that you have access to</span></span>
- <span data-ttu-id="ce01c-110">PowerShell en cours d’exécution et l’ordinateur hôte</span><span class="sxs-lookup"><span data-stu-id="ce01c-110">PowerShell running on it and the host machine</span></span>
- <span data-ttu-id="ce01c-111">VSCode et l’extension PowerShell pour VSCode</span><span class="sxs-lookup"><span data-stu-id="ce01c-111">VSCode and the PowerShell extension for VSCode</span></span>

<span data-ttu-id="ce01c-112">Cette fonctionnalité fonctionne sur Windows PowerShell et PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="ce01c-112">This feature works on Windows PowerShell and PowerShell Core.</span></span>

<span data-ttu-id="ce01c-113">Cette fonctionnalité fonctionne également lorsque vous vous connectez à un ordinateur à distance via WinRM, PowerShell Direct ou SSH.</span><span class="sxs-lookup"><span data-stu-id="ce01c-113">This feature also works when connecting to a remote machine via WinRM, PowerShell Direct, or SSH.</span></span> <span data-ttu-id="ce01c-114">Si vous souhaitez utiliser SSH, mais sont à l’aide de Windows, consultez le [version Win32 de SSH](https://github.com/PowerShell/Win32-OpenSSH)!</span><span class="sxs-lookup"><span data-stu-id="ce01c-114">If you want to use SSH, but are using Windows, check out the [Win32 version of SSH](https://github.com/PowerShell/Win32-OpenSSH)!</span></span>

## <a name="lets-go"></a><span data-ttu-id="ce01c-115">C’est parti</span><span class="sxs-lookup"><span data-stu-id="ce01c-115">Let's go</span></span>

<span data-ttu-id="ce01c-116">Dans cette section, je vais vous guider avec modification à distance et le débogage à partir de mon MacBook Pro, à une VM Ubuntu s’exécutant dans Azure.</span><span class="sxs-lookup"><span data-stu-id="ce01c-116">In this section, I'll walk through remote editing and debugging from my MacBook Pro, to an Ubuntu VM running in Azure.</span></span> <span data-ttu-id="ce01c-117">Je ne pourrais pas être à l’aide de Windows, mais **le processus est identique**.</span><span class="sxs-lookup"><span data-stu-id="ce01c-117">I might not be using Windows, but **the process is identical**.</span></span>

### <a name="local-file-editing-with-open-editorfile"></a><span data-ttu-id="ce01c-118">Modification avec EditorFile d’ouverture de fichier local</span><span class="sxs-lookup"><span data-stu-id="ce01c-118">Local file editing with Open-EditorFile</span></span>

<span data-ttu-id="ce01c-119">Avec l’extension PowerShell pour démarrer VSCode et la Console intégré PowerShell est ouvert, nous pouvons saisir `Open-EditorFile foo.ps1` ou `psedit foo.ps1` pour ouvrir le fichier local foo.ps1 se directement dans l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="ce01c-119">With the PowerShell extension for VSCode started and the PowerShell Integrated Console opened, we can type `Open-EditorFile foo.ps1` or `psedit foo.ps1` to open the local foo.ps1 file right in the editor.</span></span>

![Foo.ps1 se Open-EditorFile fonctionne localement](https://user-images.githubusercontent.com/2644648/34895897-7c2c46ac-f79c-11e7-9410-a252aff52f13.png)

>[!NOTE]
> <span data-ttu-id="ce01c-121">foo.ps1 se doit déjà exister.</span><span class="sxs-lookup"><span data-stu-id="ce01c-121">foo.ps1 must already exist.</span></span>

<span data-ttu-id="ce01c-122">À partir de là, nous pouvons :</span><span class="sxs-lookup"><span data-stu-id="ce01c-122">From there, we can:</span></span>

<span data-ttu-id="ce01c-123">ajouter des points d’arrêt à la marge ![Ajout de point d’arrêt pour la reliure](https://user-images.githubusercontent.com/2644648/34895893-7bdc38e2-f79c-11e7-8026-8ad53f9a1bad.png)</span><span class="sxs-lookup"><span data-stu-id="ce01c-123">add breakpoints to the gutter ![adding breakpoint to gutter](https://user-images.githubusercontent.com/2644648/34895893-7bdc38e2-f79c-11e7-8026-8ad53f9a1bad.png)</span></span>

<span data-ttu-id="ce01c-124">et appuyez sur F5 pour déboguer le script PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ce01c-124">and hit F5 to debug the PowerShell script.</span></span>
<span data-ttu-id="ce01c-125">![déboguer le script local PowerShell](https://user-images.githubusercontent.com/2644648/34895894-7bedb874-f79c-11e7-9180-7e0dc2d02af8.png)</span><span class="sxs-lookup"><span data-stu-id="ce01c-125">![debugging the PowerShell local script](https://user-images.githubusercontent.com/2644648/34895894-7bedb874-f79c-11e7-9180-7e0dc2d02af8.png)</span></span>

<span data-ttu-id="ce01c-126">Pendant le débogage, vous pouvez interagir avec la console de débogage, consultez les variables dans la portée à gauche et standard outils de débogage.</span><span class="sxs-lookup"><span data-stu-id="ce01c-126">While debugging, you can interact with the debug console, check out the variables in the scope on the left, and all the other standard debugging tools.</span></span>

### <a name="remote-file-editing-with-open-editorfile"></a><span data-ttu-id="ce01c-127">Modification avec Open-EditorFile de fichier distant</span><span class="sxs-lookup"><span data-stu-id="ce01c-127">Remote file editing with Open-EditorFile</span></span>

<span data-ttu-id="ce01c-128">Maintenant nous allons apprendre à la modification et débogage des fichiers à distance.</span><span class="sxs-lookup"><span data-stu-id="ce01c-128">Now let's get into remote file editing and debugging.</span></span> <span data-ttu-id="ce01c-129">Les étapes sont presque identiques, il existe une seule chose que nous devons effectuer tout d’abord, entrez notre session PowerShell au serveur distant.</span><span class="sxs-lookup"><span data-stu-id="ce01c-129">The steps are nearly the same, there's just one thing we need to do first - enter our PowerShell session to the remote server.</span></span>

<span data-ttu-id="ce01c-130">Il est une applet de commande au pour faire.</span><span class="sxs-lookup"><span data-stu-id="ce01c-130">There's a cmdlet for to do so.</span></span> <span data-ttu-id="ce01c-131">Elle est appelée `Enter-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="ce01c-131">It's called `Enter-PSSession`.</span></span>

<span data-ttu-id="ce01c-132">L’explication diluée vers le bas de l’applet de commande est :</span><span class="sxs-lookup"><span data-stu-id="ce01c-132">The watered down explanation of the cmdlet is:</span></span>

- <span data-ttu-id="ce01c-133">`Enter-PSSession -ComputerName foo` démarre une session via WinRM</span><span class="sxs-lookup"><span data-stu-id="ce01c-133">`Enter-PSSession -ComputerName foo` starts a session via WinRM</span></span>
- <span data-ttu-id="ce01c-134">`Enter-PSSession -ContainerId foo` et `Enter-PSSession -VmId foo` démarrer une session via PowerShell Direct</span><span class="sxs-lookup"><span data-stu-id="ce01c-134">`Enter-PSSession -ContainerId foo` and `Enter-PSSession -VmId foo` start a session via PowerShell Direct</span></span>
- <span data-ttu-id="ce01c-135">`Enter-PSSession -HostName foo` démarre une session via SSH</span><span class="sxs-lookup"><span data-stu-id="ce01c-135">`Enter-PSSession -HostName foo` starts a session via SSH</span></span>

<span data-ttu-id="ce01c-136">Pour plus d’informations sur `Enter-PSSession`, consultez la documentation [ici](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="ce01c-136">For more info on `Enter-PSSession`, check out the docs [here](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-6).</span></span>

<span data-ttu-id="ce01c-137">Je vais utiliser SSH pour l’accès distant dans la mesure où je veux à partir de macOS une VM Ubuntu dans Azure.</span><span class="sxs-lookup"><span data-stu-id="ce01c-137">I'll be using SSH for remoting since I'm going from macOS to an Ubuntu VM in Azure.</span></span>

<span data-ttu-id="ce01c-138">Tout d’abord, dans la Console intégrée, nous allons exécuter notre Enter-PSSession.</span><span class="sxs-lookup"><span data-stu-id="ce01c-138">First, in the Integrated Console, let's run our Enter-PSSession.</span></span> <span data-ttu-id="ce01c-139">Vous saurez que vous êtes dans la session, car `[something]` s’affiche à gauche de l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="ce01c-139">You'll know that you're in the session because `[something]` will show up to the left of your prompt.</span></span>

![L’appel à Enter-PSSession](https://user-images.githubusercontent.com/2644648/34895896-7c18e0bc-f79c-11e7-9b36-6f4bd0e9b0db.png)

<span data-ttu-id="ce01c-141">À partir de là, nous pouvons effectuer les étapes exactes comme si nous étions en train de modifier un script local.</span><span class="sxs-lookup"><span data-stu-id="ce01c-141">From there, we can do the exact steps as if we were editing a local script.</span></span>

1. <span data-ttu-id="ce01c-142">Exécutez `Open-EditorFile test.ps1` ou `psedit test.ps1` pour ouvrir l’élément distant `test.ps1` fichier ![Open-EditorFile le fichier test.ps1](https://user-images.githubusercontent.com/2644648/34895898-7c3e6a12-f79c-11e7-8bdf-549b591ecbcb.png)</span><span class="sxs-lookup"><span data-stu-id="ce01c-142">Run `Open-EditorFile test.ps1` or `psedit test.ps1` to open the remote `test.ps1` file ![Open-EditorFile the test.ps1 file](https://user-images.githubusercontent.com/2644648/34895898-7c3e6a12-f79c-11e7-8bdf-549b591ecbcb.png)</span></span>
2. <span data-ttu-id="ce01c-143">Modifier les points d’arrêt/jeu de fichiers</span><span class="sxs-lookup"><span data-stu-id="ce01c-143">Edit the file/set breakpoints</span></span> ![Modifiez et définissez des points d’arrêt](https://user-images.githubusercontent.com/2644648/34895892-7bb68246-f79c-11e7-8c0a-c2121773afbb.png)
3. <span data-ttu-id="ce01c-145">Démarrer le débogage (F5) le fichier distant</span><span class="sxs-lookup"><span data-stu-id="ce01c-145">Start debugging (F5) the remote file</span></span>

![débogage de fichier distant](https://user-images.githubusercontent.com/2644648/34895895-7c040782-f79c-11e7-93ea-47724fa5c10d.png)

<span data-ttu-id="ce01c-147">C’est tout cela !</span><span class="sxs-lookup"><span data-stu-id="ce01c-147">That's all there's to it!</span></span> <span data-ttu-id="ce01c-148">Nous espérons que ce guide a permis à nettoyer des questions sur le débogage distant et la modification de PowerShell dans VSCode.</span><span class="sxs-lookup"><span data-stu-id="ce01c-148">We hope that this guide helped clear up any questions about remote debugging and editing PowerShell in VSCode.</span></span>

<span data-ttu-id="ce01c-149">Si vous rencontrez des problèmes, n’hésitez pas à ouvrir des problèmes [sur le référentiel GitHub](http://github.com/powershell/vscode-powershell).</span><span class="sxs-lookup"><span data-stu-id="ce01c-149">If you have any problems, feel free to open issues [on the GitHub repo](http://github.com/powershell/vscode-powershell).</span></span>
