---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Changement de l’état de l’ordinateur
ms.openlocfilehash: de3e31e358548943a015b7bba275c4461202b20f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "70386278"
---
# <a name="changing-computer-state"></a>Changement de l’état de l’ordinateur

Pour réinitialiser un ordinateur dans Windows PowerShell, utilisez un outil en ligne de commande standard ou une classe WMI ou CIM. Même si vous utilisez Windows PowerShell uniquement pour exécuter l’outil, apprendre à modifier l’état d’alimentation d’un ordinateur dans Windows PowerShell permet de comprendre certains aspects importants de l’utilisation d’outils externes dans Windows PowerShell.

## <a name="locking-a-computer"></a>Verrouillage d’un ordinateur

La seule façon de verrouiller un ordinateur directement avec les outils disponibles standards consiste à appeler la fonction **LockWorkstation()** dans **user32.dll**:

```
rundll32.exe user32.dll,LockWorkStation
```

Cette commande verrouille immédiatement la station de travail. Elle utilise *rundll32.exe*, qui exécute des DLL Windows (et enregistre leurs bibliothèques en vue d’une réutilisation) pour exécuter user32.dll, une bibliothèque de fonctions de gestion de Windows.

Lorsque vous verrouillez une station de travail alors que l’option Changement rapide d’utilisateur est activée, par exemple sous Windows XP, l’ordinateur affiche l’écran d’ouverture de session utilisateur au lieu de lancer l’économiseur d’écran de l’utilisateur actuel.

Pour arrêter des sessions particulières sur un serveur Terminal Server, utilisez l’outil en ligne de commande **tsshutdn.exe**.

## <a name="logging-off-the-current-session"></a>Déconnexion de la session en cours

Pour vous déconnecter d’une session sur le système local, vous pouvez utiliser différentes techniques. La solution la plus simple consiste à utiliser l’outil en ligne de commande Bureau à distance/Services Terminal Server, **logoff.exe** (pour plus d’informations, à l’invite Windows PowerShell, tapez **logoff /?** ). Pour fermer la session active, tapez **logoff** sans argument.

Vous pouvez également recouvrir à l’outil **shutdown.exe** avec son option logoff :

```
shutdown.exe -l
```

Une autre option consiste à utiliser WMI. La classe Win32_OperatingSystem dispose d’une méthode Win32Shutdown. L’appel de la méthode avec l’indicateur 0 déclenche la fermeture de session :

```powershell
(Get-WmiObject -Class Win32_OperatingSystem -ComputerName .).Win32Shutdown(0)
```

Pour plus d’informations et pour découvrir d’autres fonctionnalités de la méthode Win32Shutdown, voir « Méthode Win32Shutdown de la classe Win32_OperatingSystem » dans MSDN.

Enfin, vous pouvez utiliser CIM avec la même classe Win32_OperatingSystem comme décrit ci-dessus dans la méthode WMI.

```powershell
Get-CIMInstance -Classname Win32_OperatingSystem | Invoke-CimMethod -MethodName Shutdown
```

## <a name="shutting-down-or-restarting-a-computer"></a>Arrêt ou redémarrage d’un ordinateur

L’arrêt et le redémarrage d’ordinateurs sont généralement des tâches de même type. Les outils permettant d’arrêter un ordinateur permettent généralement aussi de le redémarrer, et inversement. Deux options simples permettent de redémarrer un ordinateur à partir de Windows PowerShell. Utilisez Tsshutdn.exe ou Shutdown.exe avec des arguments appropriés. Vous pouvez obtenir des informations d’utilisation détaillées à partir de **tsshutdn.exe /?** ou de **shutdown.exe /?** .

Vous pouvez également exécuter des opérations d’arrêt et de redémarrage directement depuis Windows PowerShell.

Pour arrêter l’ordinateur, utilisez la commande Stop-Computer

```powershell
Stop-Computer
```

Pour redémarrer le système d’exploitation, utilisez la commande Restart-Computer

```powershell
Restart-Computer
```

Pour forcer un redémarrage immédiat de l’ordinateur, utilisez le paramètre -Force.

```powershell
Restart-Computer -Force
```
