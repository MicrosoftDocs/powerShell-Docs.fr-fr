---
title: Prise en main de PowerShell
description: Où trouver et comment lancer PowerShell pour les nouveaux utilisateurs.
ms.date: 06/02/2020
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 8b9fee222347970df4e35f9ba0841232952a292d
ms.sourcegitcommit: df5e6f032ee2d4b556d50406832732d2f7dc2502
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2021
ms.locfileid: "99603875"
---
# <a name="chapter-1---getting-started-with-powershell"></a><span data-ttu-id="d1e7f-103">Chapitre 1 - Bien démarrer avec PowerShell</span><span class="sxs-lookup"><span data-stu-id="d1e7f-103">Chapter 1 - Getting Started with PowerShell</span></span>

<span data-ttu-id="d1e7f-104">Lors des conférences ou des réunions de groupes d’utilisateurs visant à présenter PowerShell, j’ai remarqué que souvent, le présentateur avait déjà lancé PowerShell avant même que la présentation n’ait démarré.</span><span class="sxs-lookup"><span data-stu-id="d1e7f-104">I often find that presenters at conferences and user group meetings already have PowerShell running when they start entry-level presentations.</span></span> <span data-ttu-id="d1e7f-105">Ce livre commence par répondre aux questions qui m’ont été posées lors des conférences par ceux qui n’avaient jamais encore utilisé PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d1e7f-105">This book begins by answering the questions I've heard attendees who haven't previously used PowerShell ask in those sessions.</span></span>

<span data-ttu-id="d1e7f-106">Plus précisément, ce chapitre explique comment trouver et lancer PowerShell, et comment surmonter certaines difficultés que peuvent rencontrer les nouveaux utilisateurs de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d1e7f-106">Specifically, this chapter focuses on finding and launching PowerShell, and solving some of the initial pain points that new users experience with PowerShell.</span></span> <span data-ttu-id="d1e7f-107">Il est important de suivre les exemples présentés dans ce chapitre sur votre ordinateur Windows 10 Lab Environment.</span><span class="sxs-lookup"><span data-stu-id="d1e7f-107">Be sure to follow along and walk through the examples shown in this chapter on your Windows 10 lab environment computer.</span></span>

## <a name="what-do-i-need-to-get-started-with-powershell"></a><span data-ttu-id="d1e7f-108">De quoi ai-je besoin pour bien démarrer avec PowerShell ?</span><span class="sxs-lookup"><span data-stu-id="d1e7f-108">What do I need to get started with PowerShell?</span></span>

<span data-ttu-id="d1e7f-109">Toutes les versions actuelles des systèmes d’exploitation Windows sont livrées avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d1e7f-109">All modern versions of Windows operating systems ship with PowerShell installed.</span></span> <span data-ttu-id="d1e7f-110">Si vous exécutez une version antérieure à la version 5.1, vous devez installer la dernière version.</span><span class="sxs-lookup"><span data-stu-id="d1e7f-110">If you're running a version older than 5.1, you should install the latest version.</span></span>

- <span data-ttu-id="d1e7f-111">Pour mettre à niveau votre version vers Windows PowerShell 5.1, consultez [Mise à niveau des instances Windows PowerShell existantes][].</span><span class="sxs-lookup"><span data-stu-id="d1e7f-111">To upgrade to Windows PowerShell 5.1, see [Upgrading existing Windows PowerShell][]</span></span>
- <span data-ttu-id="d1e7f-112">Pour installer la dernière version de PowerShell, consultez [Installation de PowerShell][].</span><span class="sxs-lookup"><span data-stu-id="d1e7f-112">To install the latest version of PowerShell, see [Installing PowerShell][]</span></span>

## <a name="where-do-i-find-powershell"></a><span data-ttu-id="d1e7f-113">Où trouver PowerShell ?</span><span class="sxs-lookup"><span data-stu-id="d1e7f-113">Where do I find PowerShell?</span></span>

<span data-ttu-id="d1e7f-114">Le moyen le plus simple de rechercher PowerShell sur Windows 10 est de taper **PowerShell** dans la barre de recherche, comme le montre la figure 1-1.</span><span class="sxs-lookup"><span data-stu-id="d1e7f-114">The easiest way to find PowerShell on Windows 10 is to type **PowerShell** into the search bar as shown in Figure 1-1.</span></span>

