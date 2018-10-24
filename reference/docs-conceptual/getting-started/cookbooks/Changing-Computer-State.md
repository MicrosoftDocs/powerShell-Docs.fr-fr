---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Changement de l’état de l’ordinateur
ms.assetid: 8093268b-27f8-4a49-8871-142c5cc33f01
ms.openlocfilehash: f2fadcedaeddfa6f8b9dd4d70738ee062b907d61
ms.sourcegitcommit: 6749f67c32e05999e10deb9d45f90f45ac21a599
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/08/2018
ms.locfileid: "48851081"
---
# <a name="changing-computer-state"></a><span data-ttu-id="89fe3-103">Changement de l’état de l’ordinateur</span><span class="sxs-lookup"><span data-stu-id="89fe3-103">Changing Computer State</span></span>

<span data-ttu-id="89fe3-104">Pour réinitialiser un ordinateur dans Windows PowerShell, utilisez un outil en ligne de commande standard ou une classe WMI.</span><span class="sxs-lookup"><span data-stu-id="89fe3-104">To reset a computer in Windows PowerShell, use either a standard command-line tool or a WMI class.</span></span> <span data-ttu-id="89fe3-105">Même si vous utilisez Windows PowerShell uniquement pour exécuter l’outil, apprendre à modifier l’état d’alimentation d’un ordinateur dans Windows PowerShell permet de comprendre certains aspects importants de l’utilisation d’outils externes dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="89fe3-105">Although you are using Windows PowerShell only to run the tool, learning how to change a computer's power state in Windows PowerShell illustrates some of the important details about working with external tools in Windows PowerShell.</span></span>

### <a name="locking-a-computer"></a><span data-ttu-id="89fe3-106">Verrouillage d’un ordinateur</span><span class="sxs-lookup"><span data-stu-id="89fe3-106">Locking a Computer</span></span>

<span data-ttu-id="89fe3-107">La seule façon de verrouiller un ordinateur directement avec les outils disponibles standards consiste à appeler la fonction **LockWorkstation()** dans **user32.dll**:</span><span class="sxs-lookup"><span data-stu-id="89fe3-107">The only way to lock a computer directly with the standard available tools is to call the **LockWorkstation()** function in **user32.dll**:</span></span>

```
rundll32.exe user32.dll,LockWorkStation
```

<span data-ttu-id="89fe3-108">Cette commande verrouille immédiatement la station de travail.</span><span class="sxs-lookup"><span data-stu-id="89fe3-108">This command immediately locks the workstation.</span></span> <span data-ttu-id="89fe3-109">Elle utilise *rundll32.exe*, qui exécute des DLL Windows (et enregistre leurs bibliothèques en vue d’une réutilisation) pour exécuter user32.dll, une bibliothèque de fonctions de gestion de Windows.</span><span class="sxs-lookup"><span data-stu-id="89fe3-109">It uses *rundll32.exe*, which runs Windows DLLs (and saves their libraries for repeated use) to run user32.dll, a library of Windows management functions.</span></span>

<span data-ttu-id="89fe3-110">Lorsque vous verrouillez une station de travail alors que l’option Changement rapide d’utilisateur est activée, par exemple sous Windows XP, l’ordinateur affiche l’écran d’ouverture de session utilisateur au lieu de lancer l’économiseur d’écran de l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="89fe3-110">When you lock a workstation while Fast User Switching is enabled, such as on Windows XP, the computer displays the user logon screen rather than starting the current user's screensaver.</span></span>

<span data-ttu-id="89fe3-111">Pour arrêter des sessions particulières sur un serveur Terminal Server, utilisez l’outil en ligne de commande **tsshutdn.exe**.</span><span class="sxs-lookup"><span data-stu-id="89fe3-111">To shut down particular sessions on a Terminal Server, use the **tsshutdn.exe** command-line tool.</span></span>

### <a name="logging-off-the-current-session"></a><span data-ttu-id="89fe3-112">Déconnexion de la session en cours</span><span class="sxs-lookup"><span data-stu-id="89fe3-112">Logging Off the Current Session</span></span>

<span data-ttu-id="89fe3-113">Pour vous déconnecter d’une session sur le système local, vous pouvez utiliser différentes techniques.</span><span class="sxs-lookup"><span data-stu-id="89fe3-113">You can use several different techniques to log off of a session on the local system.</span></span> <span data-ttu-id="89fe3-114">La solution la plus simple consiste à utiliser l’outil en ligne de commande Bureau à distance/Services Terminal Server, **logoff.exe** (pour plus d’informations, à l’invite Windows PowerShell, tapez **logoff /?**).</span><span class="sxs-lookup"><span data-stu-id="89fe3-114">The simplest way is to use the Remote Desktop/Terminal Services command-line tool, **logoff.exe** (For details, at the Windows PowerShell prompt, type **logoff /?**).</span></span> <span data-ttu-id="89fe3-115">Pour fermer la session active, tapez **logoff** sans argument.</span><span class="sxs-lookup"><span data-stu-id="89fe3-115">To log off the current active session, type **logoff** with no arguments.</span></span>

