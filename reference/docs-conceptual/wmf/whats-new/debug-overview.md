---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
title: Améliorations apportées au débogage de script PowerShell
ms.openlocfilehash: f1771a451ba671da2371fcfc95374e6131573ddc
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "71147809"
---
# <a name="improvements-in-powershell-script-debugging"></a><span data-ttu-id="129dc-103">Améliorations apportées au débogage de script PowerShell</span><span class="sxs-lookup"><span data-stu-id="129dc-103">Improvements in PowerShell Script Debugging</span></span>

<span data-ttu-id="129dc-104">PowerShell 5.0 intègre plusieurs améliorations qui perfectionnent l’expérience de débogage.</span><span class="sxs-lookup"><span data-stu-id="129dc-104">PowerShell 5.0 includes several improvements that enhance the debugging experience.</span></span>

## <a name="break-all"></a><span data-ttu-id="129dc-105">Interrompre tout</span><span class="sxs-lookup"><span data-stu-id="129dc-105">Break All</span></span>

<span data-ttu-id="129dc-106">La console PowerShell et PowerShell ISE permettent à présent d’interrompre le débogueur pour exécuter des scripts.</span><span class="sxs-lookup"><span data-stu-id="129dc-106">The PowerShell console and PowerShell ISE now allow you to break into the debugger for running scripts.</span></span> <span data-ttu-id="129dc-107">Cela fonctionne dans les sessions locales et distantes.</span><span class="sxs-lookup"><span data-stu-id="129dc-107">This works in both local and remote sessions.</span></span>

<span data-ttu-id="129dc-108">Dans la console, appuyez sur <kbd>Ctrl</kbd>+<kbd>Pause</kbd>.</span><span class="sxs-lookup"><span data-stu-id="129dc-108">In the console, press <kbd>Ctrl</kbd>+<kbd>Break</kbd>.</span></span>

<span data-ttu-id="129dc-109">Dans ISE, appuyez sur <kbd>Ctrl</kbd>+<kbd>B</kbd> ou utilisez la commande de menu **Déboguer -> Tout interrompre**.</span><span class="sxs-lookup"><span data-stu-id="129dc-109">In ISE, press <kbd>Ctrl</kbd>+<kbd>B</kbd>, or use the **Debug -> Break All** menu command.</span></span>

## <a name="remote-debugging-and-remote-file-editing-in-powershell-ise"></a><span data-ttu-id="129dc-110">Débogage à distance et modification de fichiers à distance dans PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="129dc-110">Remote debugging and remote file editing in PowerShell ISE</span></span>

<span data-ttu-id="129dc-111">PowerShell ISE permet à présent d’ouvrir et de modifier des fichiers dans une session à distance en exécutant la commande PSEdit.</span><span class="sxs-lookup"><span data-stu-id="129dc-111">PowerShell ISE now lets you open and edit files in a remote session by running the PSEdit command.</span></span>
<span data-ttu-id="129dc-112">Par exemple, vous pouvez ouvrir un fichier pour le modifier à partir de la ligne de commande dans une session distante en procédant comme suit :</span><span class="sxs-lookup"><span data-stu-id="129dc-112">For example, you can open a file for editing from the command line in a remote session as follows:</span></span>

```powershell
[RemoteComputer1]: PS C:\> PSEdit C:\DebugDemoScripts\Test-GetMutex.ps1
```

<span data-ttu-id="129dc-113">Par ailleurs, vous pouvez maintenant modifier et enregistrer les modifications dans un fichier distant qui s’ouvre automatiquement dans PowerShell ISE quand vous atteignez un point d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="129dc-113">In addition, you can now edit and save changes in a remote file that is automatically opened in PowerShell ISE when you hit a breakpoint.</span></span> <span data-ttu-id="129dc-114">Désormais, vous pouvez déboguer un fichier de script qui s’exécute sur un ordinateur distant, modifier le fichier pour corriger une erreur puis réexécuter le script modifié.</span><span class="sxs-lookup"><span data-stu-id="129dc-114">Now, you can debug a script file that is running on a remote computer, edit the file to fix an error, and then rerun the modified script.</span></span>

## <a name="advanced-script-debugging"></a><span data-ttu-id="129dc-115">Débogage de script avancé</span><span class="sxs-lookup"><span data-stu-id="129dc-115">Advanced Script Debugging</span></span>

<span data-ttu-id="129dc-116">Il existe de nouvelles fonctionnalités avancées de débogage qui permettent de joindre n’importe quel processus de l’ordinateur local ayant chargé PowerShell, et d’y déboguer des instances d’exécution.</span><span class="sxs-lookup"><span data-stu-id="129dc-116">There are new, advanced debugging features that let you attach to any local computer process that has loaded PowerShell, and debug arbitrary runspaces in that process.</span></span>

### <a name="runspace-debugging"></a><span data-ttu-id="129dc-117">Débogage d’instance d’exécution</span><span class="sxs-lookup"><span data-stu-id="129dc-117">Runspace Debugging</span></span>

<span data-ttu-id="129dc-118">De nouvelles cmdlets permettent de lister les instances d’exécution actives dans un processus et de joindre la console PowerShell ou le débogueur PowerShell ISE à l’une d’entre elles pour le débogage de script :</span><span class="sxs-lookup"><span data-stu-id="129dc-118">New cmdlets have been added that let you list current runspaces in a process, and attach the PowerShell console or PowerShell ISE debugger to that runspace for script debugging:</span></span>

- <span data-ttu-id="129dc-119">Get-Runspace</span><span class="sxs-lookup"><span data-stu-id="129dc-119">Get-Runspace</span></span>
- <span data-ttu-id="129dc-120">Debug-Runspace</span><span class="sxs-lookup"><span data-stu-id="129dc-120">Debug-Runspace</span></span>
- <span data-ttu-id="129dc-121">Enable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="129dc-121">Enable-RunspaceDebug</span></span>
- <span data-ttu-id="129dc-122">Disable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="129dc-122">Disable-RunspaceDebug</span></span>
- <span data-ttu-id="129dc-123">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="129dc-123">Get-RunspaceDebug</span></span>

### <a name="attach-to-process-hosting-powershell"></a><span data-ttu-id="129dc-124">Joindre au processus hébergeant PowerShell</span><span class="sxs-lookup"><span data-stu-id="129dc-124">Attach to Process hosting PowerShell</span></span>

<span data-ttu-id="129dc-125">Il est à présent possible de joindre n’importe quel processus de l’ordinateur ayant chargé PowerShell.</span><span class="sxs-lookup"><span data-stu-id="129dc-125">You can now attach to any computer process that has PowerShell loaded.</span></span> <span data-ttu-id="129dc-126">Pour cela, ouvrez une session interactive avec le processus hôte.</span><span class="sxs-lookup"><span data-stu-id="129dc-126">You do this by entering into an interactive session with the host process.</span></span> <span data-ttu-id="129dc-127">Pour plus d’informations, voir :</span><span class="sxs-lookup"><span data-stu-id="129dc-127">For more information, see:</span></span>

- [<span data-ttu-id="129dc-128">Enter-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="129dc-128">Enter-PSHostProcess</span></span>](/powershell/module/Microsoft.PowerShell.Core/Enter-PSHostProcess)
- [<span data-ttu-id="129dc-129">Exit-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="129dc-129">Exit-PSHostProcess</span></span>](/powershell/module/Microsoft.PowerShell.Core/Exit-PSHostProcess)