![Figure 1-1 - Recherche de PowerShell dans le menu Démarrer](media/figure1-1.png)

<span data-ttu-id="d1e7f-116">Notez que la figure 1-1 montre quatre raccourcis différents pour PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d1e7f-116">Notice that four different shortcuts for PowerShell are shown in Figure 1-1.</span></span> <span data-ttu-id="d1e7f-117">Dans ce livre, l’ordinateur utilisé à des fins de démonstration exécute la version 64 bits de Windows 10. Vous avez donc une version 64 bits de la console PowerShell et de PowerShell ISE (environnement de script intégré), ainsi qu’une version 32 bits pour chacun, comme l’indique le suffixe (x86) dans les raccourcis.</span><span class="sxs-lookup"><span data-stu-id="d1e7f-117">The computer used for demonstration purposes in this book is running the 64-bit version of Windows 10 so there's a 64-bit version of the PowerShell console and the PowerShell ISE (Integrated Scripting Environment), and a 32-bit version of each one as denoted by the (x86) suffix on the shortcuts.</span></span> <span data-ttu-id="d1e7f-118">Si vous exécutez une version 32 bits de Windows 10, vous n’aurez que deux raccourcis.</span><span class="sxs-lookup"><span data-stu-id="d1e7f-118">If you happen to be running a 32-bit version of Windows 10, you'll only have two shortcuts.</span></span> <span data-ttu-id="d1e7f-119">Ces éléments n’ont pas le suffixe (x86), mais il s’agit de la version 32 bits.</span><span class="sxs-lookup"><span data-stu-id="d1e7f-119">Those items don't have the (x86) suffix, but are 32-bit versions.</span></span> <span data-ttu-id="d1e7f-120">Si vous disposez d’un système d’exploitation 64 bits, je vous recommande d’exécuter la version 64 bits de PowerShell, sauf si vous avez une raison particulière d’exécuter la version 32 bits.</span><span class="sxs-lookup"><span data-stu-id="d1e7f-120">If you have a 64-bit operating system, my recommendation is to run the 64-bit version of PowerShell unless you have a specific reason for running the 32-bit version.</span></span>

<span data-ttu-id="d1e7f-121">Pour plus d’informations sur le démarrage de PowerShell sur d’autres versions de Windows, consultez [Démarrage de Windows PowerShell][].</span><span class="sxs-lookup"><span data-stu-id="d1e7f-121">For information about starting PowerShell on other versions of Windows, see [Starting Windows PowerShell][].</span></span>

## <a name="how-do-i-launch-powershell"></a><span data-ttu-id="d1e7f-122">Comment lancer PowerShell ?</span><span class="sxs-lookup"><span data-stu-id="d1e7f-122">How do I launch PowerShell?</span></span>

<span data-ttu-id="d1e7f-123">Dans les environnements d’entreprise de production dont j’ai la charge, j’utilise trois comptes d’utilisateur Active Directory différents.</span><span class="sxs-lookup"><span data-stu-id="d1e7f-123">In the production enterprise environments that I support, I use three different Active Directory user accounts.</span></span> <span data-ttu-id="d1e7f-124">J’ai pris ces mêmes comptes comme exemple dans l’environnement lab de ce livre.</span><span class="sxs-lookup"><span data-stu-id="d1e7f-124">I've mirrored those accounts in the lab environment used in this book.</span></span> <span data-ttu-id="d1e7f-125">Je me connecte à l’ordinateur Windows 10 en tant qu’utilisateur de domaine, mais pas en tant qu’administrateur de domaine ou administrateur local.</span><span class="sxs-lookup"><span data-stu-id="d1e7f-125">I log into the Windows 10 computer as a domain user who is not a domain or local administrator.</span></span>

<span data-ttu-id="d1e7f-126">J’ai lancé la console PowerShell en cliquant sur le raccourci « Windows PowerShell », comme illustré dans la figure 1-1.</span><span class="sxs-lookup"><span data-stu-id="d1e7f-126">I've launched the PowerShell console by clicking on the "Windows PowerShell" shortcut as shown in Figure 1-1.</span></span>

![Figure 1-4 - Barre de titre de la fenêtre PowerShell](media/figure1-4.png)

