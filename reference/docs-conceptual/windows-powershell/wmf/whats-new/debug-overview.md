---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
title: Améliorations apportées au débogage de script PowerShell
description: WMF 5.0 ajoute de nouvelles fonctionnalités de débogage à Windows PowerShell.
ms.openlocfilehash: 5703343e1b85024931638e8b04a09f7208ea123c
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92646729"
---
# <a name="improvements-in-powershell-script-debugging"></a><span data-ttu-id="57b6b-104">Améliorations apportées au débogage de script PowerShell</span><span class="sxs-lookup"><span data-stu-id="57b6b-104">Improvements in PowerShell Script Debugging</span></span>

<span data-ttu-id="57b6b-105">PowerShell 5.0 intègre plusieurs améliorations qui perfectionnent l’expérience de débogage.</span><span class="sxs-lookup"><span data-stu-id="57b6b-105">PowerShell 5.0 includes several improvements that enhance the debugging experience.</span></span>

## <a name="break-all"></a><span data-ttu-id="57b6b-106">Interrompre tout</span><span class="sxs-lookup"><span data-stu-id="57b6b-106">Break All</span></span>

<span data-ttu-id="57b6b-107">La console PowerShell et PowerShell ISE permettent à présent d’interrompre le débogueur pour exécuter des scripts.</span><span class="sxs-lookup"><span data-stu-id="57b6b-107">The PowerShell console and PowerShell ISE now allow you to break into the debugger for running scripts.</span></span> <span data-ttu-id="57b6b-108">Cela fonctionne dans les sessions locales et distantes.</span><span class="sxs-lookup"><span data-stu-id="57b6b-108">This works in both local and remote sessions.</span></span>

<span data-ttu-id="57b6b-109">Dans la console, appuyez sur <kbd>Ctrl</kbd>+<kbd>Pause</kbd>.</span><span class="sxs-lookup"><span data-stu-id="57b6b-109">In the console, press <kbd>Ctrl</kbd>+<kbd>Break</kbd>.</span></span>

<span data-ttu-id="57b6b-110">Dans ISE, appuyez sur <kbd>Ctrl</kbd>+<kbd>B</kbd> ou utilisez la commande de menu **Déboguer -> Tout interrompre**.</span><span class="sxs-lookup"><span data-stu-id="57b6b-110">In ISE, press <kbd>Ctrl</kbd>+<kbd>B</kbd>, or use the **Debug -> Break All** menu command.</span></span>

## <a name="remote-debugging-and-remote-file-editing-in-powershell-ise"></a><span data-ttu-id="57b6b-111">Débogage à distance et modification de fichiers à distance dans PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="57b6b-111">Remote debugging and remote file editing in PowerShell ISE</span></span>

<span data-ttu-id="57b6b-112">PowerShell ISE permet à présent d’ouvrir et de modifier des fichiers dans une session à distance en exécutant la commande PSEdit.</span><span class="sxs-lookup"><span data-stu-id="57b6b-112">PowerShell ISE now lets you open and edit files in a remote session by running the PSEdit command.</span></span>
<span data-ttu-id="57b6b-113">Par exemple, vous pouvez ouvrir un fichier pour le modifier à partir de la ligne de commande dans une session distante en procédant comme suit :</span><span class="sxs-lookup"><span data-stu-id="57b6b-113">For example, you can open a file for editing from the command line in a remote session as follows:</span></span>

```powershell
[RemoteComputer1]: PS C:\> PSEdit C:\DebugDemoScripts\Test-GetMutex.ps1
```

<span data-ttu-id="57b6b-114">Par ailleurs, vous pouvez maintenant modifier et enregistrer les modifications dans un fichier distant qui s’ouvre automatiquement dans PowerShell ISE quand vous atteignez un point d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="57b6b-114">In addition, you can now edit and save changes in a remote file that is automatically opened in PowerShell ISE when you hit a breakpoint.</span></span> <span data-ttu-id="57b6b-115">Désormais, vous pouvez déboguer un fichier de script qui s’exécute sur un ordinateur distant, modifier le fichier pour corriger une erreur puis réexécuter le script modifié.</span><span class="sxs-lookup"><span data-stu-id="57b6b-115">Now, you can debug a script file that is running on a remote computer, edit the file to fix an error, and then rerun the modified script.</span></span>

## <a name="advanced-script-debugging"></a><span data-ttu-id="57b6b-116">Débogage de script avancé</span><span class="sxs-lookup"><span data-stu-id="57b6b-116">Advanced Script Debugging</span></span>

<span data-ttu-id="57b6b-117">Il existe de nouvelles fonctionnalités avancées de débogage qui permettent de joindre n’importe quel processus de l’ordinateur local ayant chargé PowerShell, et d’y déboguer des instances d’exécution.</span><span class="sxs-lookup"><span data-stu-id="57b6b-117">There are new, advanced debugging features that let you attach to any local computer process that has loaded PowerShell, and debug arbitrary runspaces in that process.</span></span>

### <a name="runspace-debugging"></a><span data-ttu-id="57b6b-118">Débogage d’instance d’exécution</span><span class="sxs-lookup"><span data-stu-id="57b6b-118">Runspace Debugging</span></span>

<span data-ttu-id="57b6b-119">De nouvelles cmdlets permettent de lister les instances d’exécution actives dans un processus et de joindre la console PowerShell ou le débogueur PowerShell ISE à l’une d’entre elles pour le débogage de script :</span><span class="sxs-lookup"><span data-stu-id="57b6b-119">New cmdlets have been added that let you list current runspaces in a process, and attach the PowerShell console or PowerShell ISE debugger to that runspace for script debugging:</span></span>

- <span data-ttu-id="57b6b-120">Get-Runspace</span><span class="sxs-lookup"><span data-stu-id="57b6b-120">Get-Runspace</span></span>
- <span data-ttu-id="57b6b-121">Debug-Runspace</span><span class="sxs-lookup"><span data-stu-id="57b6b-121">Debug-Runspace</span></span>
- <span data-ttu-id="57b6b-122">Enable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="57b6b-122">Enable-RunspaceDebug</span></span>
- <span data-ttu-id="57b6b-123">Disable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="57b6b-123">Disable-RunspaceDebug</span></span>
- <span data-ttu-id="57b6b-124">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="57b6b-124">Get-RunspaceDebug</span></span>

### <a name="attach-to-process-hosting-powershell"></a><span data-ttu-id="57b6b-125">Joindre au processus hébergeant PowerShell</span><span class="sxs-lookup"><span data-stu-id="57b6b-125">Attach to Process hosting PowerShell</span></span>

<span data-ttu-id="57b6b-126">Il est à présent possible de joindre n’importe quel processus de l’ordinateur ayant chargé PowerShell.</span><span class="sxs-lookup"><span data-stu-id="57b6b-126">You can now attach to any computer process that has PowerShell loaded.</span></span> <span data-ttu-id="57b6b-127">Pour cela, ouvrez une session interactive avec le processus hôte.</span><span class="sxs-lookup"><span data-stu-id="57b6b-127">You do this by entering into an interactive session with the host process.</span></span> <span data-ttu-id="57b6b-128">Pour plus d'informations, consultez les pages suivantes :</span><span class="sxs-lookup"><span data-stu-id="57b6b-128">For more information, see:</span></span>

- [<span data-ttu-id="57b6b-129">Enter-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="57b6b-129">Enter-PSHostProcess</span></span>](/powershell/module/Microsoft.PowerShell.Core/Enter-PSHostProcess)
- [<span data-ttu-id="57b6b-130">Exit-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="57b6b-130">Exit-PSHostProcess</span></span>](/powershell/module/Microsoft.PowerShell.Core/Exit-PSHostProcess)
