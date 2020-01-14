---
ms.date: 12/23/2019
keywords: powershell,applet de commande
title: Changement de l’état de l’ordinateur
ms.openlocfilehash: 9278df55ba027134a61c8ed4e89b5b839d460b29
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736911"
---
# <a name="changing-computer-state"></a><span data-ttu-id="896a8-103">Changement de l’état de l’ordinateur</span><span class="sxs-lookup"><span data-stu-id="896a8-103">Changing Computer State</span></span>

<span data-ttu-id="896a8-104">Pour réinitialiser un ordinateur dans PowerShell, utilisez un outil en ligne de commande standard ou une classe WMI ou CIM.</span><span class="sxs-lookup"><span data-stu-id="896a8-104">To reset a computer in PowerShell, use either a standard command-line tool, WMI or CIM class.</span></span>
<span data-ttu-id="896a8-105">Même si vous utilisez PowerShell uniquement pour exécuter l’outil, apprendre à modifier l’état d’alimentation d’un ordinateur dans PowerShell permet de comprendre certains aspects importants de l’utilisation d’outils externes dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="896a8-105">Although you are using PowerShell only to run the tool, learning how to change a computer's power state in PowerShell illustrates some of the important details about working with external tools in PowerShell.</span></span>

## <a name="locking-a-computer"></a><span data-ttu-id="896a8-106">Verrouillage d’un ordinateur</span><span class="sxs-lookup"><span data-stu-id="896a8-106">Locking a Computer</span></span>

<span data-ttu-id="896a8-107">La seule façon de verrouiller un ordinateur directement avec les outils disponibles standards consiste à appeler la fonction **LockWorkstation()** dans **user32.dll**:</span><span class="sxs-lookup"><span data-stu-id="896a8-107">The only way to lock a computer directly with the standard available tools is to call the **LockWorkstation()** function in **user32.dll**:</span></span>

```powershell
rundll32.exe user32.dll,LockWorkStation
```

<span data-ttu-id="896a8-108">Cette commande verrouille immédiatement la station de travail.</span><span class="sxs-lookup"><span data-stu-id="896a8-108">This command immediately locks the workstation.</span></span> <span data-ttu-id="896a8-109">Elle utilise **rundll32.exe**, qui exécute des DLL Windows (et enregistre leurs bibliothèques en vue d’une réutilisation) pour exécuter `user32.dll`, une bibliothèque de fonctions de gestion de Windows.</span><span class="sxs-lookup"><span data-stu-id="896a8-109">It uses **rundll32.exe**, which runs Windows DLLs (and saves their libraries for repeated use) to run `user32.dll`, a library of Windows management functions.</span></span>

<span data-ttu-id="896a8-110">Lorsque vous verrouillez une station de travail alors que l’option Changement rapide d’utilisateur est activée, par exemple sous Windows XP, l’ordinateur affiche l’écran d’ouverture de session utilisateur au lieu de lancer l’économiseur d’écran de l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="896a8-110">When you lock a workstation while Fast User Switching is enabled, such as on Windows XP, the computer displays the user logon screen rather than starting the current user's screensaver.</span></span>

<span data-ttu-id="896a8-111">Pour arrêter des sessions particulières sur un serveur Terminal Server, utilisez l’outil en ligne de commande **tsshutdn.exe**.</span><span class="sxs-lookup"><span data-stu-id="896a8-111">To shut down particular sessions on a Terminal Server, use the **tsshutdn.exe** command-line tool.</span></span>

## <a name="logging-off-the-current-session"></a><span data-ttu-id="896a8-112">Déconnexion de la session en cours</span><span class="sxs-lookup"><span data-stu-id="896a8-112">Logging Off the Current Session</span></span>

<span data-ttu-id="896a8-113">Pour vous déconnecter d’une session sur le système local, vous pouvez utiliser différentes techniques.</span><span class="sxs-lookup"><span data-stu-id="896a8-113">You can use several different techniques to log off of a session on the local system.</span></span> <span data-ttu-id="896a8-114">La solution la plus simple consiste à utiliser l’outil en ligne de commande Bureau à distance/Services Terminal Server, **logoff.exe** (pour plus d’informations, à l’invite PowerShell, tapez `logoff /?`).</span><span class="sxs-lookup"><span data-stu-id="896a8-114">The simplest way is to use the Remote Desktop/Terminal Services command-line tool, **logoff.exe** (For details, at the PowerShell prompt, type `logoff /?`).</span></span> <span data-ttu-id="896a8-115">Pour fermer la session active, tapez `logoff` sans argument.</span><span class="sxs-lookup"><span data-stu-id="896a8-115">To log off the current active session, type `logoff` with no arguments.</span></span>