<span data-ttu-id="d1e7f-128">Notez que la barre de titre de la console PowerShell indique « Windows PowerShell », comme dans la figure 1-4.</span><span class="sxs-lookup"><span data-stu-id="d1e7f-128">Notice that the title bar of the PowerShell console says "Windows PowerShell" as shown in Figure 1-4.</span></span> <span data-ttu-id="d1e7f-129">Certaines commandes s’exécutent bien, toutefois, PowerShell ne peut pas participer au contrôle de compte d’utilisateur (UAC).</span><span class="sxs-lookup"><span data-stu-id="d1e7f-129">Some commands run fine, but PowerShell can't participate in User Access Control (UAC).</span></span> <span data-ttu-id="d1e7f-130">Cela signifie qu’il ne peut pas demander une élévation des privilèges pour les tâches qui nécessitent l’approbation d’un administrateur.</span><span class="sxs-lookup"><span data-stu-id="d1e7f-130">That means it's unable to prompt for elevation for tasks that require the approval of an administrator.</span></span>
<span data-ttu-id="d1e7f-131">Le message d’erreur suivant est généré :</span><span class="sxs-lookup"><span data-stu-id="d1e7f-131">The following error message is generated:</span></span>

```powershell
Get-Service -Name W32Time | Stop-Service
```

```Output
Stop-Service : Service 'Windows Time (W32Time)' cannot be stopped due to the following
error: Cannot open W32Time service on computer '.'.
At line:1 char:29
+ Get-Service -Name W32Time | Stop-Service
+
    + CategoryInfo          : CloseError: (System.ServiceProcess.ServiceController:ServiceController)
     [Stop-Service], ServiceCommandException
    + FullyQualifiedErrorId : CouldNotStopService,Microsoft.PowerShell.Commands.StopServiceCommand
```

<span data-ttu-id="d1e7f-132">La solution à ce problème consiste à exécuter PowerShell en tant qu’utilisateur de domaine et administrateur local.</span><span class="sxs-lookup"><span data-stu-id="d1e7f-132">The solution to this problem is to run PowerShell as a domain user who is a local administrator.</span></span>
<span data-ttu-id="d1e7f-133">Voici la configuration de mon deuxième compte d’utilisateur de domaine.</span><span class="sxs-lookup"><span data-stu-id="d1e7f-133">This is how my second domain user account is configured.</span></span> <span data-ttu-id="d1e7f-134">Si j’applique le principe du « privilège minimum », ce compte ne doit PAS être un administrateur de domaine, ni disposer de privilèges élevés au sein du domaine.</span><span class="sxs-lookup"><span data-stu-id="d1e7f-134">Using the principal of least privilege, this account should NOT be a domain administrator, or have any elevated privileges in the domain.</span></span>

<span data-ttu-id="d1e7f-135">Fermez PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d1e7f-135">Close PowerShell.</span></span> <span data-ttu-id="d1e7f-136">Relancez la console PowerShell, mais cette fois-ci, cliquez avec le bouton droit sur le raccourci **Windows PowerShell**, puis sélectionnez **Exécuter en tant qu’administrateur**, comme indiqué dans la figure 1-5.</span><span class="sxs-lookup"><span data-stu-id="d1e7f-136">Relaunch the PowerShell console, except this time right-click on the **Windows PowerShell** shortcut and select **Run as administrator** as shown in Figure 1-5.</span></span>

![Figure 1-5 - Menu contextuel -Exécuter en tant qu’administrateur](media/figure1-5.png)

<span data-ttu-id="d1e7f-138">Si vous êtes connecté à Windows en tant qu’utilisateur normal, vous êtes invité à entrer vos informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="d1e7f-138">If you're logged into Windows as a normal user, you'll be prompted for credentials.</span></span> <span data-ttu-id="d1e7f-139">Je vais entrer les informations d’identification de mon compte d’utilisateur, qui est un compte d’utilisateur de domaine et d’administrateur local, comme le montre la figure 1-6.</span><span class="sxs-lookup"><span data-stu-id="d1e7f-139">I'll enter the credentials for my user account who is a domain user and local admin as shown in Figure 1-6.</span></span>

![Figure 1-6](media/figure1-6.png)

<span data-ttu-id="d1e7f-141">Une fois que vous avez relancé PowerShell en tant qu’administrateur, la barre de titre doit indiquer « Administrateur : Windows PowerShell», comme illustré à la figure 1-7.</span><span class="sxs-lookup"><span data-stu-id="d1e7f-141">Once PowerShell is relaunched as an administrator, the title bar should say "Administrator: Windows PowerShell" as shown in Figure 1-7.</span></span>