<span data-ttu-id="89fe3-116">Vous pouvez également recouvrir à l’outil **shutdown.exe** avec son option logoff :</span><span class="sxs-lookup"><span data-stu-id="89fe3-116">You can also use the **shutdown.exe** tool with its logoff option:</span></span>

```
shutdown.exe -l
```

<span data-ttu-id="89fe3-117">Une troisième option consiste à utiliser WMI.</span><span class="sxs-lookup"><span data-stu-id="89fe3-117">A third option is to use WMI.</span></span> <span data-ttu-id="89fe3-118">La classe Win32_OperatingSystem dispose d’une méthode Win32Shutdown.</span><span class="sxs-lookup"><span data-stu-id="89fe3-118">The Win32_OperatingSystem class has a Win32Shutdown method.</span></span> <span data-ttu-id="89fe3-119">L’appel de la méthode avec l’indicateur 0 déclenche la fermeture de session :</span><span class="sxs-lookup"><span data-stu-id="89fe3-119">Invoking the method with the 0 flag initiates logoff:</span></span>

```powershell
(Get-WmiObject -Class Win32_OperatingSystem -ComputerName .).Win32Shutdown(0)
```

<span data-ttu-id="89fe3-120">Pour plus d’informations et pour découvrir d’autres fonctionnalités de la méthode Win32Shutdown, voir « Méthode Win32Shutdown de la classe Win32_OperatingSystem » dans MSDN.</span><span class="sxs-lookup"><span data-stu-id="89fe3-120">For more information, and to find other features of the Win32Shutdown method, see "Win32Shutdown Method of the Win32_OperatingSystem Class" in MSDN.</span></span>

### <a name="shutting-down-or-restarting-a-computer"></a><span data-ttu-id="89fe3-121">Arrêt ou redémarrage d’un ordinateur</span><span class="sxs-lookup"><span data-stu-id="89fe3-121">Shutting Down or Restarting a Computer</span></span>

<span data-ttu-id="89fe3-122">L’arrêt et le redémarrage d’ordinateurs sont généralement des tâches de même type.</span><span class="sxs-lookup"><span data-stu-id="89fe3-122">Shutting down and restarting computers are generally the same types of task.</span></span> <span data-ttu-id="89fe3-123">Les outils permettant d’arrêter un ordinateur permettent généralement aussi de le redémarrer, et inversement.</span><span class="sxs-lookup"><span data-stu-id="89fe3-123">Tools that shut down a computer will generally restart it as well—and vice versa.</span></span> <span data-ttu-id="89fe3-124">Deux options simples permettent de redémarrer un ordinateur à partir de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="89fe3-124">There are two straightforward options for restarting a computer from Windows PowerShell.</span></span> <span data-ttu-id="89fe3-125">Utilisez Tsshutdn.exe ou Shutdown.exe avec des arguments appropriés.</span><span class="sxs-lookup"><span data-stu-id="89fe3-125">Use either Tsshutdn.exe or Shutdown.exe with appropriate arguments.</span></span> <span data-ttu-id="89fe3-126">Vous pouvez obtenir des informations d’utilisation détaillées à partir de **tsshutdn.exe /?**</span><span class="sxs-lookup"><span data-stu-id="89fe3-126">You can get detailed usage information from **tsshutdn.exe /?**</span></span> <span data-ttu-id="89fe3-127">ou de **shutdown.exe /?**.</span><span class="sxs-lookup"><span data-stu-id="89fe3-127">or **shutdown.exe /?**.</span></span>

<span data-ttu-id="89fe3-128">Vous pouvez également exécuter des opérations d’arrêt et de redémarrage directement depuis Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="89fe3-128">You can also perform shutdown and restart operations directly from Windows PowerShell as well.</span></span>

<span data-ttu-id="89fe3-129">Pour arrêter l’ordinateur, utilisez la commande Stop-Computer</span><span class="sxs-lookup"><span data-stu-id="89fe3-129">To shut down the computer, use the Stop-Computer command</span></span>

```powershell
Stop-Computer
```

<span data-ttu-id="89fe3-130">Pour redémarrer le système d’exploitation, utilisez la commande Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="89fe3-130">To restart the operating system, use the Restart-Computer command</span></span>

```powershell
Restart-Computer
```

<span data-ttu-id="89fe3-131">Pour forcer un redémarrage immédiat de l’ordinateur, utilisez le paramètre -Force.</span><span class="sxs-lookup"><span data-stu-id="89fe3-131">To force an immediate restart of the computer, use the -Force parameter.</span></span>

```powershell
Restart-Computer -Force
```
