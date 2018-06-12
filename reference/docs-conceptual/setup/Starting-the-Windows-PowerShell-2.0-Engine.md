---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Démarrage du moteur Windows PowerShell 2.0
ms.assetid: edafc2fa-7576-49c2-bbba-9336f4bcfc28
ms.openlocfilehash: 618745ff4865dd046acf46487e87c3ca0e324f95
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2018
ms.locfileid: "34482962"
---
# <a name="starting-the-windows-powershell-20-engine"></a>Démarrage du moteur Windows PowerShell 2.0

Cette section explique comment démarrer le moteur Windows PowerShell 2.0 sur Windows 8.1, Windows Server 2012 R2, Windows 8 et Windows Server 2012, qui incluent le moteur Windows PowerShell 2.0, et sur d’autres systèmes sur lesquels Windows PowerShell 2.0, Windows PowerShell 3.0 et Windows PowerShell 4.0 sont installés.

Windows PowerShell 4.0 et Windows PowerShell 3.0 sont conçus pour offrir une compatibilité descendante avec Windows PowerShell 2.0. Les applets de commande, fournisseurs, composants logiciels enfichables, modules et scripts écrits pour Windows PowerShell 2.0 s’exécutent sans modification dans Windows PowerShell 3.0 et Windows PowerShell 4.0. Toutefois, en raison d’une modification de la stratégie d’activation du runtime de Microsoft .NET Framework 4, les programmes hôtes de Windows PowerShell écrits pour Windows PowerShell 2.0 et compilés avec Common Language Runtime (CLR) 2.0 ne peuvent pas s’exécuter sans modification dans Windows PowerShell 3.0 ou Windows PowerShell 4.0, qui sont compilés avec CLR 4.0. Le moteur Windows PowerShell 2.0 est destiné à être utilisé uniquement quand un script ou un programme hôte existant ne peut pas s’exécuter parce qu’il n’est pas compatible avec Windows PowerShell 4.0, Windows PowerShell 3.0 ou Microsoft .NET Framework 4. Ces cas sont supposé être rares.

De nombreux programmes qui nécessitent le moteur Windows PowerShell 2.0 le démarrent automatiquement. Ces instructions sont fournies pour les rares cas où vous devez démarrer le moteur manuellement.

## <a name="installing-and-enabling-required-programs"></a>Installation et activation des programmes requis

Avant de démarrer le moteur Windows PowerShell 2.0, activez le moteur Windows PowerShell 2.0 et Microsoft .NET Framework 3.5 avec Service Pack 1. Pour obtenir des instructions, voir [Installation de Windows PowerShell](Installing-Windows-PowerShell.md).

Les systèmes sur lesquels [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881) ou Windows Management Framework 3.0 sont installés disposent de tous les composants requis. Aucune autre configuration n’est nécessaire. Pour plus d’informations sur l’installation de [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881) ou de Windows Management Framework 3.0, consultez [Installation de Windows PowerShell](Installing-Windows-PowerShell.md).

## <a name="how-to-start-the-windows-powershell-20-engine"></a>Comment démarrer le moteur Windows PowerShell 2.0

Quand vous démarrez Windows PowerShell, la version la plus récente démarre par défaut. Pour démarrer Windows PowerShell avec le moteur Windows PowerShell 2.0, utilisez le paramètre Version de PowerShell.exe. Vous pouvez exécuter la commande à tout invite de commandes, y compris de Windows PowerShell et de Cmd.exe.

```
PowerShell.exe -Version 2
```

## <a name="how-to-start-a-remote-session-with-the-windows-powershell-20-engine"></a>Comment démarrer une session à distance avec le moteur Windows PowerShell 2.0

Pour exécuter le moteur Windows PowerShell 2.0 dans une session à distance, créez une configuration de session (également appelée « point de terminaison ») sur l’ordinateur distant qui charge le moteur Windows PowerShell 2.0. La configuration de session est enregistrée sur l’ordinateur distant et peut être utilisée par toute personne autorisée à créer des sessions faisant appel au moteur Windows PowerShell 2.0.