![Figure 1-7](media/figure1-7.png)

<span data-ttu-id="d1e7f-143">Maintenant que PowerShell est exécuté avec une élévation des privilèges en tant qu’administrateur local, le contrôle de compte d’utilisateur ne posera plus de problème lorsque vous exécuterez une commande sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="d1e7f-143">Now that PowerShell is being run elevated as a local administrator, UAC will no longer be a problem when a command is run on the local computer that would normally require a prompt for elevation.</span></span> <span data-ttu-id="d1e7f-144">Notez toutefois que toutes les autres commandes exécutées à partir de cette instance de la console PowerShell s’exécutent elles aussi avec des privilèges élevés.</span><span class="sxs-lookup"><span data-stu-id="d1e7f-144">Keep in mind though that any command run from this elevated instance of the PowerShell console, also runs elevated.</span></span>

<span data-ttu-id="d1e7f-145">Pour simplifier la recherche de PowerShell et le lancer en tant qu’administrateur, je vous recommande de l’épingler à la barre des tâches et de le configurer pour qu’il se lance automatiquement en tant qu’administrateur chaque fois qu’il est exécuté.</span><span class="sxs-lookup"><span data-stu-id="d1e7f-145">To simplify finding PowerShell and launching it as an administrator, I recommend pinning it to the taskbar and setting it to automatically launch as an admin each time it's run.</span></span>

<span data-ttu-id="d1e7f-146">Recherchez de nouveau PowerShell, mais cette fois-ci, cliquez dessus avec le bouton droit, puis sélectionnez « Épingler à la barre des tâches », comme illustré à la figure 1-8.</span><span class="sxs-lookup"><span data-stu-id="d1e7f-146">Search for PowerShell again, except this time right-click on it and select "Pin to taskbar" as shown in Figure 1-8.</span></span>

![Figure 1-8](media/figure1-8.png)

<span data-ttu-id="d1e7f-148">Cliquez avec le bouton droit sur le raccourci PowerShell qui est maintenant épinglé à la barre des tâches, puis sélectionnez Propriétés, comme indiqué dans la figure 1-9.</span><span class="sxs-lookup"><span data-stu-id="d1e7f-148">Right-click on the PowerShell shortcut that's now pinned to the taskbar and select properties as shown in Figure 1-9.</span></span>

![Figure 1-9 - Contrôle de compte d’utilisateur - Entrer les informations d’identification](media/figure1-9.png)

<span data-ttu-id="d1e7f-150">Cliquez sur « Avancé », comme indiqué par le « 1 » dans la figure 1-10, cochez la case « Exécuter en tant qu’administrateur », comme indiqué par le « 2 » dans la figure 1-10, puis cliquez deux fois sur OK pour accepter les modifications et quitter les deux boîtes de dialogue.</span><span class="sxs-lookup"><span data-stu-id="d1e7f-150">Click on "Advanced" as denoted by #1 in Figure 1-10, then check the "Run as administrator" checkbox as denoted by #2 in Figure 1-10, and then click OK twice to accept the changes and exit out of both dialog boxes.</span></span>

![Figure 1-10 - Barre de titre affichant « Administrateur »](media/figure1-10.png)

<span data-ttu-id="d1e7f-152">Vous n’aurez plus à rechercher PowerShell ni à le configurer pour être exécuté en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="d1e7f-152">You'll never have to worry about finding PowerShell or whether or not it's running as an administrator again.</span></span>

<span data-ttu-id="d1e7f-153">Si vous exécutez PowerShell en tant qu’administrateur dans le but d’éviter les problèmes liés au contrôle de compte d’utilisateur, cela impactera uniquement les commandes qui sont exécutées sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="d1e7f-153">Running PowerShell elevated as an administrator to prevent having problems with UAC only impacts commands that are run against the local computer.</span></span> <span data-ttu-id="d1e7f-154">Cela n’aura aucun effet sur les commandes qui ciblent les ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="d1e7f-154">It has no effect on commands that target remote computers.</span></span>

## <a name="what-version-of-powershell-am-i-running"></a><span data-ttu-id="d1e7f-155">Quelle est la version de mon instance PowerShell ?</span><span class="sxs-lookup"><span data-stu-id="d1e7f-155">What version of PowerShell am I running?</span></span>

<span data-ttu-id="d1e7f-156">Dans PowerShell, il existe plusieurs variables automatiques qui stockent des informations d’état.</span><span class="sxs-lookup"><span data-stu-id="d1e7f-156">There are a number of automatic variables in PowerShell that store state information.</span></span> <span data-ttu-id="d1e7f-157">L’une de ces variables est `$PSVersionTable`, qui contient une table de hachage pouvant être utilisée pour afficher des informations utiles sur la version de PowerShell :</span><span class="sxs-lookup"><span data-stu-id="d1e7f-157">One of these variables is `$PSVersionTable`, which contains a hashtable that can be used to display the relevant PowerShell version information:</span></span>

```powershell
$PSVersionTable
```

```Output
Name                           Value
----                           -----
PSVersion                      5.1.19041.1
PSEdition                      Desktop
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
BuildVersion                   10.0.19041.1
CLRVersion                     4.0.30319.42000
WSManStackVersion              3.0
PSRemotingProtocolVersion      2.3
SerializationVersion           1.1.0.1
```

<span data-ttu-id="d1e7f-158">Les versions récentes de Windows PowerShell sont distribuées avec Windows Management Framework (WMF).</span><span class="sxs-lookup"><span data-stu-id="d1e7f-158">Newer versions of Windows PowerShell are distributed as part of the Windows Management Framework (WMF).</span></span> <span data-ttu-id="d1e7f-159">Chaque version de WMF nécessite une version spécifique de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d1e7f-159">A specific version of the .NET Framework is required depending on the WMF version.</span></span> <span data-ttu-id="d1e7f-160">Pour mettre à niveau votre version vers Windows PowerShell 5.1, consultez [Mise à niveau des instances Windows PowerShell existantes][].</span><span class="sxs-lookup"><span data-stu-id="d1e7f-160">To upgrade to Windows PowerShell 5.1, see [Upgrading existing Windows PowerShell][].</span></span>

## <a name="execution-policy"></a><span data-ttu-id="d1e7f-161">Stratégie d’exécution</span><span class="sxs-lookup"><span data-stu-id="d1e7f-161">Execution Policy</span></span>

<span data-ttu-id="d1e7f-162">Contrairement à la croyance populaire, la stratégie d’exécution de PowerShell ne constitue pas une barrière de sécurité.</span><span class="sxs-lookup"><span data-stu-id="d1e7f-162">Contrary to popular belief, the execution policy in PowerShell is not a security boundary.</span></span> <span data-ttu-id="d1e7f-163">Elle est conçue pour empêcher un utilisateur d’exécuter un script à son insu.</span><span class="sxs-lookup"><span data-stu-id="d1e7f-163">It's designed to prevent a user from unknowingly running a script.</span></span> <span data-ttu-id="d1e7f-164">Un utilisateur déterminé peut facilement contourner cette stratégie d’exécution dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d1e7f-164">A determined user can easily bypass the execution policy in PowerShell.</span></span> <span data-ttu-id="d1e7f-165">Le tableau 1-2 montre la stratégie d’exécution par défaut des systèmes d’exploitation Windows actuels.</span><span class="sxs-lookup"><span data-stu-id="d1e7f-165">Table 1-2 shows the default execution policy for current Windows operating systems.</span></span>

| <span data-ttu-id="d1e7f-166">Version du système d’exploitation Windows</span><span class="sxs-lookup"><span data-stu-id="d1e7f-166">Windows Operating System Version</span></span> | <span data-ttu-id="d1e7f-167">Stratégie d’exécution par défaut</span><span class="sxs-lookup"><span data-stu-id="d1e7f-167">Default Execution Policy</span></span> |
| -------------------------------- | ------------------------ |
| <span data-ttu-id="d1e7f-168">Server 2019</span><span class="sxs-lookup"><span data-stu-id="d1e7f-168">Server 2019</span></span>                      | <span data-ttu-id="d1e7f-169">RemoteSigned</span><span class="sxs-lookup"><span data-stu-id="d1e7f-169">Remote Signed</span></span>            |
| <span data-ttu-id="d1e7f-170">Server 2016</span><span class="sxs-lookup"><span data-stu-id="d1e7f-170">Server 2016</span></span>                      | <span data-ttu-id="d1e7f-171">RemoteSigned</span><span class="sxs-lookup"><span data-stu-id="d1e7f-171">Remote Signed</span></span>            |
| <span data-ttu-id="d1e7f-172">Windows 10</span><span class="sxs-lookup"><span data-stu-id="d1e7f-172">Windows 10</span></span>                       | <span data-ttu-id="d1e7f-173">Restreint</span><span class="sxs-lookup"><span data-stu-id="d1e7f-173">Restricted</span></span>               |