<span data-ttu-id="896a8-116">Vous pouvez également recouvrir à l’outil **shutdown.exe** avec son option logoff :</span><span class="sxs-lookup"><span data-stu-id="896a8-116">You can also use the **shutdown.exe** tool with its logoff option:</span></span>

```powershell
shutdown.exe -l
```

<span data-ttu-id="896a8-117">Une autre option consiste à utiliser WMI.</span><span class="sxs-lookup"><span data-stu-id="896a8-117">Another option is to use WMI.</span></span> <span data-ttu-id="896a8-118">La classe **Win32_OperatingSystem** dispose d’une méthode **Arrêt**.</span><span class="sxs-lookup"><span data-stu-id="896a8-118">The **Win32_OperatingSystem** class has a **Shutdown** method.</span></span>
<span data-ttu-id="896a8-119">L’appel de la méthode avec l’indicateur 0 déclenche la fermeture de session :</span><span class="sxs-lookup"><span data-stu-id="896a8-119">Invoking the method with the 0 flag initiates logoff:</span></span>

<span data-ttu-id="896a8-120">Pour plus d’informations sur la méthode **Arrêt**, consultez la [méthode Arrêt de la classe Win32_OperatingSystem](/windows/win32/cimwin32prov/shutdown-method-in-class-win32-operatingsystem)</span><span class="sxs-lookup"><span data-stu-id="896a8-120">For more information about the **Shutdown** method, see [Shutdown method of the Win32_OperatingSystem class](/windows/win32/cimwin32prov/shutdown-method-in-class-win32-operatingsystem)</span></span>

```powershell
Get-CimInstance -Classname Win32_OperatingSystem | Invoke-CimMethod -MethodName Shutdown
```

## <a name="shutting-down-or-restarting-a-computer"></a><span data-ttu-id="896a8-121">Arrêt ou redémarrage d’un ordinateur</span><span class="sxs-lookup"><span data-stu-id="896a8-121">Shutting Down or Restarting a Computer</span></span>

<span data-ttu-id="896a8-122">L’arrêt et le redémarrage d’ordinateurs sont généralement des tâches de même type.</span><span class="sxs-lookup"><span data-stu-id="896a8-122">Shutting down and restarting computers are generally the same types of task.</span></span> <span data-ttu-id="896a8-123">Les outils permettant d’arrêter un ordinateur permettent généralement aussi de le redémarrer, et inversement.</span><span class="sxs-lookup"><span data-stu-id="896a8-123">Tools that shut down a computer will generally restart it as well—and vice versa.</span></span> <span data-ttu-id="896a8-124">Deux options simples permettent de redémarrer un ordinateur à partir de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="896a8-124">There are two straightforward options for restarting a computer from PowerShell.</span></span> <span data-ttu-id="896a8-125">Utilisez **tsshutdn.exe** ou **shutdown.exe** avec des arguments appropriés.</span><span class="sxs-lookup"><span data-stu-id="896a8-125">Use either **tsshutdn.exe** or **shutdown.exe** with appropriate arguments.</span></span> <span data-ttu-id="896a8-126">Vous pouvez obtenir des informations d’utilisation détaillées à partir de `tsshutdn.exe /?` ou `shutdown.exe /?`.</span><span class="sxs-lookup"><span data-stu-id="896a8-126">You can get detailed usage information from `tsshutdn.exe /?` or `shutdown.exe /?`.</span></span>

<span data-ttu-id="896a8-127">Vous pouvez également exécuter des opérations d’arrêt et de redémarrage directement depuis PowerShell.</span><span class="sxs-lookup"><span data-stu-id="896a8-127">You can also perform shutdown and restart operations directly from PowerShell as well.</span></span>

<span data-ttu-id="896a8-128">Pour arrêter l’ordinateur, utilisez la commande Stop-Computer</span><span class="sxs-lookup"><span data-stu-id="896a8-128">To shut down the computer, use the Stop-Computer command</span></span>

```powershell
Stop-Computer
```

<span data-ttu-id="896a8-129">Pour redémarrer le système d’exploitation, utilisez la commande Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="896a8-129">To restart the operating system, use the Restart-Computer command</span></span>

```powershell
Restart-Computer
```

<span data-ttu-id="896a8-130">Pour forcer un redémarrage immédiat de l’ordinateur, utilisez le paramètre -Force.</span><span class="sxs-lookup"><span data-stu-id="896a8-130">To force an immediate restart of the computer, use the -Force parameter.</span></span>

```powershell
Restart-Computer -Force
```
