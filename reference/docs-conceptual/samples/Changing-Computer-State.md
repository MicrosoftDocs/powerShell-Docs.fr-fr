---
ms.date: 12/23/2019
keywords: powershell,applet de commande
title: Changement de l’état de l’ordinateur
description: Cet exemple montre comment utiliser des commandes externes dans PowerShell pour gérer la configuration d’un ordinateur.
ms.openlocfilehash: 341f29f24d7e4bd341ccc0954b16d4b75880678b
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500672"
---
# <a name="changing-computer-state"></a><span data-ttu-id="4d22b-104">Changement de l’état de l’ordinateur</span><span class="sxs-lookup"><span data-stu-id="4d22b-104">Changing Computer State</span></span>

<span data-ttu-id="4d22b-105">Pour réinitialiser un ordinateur dans PowerShell, utilisez un outil en ligne de commande standard, ou WMI ou une classe CIM.</span><span class="sxs-lookup"><span data-stu-id="4d22b-105">To reset a computer in PowerShell, use either a standard command-line tool, WMI, or a CIM class.</span></span>
<span data-ttu-id="4d22b-106">Même si vous utilisez PowerShell uniquement pour exécuter l’outil, apprendre à modifier l’état d’alimentation d’un ordinateur dans PowerShell permet de comprendre certains aspects importants de l’utilisation d’outils externes dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4d22b-106">Although you are using PowerShell only to run the tool, learning how to change a computer's power state in PowerShell illustrates some of the important details about working with external tools in PowerShell.</span></span>

## <a name="locking-a-computer"></a><span data-ttu-id="4d22b-107">Verrouillage d’un ordinateur</span><span class="sxs-lookup"><span data-stu-id="4d22b-107">Locking a Computer</span></span>

<span data-ttu-id="4d22b-108">La seule façon de verrouiller un ordinateur directement avec les outils disponibles standards consiste à appeler la fonction **LockWorkstation()** dans **user32.dll** :</span><span class="sxs-lookup"><span data-stu-id="4d22b-108">The only way to lock a computer directly with the standard available tools is to call the **LockWorkstation()** function in **user32.dll** :</span></span>

```powershell
rundll32.exe user32.dll,LockWorkStation
```

<span data-ttu-id="4d22b-109">Cette commande verrouille immédiatement la station de travail.</span><span class="sxs-lookup"><span data-stu-id="4d22b-109">This command immediately locks the workstation.</span></span> <span data-ttu-id="4d22b-110">Elle utilise **rundll32.exe** , qui exécute des DLL Windows (et enregistre leurs bibliothèques en vue d’une réutilisation) pour exécuter `user32.dll`, une bibliothèque de fonctions de gestion de Windows.</span><span class="sxs-lookup"><span data-stu-id="4d22b-110">It uses **rundll32.exe** , which runs Windows DLLs (and saves their libraries for repeated use) to run `user32.dll`, a library of Windows management functions.</span></span>

<span data-ttu-id="4d22b-111">Lorsque vous verrouillez une station de travail alors que l’option Changement rapide d’utilisateur est activée, par exemple sous Windows XP, l’ordinateur affiche l’écran d’ouverture de session utilisateur au lieu de lancer l’économiseur d’écran de l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="4d22b-111">When you lock a workstation while Fast User Switching is enabled, such as on Windows XP, the computer displays the user logon screen rather than starting the current user's screensaver.</span></span>

<span data-ttu-id="4d22b-112">Pour arrêter des sessions particulières sur un serveur Terminal Server, utilisez l’outil en ligne de commande **tsshutdn.exe** .</span><span class="sxs-lookup"><span data-stu-id="4d22b-112">To shut down particular sessions on a Terminal Server, use the **tsshutdn.exe** command-line tool.</span></span>

## <a name="logging-off-the-current-session"></a><span data-ttu-id="4d22b-113">Déconnexion de la session en cours</span><span class="sxs-lookup"><span data-stu-id="4d22b-113">Logging Off the Current Session</span></span>

<span data-ttu-id="4d22b-114">Pour vous déconnecter d’une session sur le système local, vous pouvez utiliser différentes techniques.</span><span class="sxs-lookup"><span data-stu-id="4d22b-114">You can use several different techniques to log off of a session on the local system.</span></span> <span data-ttu-id="4d22b-115">La solution la plus simple consiste à utiliser l’outil en ligne de commande Bureau à distance/Services Terminal Server, **logoff.exe** (pour plus d’informations, à l’invite PowerShell, tapez `logoff /?`).</span><span class="sxs-lookup"><span data-stu-id="4d22b-115">The simplest way is to use the Remote Desktop/Terminal Services command-line tool, **logoff.exe** (For details, at the PowerShell prompt, type `logoff /?`).</span></span> <span data-ttu-id="4d22b-116">Pour fermer la session active, tapez `logoff` sans argument.</span><span class="sxs-lookup"><span data-stu-id="4d22b-116">To log off the current active session, type `logoff` with no arguments.</span></span>

