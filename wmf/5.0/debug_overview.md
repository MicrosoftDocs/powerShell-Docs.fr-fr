---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: 9ead27fd5d4f146e9062488c1c8cc22a073b922e
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34187100"
---
# <a name="improvements-in-powershell-script-debugging"></a><span data-ttu-id="7a245-102">Améliorations apportées au débogage de script PowerShell</span><span class="sxs-lookup"><span data-stu-id="7a245-102">Improvements in PowerShell Script Debugging</span></span>

<span data-ttu-id="7a245-103">Un certain nombre d’améliorations ont été apportées à PowerShell 5.0 pour améliorer l’expérience de débogage :</span><span class="sxs-lookup"><span data-stu-id="7a245-103">A number of improvements were made in PowerShell 5.0 to enhance the debugging experience:</span></span>

## <a name="break-all"></a><span data-ttu-id="7a245-104">Interrompre tout</span><span class="sxs-lookup"><span data-stu-id="7a245-104">Break All</span></span>

<span data-ttu-id="7a245-105">La console PowerShell et Windows PowerShell ISE vous permettent désormais de vous arrêter dans le débogueur pour exécuter des scripts.</span><span class="sxs-lookup"><span data-stu-id="7a245-105">The PowerShell console and Windows PowerShell ISE now allow you to break into the debugger for running scripts.</span></span> <span data-ttu-id="7a245-106">Cela fonctionne dans les sessions locales et distantes.</span><span class="sxs-lookup"><span data-stu-id="7a245-106">This works in both local and remote sessions.</span></span>

<span data-ttu-id="7a245-107">Dans la console, appuyez sur **Ctrl+Pause**.</span><span class="sxs-lookup"><span data-stu-id="7a245-107">In the console, press **Ctrl+Break**.</span></span>

<span data-ttu-id="7a245-108">Dans ISE, appuyez sur **Ctrl+B** ou utilisez la commande de menu **Déboguer -> Interrompre tout**.</span><span class="sxs-lookup"><span data-stu-id="7a245-108">In ISE, press **Ctrl+B**, or use the **Debug -> Break All** menu command.</span></span>

## <a name="remote-debugging-and-remote-file-editing-in-windows-powershell-ise"></a><span data-ttu-id="7a245-109">Débogage à distance et modification de fichiers à distance dans Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="7a245-109">Remote debugging and remote file editing in Windows PowerShell ISE</span></span>

<span data-ttu-id="7a245-110">Windows PowerShell ISE vous permet désormais d’ouvrir et de modifier des fichiers dans une session à distance en exécutant la commande PSEdit.</span><span class="sxs-lookup"><span data-stu-id="7a245-110">Windows PowerShell ISE now lets you open and edit files in a remote session by running the PSEdit command.</span></span>
<span data-ttu-id="7a245-111">Par exemple, vous pouvez ouvrir un fichier pour le modifier à partir de la ligne de commande dans une session distante en procédant comme suit :</span><span class="sxs-lookup"><span data-stu-id="7a245-111">For example, you can open a file for editing from the command line in a remote session as follows:</span></span>

```powershell
[RemoteComputer1]: PS C:\> PSEdit C:\DebugDemoScripts\Test-GetMutex.ps1
```

<span data-ttu-id="7a245-112">De plus, vous pouvez maintenant modifier et enregistrer les modifications dans un fichier distant qui est ouvert automatiquement dans Windows PowerShell ISE quand vous atteignez un point d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="7a245-112">In addition, you can now edit and save changes in a remote file that is automatically opened in Windows PowerShell ISE when you hit a breakpoint.</span></span>
<span data-ttu-id="7a245-113">Désormais, vous pouvez déboguer un fichier de script qui s’exécute sur un ordinateur distant, modifier le fichier pour corriger une erreur puis réexécuter le script modifié.</span><span class="sxs-lookup"><span data-stu-id="7a245-113">Now, you can debug a script file that is running on a remote computer, edit the file to fix an error, and then rerun the modified script.</span></span>

## <a name="advanced-script-debugging"></a><span data-ttu-id="7a245-114">Débogage de script avancé</span><span class="sxs-lookup"><span data-stu-id="7a245-114">Advanced Script Debugging</span></span>

<span data-ttu-id="7a245-115">Il existe de nouvelles fonctionnalités de débogage avancées qui vous permettent de joindre tout processus de l’ordinateur local ayant chargé Windows PowerShell, et de déboguer des instances d’exécution arbitraires dans ce processus.</span><span class="sxs-lookup"><span data-stu-id="7a245-115">There are new, advanced debugging features that let you attach to any local computer process that has loaded Windows PowerShell, and debug arbitrary runspaces in that process.</span></span>

### <a name="runspace-debugging"></a><span data-ttu-id="7a245-116">Débogage d’instance d’exécution</span><span class="sxs-lookup"><span data-stu-id="7a245-116">Runspace Debugging</span></span>

<span data-ttu-id="7a245-117">De nouvelles applets de commande permettent de répertorier les instances en cours d’exécution dans un processus et d’attacher la console Windows PowerShell ou le débogueur ISE à cette instance d’exécution pour le débogage de script :</span><span class="sxs-lookup"><span data-stu-id="7a245-117">New cmdlets have been added that let you list current runspaces in a process, and attach the Windows PowerShell console or ISE debugger to that runspace for script debugging:</span></span>

-   <span data-ttu-id="7a245-118">Get-Runspace</span><span class="sxs-lookup"><span data-stu-id="7a245-118">Get-Runspace</span></span>
-   <span data-ttu-id="7a245-119">Debug-Runspace</span><span class="sxs-lookup"><span data-stu-id="7a245-119">Debug-Runspace</span></span>
-   <span data-ttu-id="7a245-120">Enable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="7a245-120">Enable-RunspaceDebug</span></span>
-   <span data-ttu-id="7a245-121">Disable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="7a245-121">Disable-RunspaceDebug</span></span>
-   <span data-ttu-id="7a245-122">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="7a245-122">Get-RunspaceDebug</span></span>

### <a name="attach-to-process-hosting-powershell"></a><span data-ttu-id="7a245-123">Joindre au processus hébergeant PowerShell</span><span class="sxs-lookup"><span data-stu-id="7a245-123">Attach to Process hosting PowerShell</span></span>

<span data-ttu-id="7a245-124">Vous pouvez désormais joindre n’importe quel processus de l’ordinateur ayant chargé Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7a245-124">You can now attach to any computer process that has Windows PowerShell loaded.</span></span> <span data-ttu-id="7a245-125">Pour cela, vous devez établir une session interactive avec le processus, comme vous le faites pour établir une session interactive à distance en exécutant l’applet de commande Enter-PSSession :</span><span class="sxs-lookup"><span data-stu-id="7a245-125">You do this by entering into an interactive session with the process, similarly to how you enter into an interactive remote session by running the Enter-PSSession cmdlet:</span></span>

-   <span data-ttu-id="7a245-126">Enter-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="7a245-126">Enter-PSHostProcess</span></span>
-   <span data-ttu-id="7a245-127">Exit-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="7a245-127">Exit-PSHostProcess</span></span>