<span data-ttu-id="d1e7f-174">Quel que soit le paramètre de stratégie d’exécution, toutes les commandes PowerShell peuvent être exécutées de manière interactive.</span><span class="sxs-lookup"><span data-stu-id="d1e7f-174">Regardless of the execution policy setting, any PowerShell command can be run interactively.</span></span> <span data-ttu-id="d1e7f-175">La stratégie d’exécution affecte uniquement les commandes qui s’exécutent dans un script.</span><span class="sxs-lookup"><span data-stu-id="d1e7f-175">The execution policy only affects commands running in a script.</span></span> <span data-ttu-id="d1e7f-176">L’applet de commande `Get-ExecutionPolicy` est utilisée pour déterminer le paramètre de stratégie d’exécution qui est appliqué, et l’applet de commande `Set-ExecutionPolicy` est utilisée pour modifier la stratégie d’exécution.</span><span class="sxs-lookup"><span data-stu-id="d1e7f-176">The `Get-ExecutionPolicy` cmdlet is used to determine what the current execution policy setting is and the `Set-ExecutionPolicy` cmdlet is used to change the execution policy.</span></span> <span data-ttu-id="d1e7f-177">Je recommande d’utiliser la stratégie **RemoteSigned**, qui exige que les scripts téléchargés soient signés par un éditeur approuvé pour pouvoir être exécutés.</span><span class="sxs-lookup"><span data-stu-id="d1e7f-177">My recommendation is to use the **RemoteSigned** policy, which requires downloaded scripts to be signed by a trusted publisher in order to be run.</span></span>

<span data-ttu-id="d1e7f-178">Vérifiez la stratégie d’exécution actuelle :</span><span class="sxs-lookup"><span data-stu-id="d1e7f-178">Check the current execution policy:</span></span>

```powershell
Get-ExecutionPolicy
```

```Output
Restricted
```

<span data-ttu-id="d1e7f-179">Les scripts PowerShell ne peuvent pas être exécutés lorsque la stratégie d’exécution est définie sur **Restricted**.</span><span class="sxs-lookup"><span data-stu-id="d1e7f-179">PowerShell scripts can't be run at all when the execution policy is set to **Restricted**.</span></span> <span data-ttu-id="d1e7f-180">Il s’agit du paramètre par défaut sur tous les systèmes d’exploitation clients Windows.</span><span class="sxs-lookup"><span data-stu-id="d1e7f-180">This is the default setting on all Windows client operating systems.</span></span> <span data-ttu-id="d1e7f-181">Pour illustrer ce problème, enregistrez le code suivant sous la forme d’un fichier `.ps1` nommé `Stop-TimeService.ps1`.</span><span class="sxs-lookup"><span data-stu-id="d1e7f-181">To demonstrate the problem, save the following code as a `.ps1` file named `Stop-TimeService.ps1`.</span></span>

```powershell
Get-Service -Name W32Time | Stop-Service -PassThru
```

<span data-ttu-id="d1e7f-182">Cette commande s’exécute de manière interactive sans erreur tant que PowerShell est exécuté avec une élévation des privilèges, en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="d1e7f-182">That command runs interactively without error as long as PowerShell is run elevated as an administrator.</span></span> <span data-ttu-id="d1e7f-183">Toutefois, dès qu’il est enregistré sous la forme d’un fichier de script et que vous essayez de l’exécuter, celui-ci génère une erreur :</span><span class="sxs-lookup"><span data-stu-id="d1e7f-183">But as soon as it's saved as a script file and you try to execute the script, it generates an error:</span></span>

```powershell
.\Stop-TimeService.ps1
```

```Output
.\Stop-TimeService.ps1 : File C:\demo\Stop-TimeService.ps1 cannot be loaded because
running scripts is disabled on this system. For more information, see
about_Execution_Policies at http://go.microsoft.com/fwlink/?LinkID=135170.
At line:1 char:1
+ .\Stop-TimeService.ps1
+
    + CategoryInfo          : SecurityError: (:) [], PSSecurityException
    + FullyQualifiedErrorId : UnauthorizedAccess
```

<span data-ttu-id="d1e7f-184">Notez que l’erreur qui s’affiche dans le jeu de résultats précédent vous indique exactement quel est le problème (l’exécution des scripts a été désactivée sur ce système).</span><span class="sxs-lookup"><span data-stu-id="d1e7f-184">Notice that the error shown in the previous set of results tells you exactly what the problem is (running scripts is disabled on this system).</span></span> <span data-ttu-id="d1e7f-185">Dans PowerShell, quand vous exécutez une commande qui génère un message d’erreur, il est important de lire le message d’erreur au lieu de réexécuter simplement la commande en espérant que celle-ci s’exécute correctement cette fois-ci.</span><span class="sxs-lookup"><span data-stu-id="d1e7f-185">When you run a command in PowerShell that generates an error message, be sure to read the error message instead of just rerunning the command and hoping that it runs successfully.</span></span>

<span data-ttu-id="d1e7f-186">Modifiez la stratégie d’exécution PowerShell pour qu’elle soit signée à distance (RemoteSigned).</span><span class="sxs-lookup"><span data-stu-id="d1e7f-186">Change the PowerShell execution policy to remote signed.</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned
```

```Output
Execution Policy Change
The execution policy helps protect you from scripts that you do not trust. Changing the execution
policy might expose you to the security risks described in the about_Execution_Policies help topic
at http://go.microsoft.com/fwlink/?LinkID=135170. Do you want to change the execution policy?
[Y] Yes [A] Yes to All [N] No [L] No to All [S] Suspend [?] Help (default is "N"):y
```

<span data-ttu-id="d1e7f-187">Lisez l’avertissement qui s’affiche lorsque vous modifiez la stratégie d’exécution.</span><span class="sxs-lookup"><span data-stu-id="d1e7f-187">Be sure to read the warning that's displayed when changing the execution policy.</span></span> <span data-ttu-id="d1e7f-188">Je vous conseille également de consulter la rubrique d’aide [about_Execution_Policies][] afin de bien comprendre ce qu’implique la modification d’une stratégie d’exécution au niveau de la sécurité.</span><span class="sxs-lookup"><span data-stu-id="d1e7f-188">I also recommend taking a look at the [about_Execution_Policies][] help topic to make sure you understand the security implications of changing the execution policy.</span></span>

<span data-ttu-id="d1e7f-189">Maintenant que la stratégie d’exécution a été définie sur **RemoteSigned**, le script `Stop-TimeService.ps1` s’exécute sans erreurs.</span><span class="sxs-lookup"><span data-stu-id="d1e7f-189">Now that the execution policy has been set to **RemoteSigned**, the `Stop-TimeService.ps1` script runs error free.</span></span>

```powershell
.\Stop-TimeService.ps1
```

```Output
Status   Name               DisplayName
------   ----               -----------
Stopped  W32Time            Windows Time
```

<span data-ttu-id="d1e7f-190">Pour ne pas rencontrer de problèmes imprévus, veillez à démarrer le service Temps Windows avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="d1e7f-190">Be sure to start your Windows Time service before continuing otherwise you may run into unforeseen problems.</span></span>

```powershell
Start-Service -Name w32time
```

## <a name="summary"></a><span data-ttu-id="d1e7f-191">Résumé</span><span class="sxs-lookup"><span data-stu-id="d1e7f-191">Summary</span></span>

<span data-ttu-id="d1e7f-192">Dans ce chapitre, vous avez vu comment rechercher et lancer PowerShell, et comment créer un raccourci qui permet d’exécuter PowerShell en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="d1e7f-192">In this chapter, you've learned how to find and launch PowerShell, and how to create a shortcut that launches PowerShell as an administrator.</span></span> <span data-ttu-id="d1e7f-193">Vous avez également découvert la stratégie d’exécution par défaut et vous avez vu comment la modifier.</span><span class="sxs-lookup"><span data-stu-id="d1e7f-193">You've also learned about the default execution policy and how to change it.</span></span>

## <a name="review"></a><span data-ttu-id="d1e7f-194">Révision</span><span class="sxs-lookup"><span data-stu-id="d1e7f-194">Review</span></span>

1. <span data-ttu-id="d1e7f-195">Comment savoir quelle version de PowerShell un ordinateur exécute ?</span><span class="sxs-lookup"><span data-stu-id="d1e7f-195">How do you determine what PowerShell version a computer is running?</span></span>
1. <span data-ttu-id="d1e7f-196">Pourquoi est-il important de lancer PowerShell avec une élévation de privilèges en tant qu’administrateur ?</span><span class="sxs-lookup"><span data-stu-id="d1e7f-196">Why is it important to launch PowerShell elevated as an administrator?</span></span>
1. <span data-ttu-id="d1e7f-197">Comment déterminer la stratégie d’exécution PowerShell actuellement appliquée ?</span><span class="sxs-lookup"><span data-stu-id="d1e7f-197">How do you determine the current PowerShell execution policy?</span></span>
1. <span data-ttu-id="d1e7f-198">Que permet d’éviter la stratégie d’exécution PowerShell par défaut sur les ordinateurs clients Windows ?</span><span class="sxs-lookup"><span data-stu-id="d1e7f-198">What does the default PowerShell execution policy on Windows client computers prevent from occurring?</span></span>
1. <span data-ttu-id="d1e7f-199">Comment modifier la stratégie d’exécution PowerShell ?</span><span class="sxs-lookup"><span data-stu-id="d1e7f-199">How do you change the PowerShell execution policy?</span></span>

## <a name="recommended-reading"></a><span data-ttu-id="d1e7f-200">Lecture recommandée</span><span class="sxs-lookup"><span data-stu-id="d1e7f-200">Recommended Reading</span></span>

<span data-ttu-id="d1e7f-201">Si vous souhaitez en savoir plus sur les sujets abordés dans ce chapitre, je vous conseille de lire les rubriques d’aide PowerShell suivantes.</span><span class="sxs-lookup"><span data-stu-id="d1e7f-201">For those who want to know more information about the topics covered in this chapter, I recommend reading the following PowerShell help topics.</span></span>

- <span data-ttu-id="d1e7f-202">[about_Automatic_Variables][]</span><span class="sxs-lookup"><span data-stu-id="d1e7f-202">[about_Automatic_Variables][]</span></span>
- <span data-ttu-id="d1e7f-203">[about_Hash_Tables][]</span><span class="sxs-lookup"><span data-stu-id="d1e7f-203">[about_Hash_Tables][]</span></span>
- <span data-ttu-id="d1e7f-204">[about_Execution_Policies][]</span><span class="sxs-lookup"><span data-stu-id="d1e7f-204">[about_Execution_Policies][]</span></span>

<span data-ttu-id="d1e7f-205">Dans le chapitre suivant, vous allez découvrir la détectabilité des commandes dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d1e7f-205">In the next chapter, you'll learn about the discoverability of commands in PowerShell.</span></span> <span data-ttu-id="d1e7f-206">L’un des sujets abordés sera la mise à jour de PowerShell dans le but de rendre les rubriques d’aide consultables directement dans PowerShell au lieu d’avoir à les lire sur Internet.</span><span class="sxs-lookup"><span data-stu-id="d1e7f-206">One of the things that will be covered is how to update PowerShell so those help topics can be viewed right from within PowerShell instead of having to view them on the internet.</span></span>

<!-- link references -->
[about_Automatic_Variables]: /powershell/module/microsoft.powershell.core/about/about_automatic_variables
[about_Hash_Tables]: /powershell/module/microsoft.powershell.core/about/about_hash_tables
[about_Execution_Policies]: /powershell/module/microsoft.powershell.core/about/about_execution_policies
[Mise à niveau des instances Windows PowerShell existantes]: /powershell/scripting/windows-powershell/install/installing-windows-powershell#upgrading-existing-windows-powershell
[Upgrading existing Windows PowerShell]: /powershell/scripting/windows-powershell/install/installing-windows-powershell#upgrading-existing-windows-powershell
[Installation de PowerShell]: /powershell/scripting/install/installing-powershell
[Installing PowerShell]: /powershell/scripting/install/installing-powershell
[Démarrage de Windows PowerShell]: /powershell/scripting/windows-powershell/starting-windows-powershell
[Starting Windows PowerShell]: /powershell/scripting/windows-powershell/starting-windows-powershell