<span data-ttu-id="4d22b-117">Vous pouvez également recouvrir à l’outil **shutdown.exe** avec son option logoff :</span><span class="sxs-lookup"><span data-stu-id="4d22b-117">You can also use the **shutdown.exe** tool with its logoff option:</span></span>

```powershell
shutdown.exe -l
```

<span data-ttu-id="4d22b-118">Une autre option consiste à utiliser WMI.</span><span class="sxs-lookup"><span data-stu-id="4d22b-118">Another option is to use WMI.</span></span> <span data-ttu-id="4d22b-119">La classe **Win32_OperatingSystem** dispose d’une méthode **Arrêt** .</span><span class="sxs-lookup"><span data-stu-id="4d22b-119">The **Win32_OperatingSystem** class has a **Shutdown** method.</span></span>
<span data-ttu-id="4d22b-120">L’appel de la méthode avec l’indicateur 0 déclenche la fermeture de session :</span><span class="sxs-lookup"><span data-stu-id="4d22b-120">Invoking the method with the 0 flag initiates logoff:</span></span>

<span data-ttu-id="4d22b-121">Pour plus d’informations sur la méthode **Arrêt** , consultez la [méthode Arrêt de la classe Win32_OperatingSystem](/windows/win32/cimwin32prov/shutdown-method-in-class-win32-operatingsystem)</span><span class="sxs-lookup"><span data-stu-id="4d22b-121">For more information about the **Shutdown** method, see [Shutdown method of the Win32_OperatingSystem class](/windows/win32/cimwin32prov/shutdown-method-in-class-win32-operatingsystem)</span></span>

```powershell
Get-CimInstance -Classname Win32_OperatingSystem | Invoke-CimMethod -MethodName Shutdown
```

## <a name="shutting-down-or-restarting-a-computer"></a><span data-ttu-id="4d22b-122">Arrêt ou redémarrage d’un ordinateur</span><span class="sxs-lookup"><span data-stu-id="4d22b-122">Shutting Down or Restarting a Computer</span></span>

<span data-ttu-id="4d22b-123">L’arrêt et le redémarrage d’ordinateurs sont généralement des tâches de même type.</span><span class="sxs-lookup"><span data-stu-id="4d22b-123">Shutting down and restarting computers are generally the same types of task.</span></span> <span data-ttu-id="4d22b-124">Les outils permettant d’arrêter un ordinateur permettent généralement aussi de le redémarrer, et inversement.</span><span class="sxs-lookup"><span data-stu-id="4d22b-124">Tools that shut down a computer will generally restart it as well—and vice versa.</span></span> <span data-ttu-id="4d22b-125">Deux options simples permettent de redémarrer un ordinateur à partir de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4d22b-125">There are two straightforward options for restarting a computer from PowerShell.</span></span> <span data-ttu-id="4d22b-126">Utilisez **tsshutdn.exe** ou **shutdown.exe** avec des arguments appropriés.</span><span class="sxs-lookup"><span data-stu-id="4d22b-126">Use either **tsshutdn.exe** or **shutdown.exe** with appropriate arguments.</span></span> <span data-ttu-id="4d22b-127">Vous pouvez obtenir des informations d’utilisation détaillées à partir de `tsshutdn.exe /?` ou `shutdown.exe /?`.</span><span class="sxs-lookup"><span data-stu-id="4d22b-127">You can get detailed usage information from `tsshutdn.exe /?` or `shutdown.exe /?`.</span></span>

<span data-ttu-id="4d22b-128">Vous pouvez également exécuter des opérations d’arrêt et de redémarrage directement depuis PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4d22b-128">You can also perform shutdown and restart operations directly from PowerShell as well.</span></span>

<span data-ttu-id="4d22b-129">Pour arrêter l’ordinateur, utilisez la commande Stop-Computer</span><span class="sxs-lookup"><span data-stu-id="4d22b-129">To shut down the computer, use the Stop-Computer command</span></span>

```powershell
Stop-Computer
```

<span data-ttu-id="4d22b-130">Pour redémarrer le système d’exploitation, utilisez la commande Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="4d22b-130">To restart the operating system, use the Restart-Computer command</span></span>

```powershell
Restart-Computer
```

<span data-ttu-id="4d22b-131">Pour forcer un redémarrage immédiat de l’ordinateur, utilisez le paramètre -Force.</span><span class="sxs-lookup"><span data-stu-id="4d22b-131">To force an immediate restart of the computer, use the -Force parameter.</span></span>

```powershell
Restart-Computer -Force
```