Il s’agit d’une tâche avancée généralement effectuée par un administrateur système.

La procédure suivante utilise le paramètre **PSVersion** de l’applet de commande [Register-PSSessionConfiguration](https://technet.microsoft.com/library/e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) pour créer une configuration de session qui utilise le moteur Windows PowerShell 2.0. Vous pouvez également utiliser le paramètre **PowerShellVersion** de l’applet de comment [New-PSSessionConfigurationFile](https://technet.microsoft.com/library/5f3e3633-6e90-479c-aea9-ba45a1954866) pour créer un fichier de configuration de session pour une session qui charge le moteur Windows PowerShell 2.0, et pouvez utiliser le paramètre **PSVersion** de l’applet de commande [Set-PSSessionConfiguration](https://technet.microsoft.com/library/b21fbad3-1759-4260-b206-dcb8431cd6ea) pour modifier une configuration de session afin d’utiliser le moteur Windows PowerShell 2.0.

Pour plus d’informations sur les fichiers de configuration de session, consultez [about_Session_Configuration_Files](https://technet.microsoft.com/library/c7217447-1ebf-477b-a8ef-4dbe9a1473b8). Pour plus d’informations sur les configurations de session, notamment l’installation et la sécurité, consultez [about_Session_Configurations[v4]](https://technet.microsoft.com/library/a2fbe12a-350c-4d04-be50-24102824e3ab).

#### <a name="to-start-a-remote-windows-powershell-20-session"></a>Pour démarrer une session Windows PowerShell 2.0 à distance

1. Pour créer une configuration de session qui requiert le moteur Windows PowerShell 2.0, utilisez le paramètre **PSVersion** de l’applet de commande [Register-PSSessionConfiguration](https://technet.microsoft.com/library/e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) avec la valeur « 2.0 ». Exécutez cette commande sur l’ordinateur « côté serveur » ou en fin de réception de la connexion.

   L’exemple de commande suivant crée la configuration de session PS2 sur l’ordinateur Server01. Pour exécuter cette commande, démarrez Windows PowerShell 4.0 ou Windows PowerShell 3.0 avec l’option **Exécuter en tant qu’administrateur**.

   ```powershell
   Register-PSSessionConfiguration -Name PS2 -PSVersion 2.0
   ```

2. Pour créer une session sur l’ordinateur Server01 qui utilise la configuration de session PS2, utilisez le paramètre **ConfigurationName** d’applets de commande qui créent une session à distance, telle l’applet de commande [New-PSSession](https://technet.microsoft.com/library/76f6628c-054c-4eda-ba7a-a6f28daaa26f).

   Quand une session utilisant la configuration de session démarre, le moteur Windows PowerShell 2.0 est automatiquement chargé dans la session.

   La commande suivante démarre une session sur l’ordinateur Server01 qui utilise la configuration de session PS2. La commande enregistre la session dans la variable $s.

   ```powershell
   $s = New-PSSession -ComputerName Server01 -ConfigurationName PS2
   ```

## <a name="how-to-start-a-background-job-with-the-windows-powershell-20-engine"></a>Comment démarrer un travail en arrière-plan avec le moteur Windows PowerShell 2.0

Pour démarrer un travail en arrière-plan avec le moteur Windows PowerShell 2.0, utilisez le paramètre **PSVersion** de l’applet de commande [Start-Job](https://technet.microsoft.com/library/2bc04935-0deb-4ec0-b856-d7290cca6442).

La commande suivante démarre un travail en arrière-plan avec le moteur Windows PowerShell 2.0.

```powershell
Start-Job {Get-Process} -PSVersion 2.0
```

Pour plus d’informations sur les tâches en arrière-plan, consultez [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs).